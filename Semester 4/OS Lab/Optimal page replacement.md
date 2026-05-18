📚 THEORY

Optimal Page Replacement is a page replacement algorithm used in operating systems.

It replaces:

> The page that will not be used for the longest period of time in the future.




---

🔹 Key Idea

Future page references are checked

Page used farthest in future is replaced

Produces minimum number of page faults



---

🔹 Important Terms

Page → unit of memory

Frame → memory slot

Page Fault → occurs when page is not present in memory



---

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



---

Step 5:

For each page in reference string:

Check if page already exists in frames

If found:

Continue to next page


Else:

Check future page references

Find page that will not be used for longest time

Replace that page

Increment page faults




---

Step 6:

Display total page faults


---

Step 7:

Stop

---

`#include <stdio.h>
#include <stdlib.h>
#include <time.h>

#define MAX_PAGES 100

// Optimal Page Replacement
int optimal(int pages[], int n, int frames) {

    int fr[10];
    int pageFaults = 0;

    // Initialize frames
    for (int i = 0; i < frames; i++)
        fr[i] = -1;

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

            int pos = 0, farthest = -1;

            for (int j = 0; j < frames; j++) {

                int k;

                for (k = i + 1; k < n; k++) {

                    if (fr[j] == pages[k]) {

                        if (k > farthest) {

                            farthest = k;
                            pos = j;
                        }

                        break;
                    }
                }

                // Page not used again
                if (k == n) {

                    pos = j;
                    break;
                }
            }

            // Replace page
            fr[pos] = pages[i];

            pageFaults++;
        }
    }

    return pageFaults;
}

int main(int argc, char *argv[]) {

    if (argc != 3) {

        printf("Usage: %s <reference_string_length> <num_frames>\n", argv[0]);
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

    int faults = optimal(pages, n, frames);

    printf("\nTotal page faults (Optimal): %d\n", faults);

    return 0;
}`