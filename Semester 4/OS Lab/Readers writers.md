ALGORITHM – Readers Writers Problem

Step 1:

Start


---

Step 2:

Initialize:

Semaphore mutex

Semaphore rw_mutex

read_count = 0



---

Step 3:

Create reader and writer threads using:

pthread_create()


---

Step 4:

Reader Process:

Wait on mutex

Increment read_count

If first reader:

Lock rw_mutex


Release mutex



---

Step 5:

Reader enters critical section and reads shared data.


---

Step 6:

Reader exits:

Wait on mutex

Decrement read_count

If last reader:

Release rw_mutex


Release mutex



---

Step 7:

Writer Process:

Wait on rw_mutex

Enter critical section

Write data

Release rw_mutex



---

Step 8:

Repeat reading and writing operations.


---

Step 9:

Wait for all threads using:

pthread_join()


---

Step 10:

Destroy semaphores and stop.


---

PROGRAM

#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>
#include <semaphore.h>
#include <unistd.h>

sem_t mutex, rw_mutex;

int read_count = 0,
    int data = 0;

void *reader(void *arg) {

    int id = *(int *)arg;

    while (1) {

        // Entry section
        sem_wait(&mutex);

        read_count++;

        if (read_count == 1)
            sem_wait(&rw_mutex);

        sem_post(&mutex);

        // Critical section
        printf("Reader %d reads data = %d\n", id, data);

        sleep(1);

        // Exit section
        sem_wait(&mutex);

        read_count--;

        if (read_count == 0)
            sem_post(&rw_mutex);

        sem_post(&mutex);

        sleep(1);
    }
}

void *writer(void *arg) {

    int id = *(int *)arg;

    while (1) {

        sem_wait(&rw_mutex);

        // Critical section
        data++;

        printf("Writer %d writes data = %d\n", id, data);

        sleep(2);

        sem_post(&rw_mutex);

        sleep(1);
    }
}

int main() {

    pthread_t r[3], w[2];

    int rid[3] = {1, 2, 3};
    int wid[2] = {1, 2};

    // Initialize semaphores
    sem_init(&mutex, 0, 1);
    sem_init(&rw_mutex, 0, 1);

    // Create reader threads
    for (int i = 0; i < 3; i++)
        pthread_create(&r[i], NULL,
                       reader, &rid[i]);

    // Create writer threads
    for (int i = 0; i < 2; i++)
        pthread_create(&w[i], NULL,
                       writer, &wid[i]);

    // Wait for threads
    for (int i = 0; i < 3; i++)
        pthread_join(r[i], NULL);

    for (int i = 0; i < 2; i++)
        pthread_join(w[i], NULL);

    // Destroy semaphores
    sem_destroy(&mutex);
    sem_destroy(&rw_mutex);

    return 0;
}

SAMPLE OUTPUT

Reader 1 reads data = 0
Reader 2 reads data = 0
Reader 3 reads data = 0

Writer 1 writes data = 1

Reader 1 reads data = 1
Reader 2 reads data = 1
Reader 3 reads data = 1

Writer 2 writes data = 2