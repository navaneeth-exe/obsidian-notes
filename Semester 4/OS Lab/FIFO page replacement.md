🧾 ALGORITHM

Step 1:

Start


---

Step 2:

Read command-line arguments:

Length of reference string

Number of frames



---

Step 3:

Generate random page reference string (0–9)


---

Step 4:

Initialize:

Frame array with -1

pageFaults = 0

front = 0



---

Step 5:

For each page in reference string:

Check if page already exists in frames

If found:

Continue to next page


Else:

Replace oldest page using front

Move front circularly

Increment page faults




---

Step 6:

Display total page faults


---

Step 7:

Stop


---

💻 PROGRAM

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

#define MAX_PAGES 100

// FIFO Page Replacement
int fifo(int pages[], int n, int frames) {

    int fr[10];
    int pageFaults = 0, front = 0;

    // Initialize frames
    for (int i = 0; i < frames; i++) {
        fr[i] = -1;
    }

    for (int i = 0; i < n; i++) {

        int found = 0;

        // Check if page exists
        for (int j = 0; j < frames; j++) {

            if (fr[j] == pages[i]) {
                found = 1;
                break;
            }
        }

        // Page Fault
        if (!found) {

            // Replace oldest page
            fr[front] = pages[i];

            // Move front circularly
            front = (front + 1) % frames;

            pageFaults++;
        }
    }

    return pageFaults;
}

int main(int argc, char *argv[]) {

    if (argc != 3) {

        printf("Usage: %s <reference_string_length> <num_frames>\n",
               argv[0]);

        return 1;
    }

    int n = atoi(argv[1]);
    int frames = atoi(argv[2]);

    int pages[MAX_PAGES];

    if (n <= 0 || n > MAX_PAGES || frames < 1 || frames > 7) {

        printf("Invalid arguments.\n");
        return 1;
    }

    srand(time(NULL));

    printf("\nGenerated page reference string:\n");

    for (int i = 0; i < n; i++) {

        pages[i] = rand() % 10;

        printf("%d ", pages[i]);
    }

    printf("\n");

    int faults = fifo(pages, n, frames);

    printf("\nTotal page faults (FIFO): %d\n", faults);

    return 0;
}