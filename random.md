#  Measure Execution Time in Array Search

##  Description
This C program searches for multiple values (each value from the array itself) and measures the execution time of each search operation using the `clock()` function from `time.h`.

It prints:
- Whether the number was found or not
- Its index (if found)
- The closest number (if not found)
- The execution time for each search

---

##  How It Works

- The array `random[100]` is initialized with 100 integers.
- For each number in the array, the function `measuretime()` is called.
- Inside `measuretime()`:
  - The time is recorded before and after the search.
  - If the number is found → its index and execution time are printed.
  - If not found → the closest number is found and printed, along with the execution time.
- The main function loops through all 100 numbers and measures each search.

---

##  Code

```c
#include <stdio.h>
#include <time.h>


    int random[100] = {
        43, 17, 93, 2, 67, 11, 58, 90, 7, 36,
        83, 14, 39, 99, 23, 77, 1, 64, 55, 10,
        47, 31, 85, 29, 6, 96, 40, 71, 26, 80,
        5, 52, 19, 38, 33, 13, 92, 24, 62, 8,
        70, 45, 20, 98, 88, 59, 3, 95, 61, 16,
        34, 78, 9, 27, 66, 73, 81, 18, 87, 56,
        22, 37, 0, 68, 15, 60, 12, 42, 84, 32,
        30, 79, 94, 28, 76, 63, 21, 35, 65, 86,
        91, 46, 41, 50, 4, 97, 25, 53, 44, 54,
        48, 1, 82, 75, 74, 89, 57, 49, 69, 51
    };
void measuretime(int number){
    clock_t start = clock();

    for (int i = 0; i < 100; i++) {
        if (random[i] == number) {
            clock_t end = clock();
            double time_taken = (double)(end - start) / CLOCKS_PER_SEC;
            printf("Number %d found at index %d\n", number, i);
            printf("Execution time: %d seconds\n", time_taken);
            return 0;
        }
    }

    for (int i = 1; i < 100; i++) {
        int d1 = random[i] - number;
        if (d1 < 0) d1 = -d1;

        int d2 = random[0] - number;
        if (d2 < 0) d2 = -d2;

        if (d1 < d2) {
            random[0] = random[i];
        }
    }

    clock_t end = clock();
    double time_taken = (double)(end - start) ;

    printf("Number %d not found. Closest number is %d\n", number, random[0]);
    printf("Execution time: %d seconds\n", time_taken);
}
int main() {



    int number;
    printf("Enter Number: ");
    scanf("%d", &number);

    for (int i = 0; i < 100; i++) {
            measuretime(random[i]);
            }
    return 0;
}


