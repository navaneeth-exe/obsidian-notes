🧾 ALGORITHM – FCFS

Step 1:

Start


---

Step 2:

Read initial head position using command line argument.


---

Step 3:

Generate random disk requests between:

0 to 4999


---

Step 4:

Initialize:

current = head

total = 0



---

Step 5:

Service requests in the order they are generated.


---

Step 6:

For each request:

Calculate head movement

Add movement to total

Update current head position



---

Step 7:

Repeat until all requests are serviced.


---

Step 8:

Display:

Disk requests

Seek sequence

Total head movement



---

Step 9:

Stop


---

💻 PROGRAM

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

#define CYLINDERS 5000
#define REQUESTS 10

int main(int argc, char *argv[]) {

    if(argc != 2) {

        printf("Usage: %s <initial_head_position>\n", argv[0]);
        return 1;
    }

    int head = atoi(argv[1]);

    int req[REQUESTS];

    srand(time(0));

    // Generate random requests
    printf("Disk Requests:\n");

    for(int i = 0; i < REQUESTS; i++) {

        req[i] = rand() % CYLINDERS;

        printf("%d ", req[i]);
    }

    printf("\n");

    int total = 0;
    int current = head;

    printf("\nSeek Sequence:\n");

    // Service requests in arrival order
    for(int i = 0; i < REQUESTS; i++) {

        printf("%d ", req[i]);

        total += abs(current - req[i]);

        current = req[i];
    }

    printf("\n\nTotal Head Movement = %d\n", total);

    return 0;
}