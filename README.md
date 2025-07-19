# randomtask.c

#  Search in Random Array

##  Description
This C program initializes an array of 100 random integers and allows the user to input a number to search for. If the number exists in the array, the program prints its index. If not found, it returns the number closest in value to the input.

---

##  How It Works

- The program defines an integer array `random[100]` with predefined values.
- It asks the user to enter a number.
- It performs a linear search in the array:
  - If the number is found → prints its index and exits.
  - If not found → it calculates the absolute difference between the input number and each value in the array.
  - The closest value is selected and printed.

---

##  Code

```c
#include <stdio.h>

int main() {
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

    int number;
    printf("Enter Number: ");
    scanf("%d", &number);

    for (int i = 0; i < 100; i++) {
        if (random[i] == number) {
            printf("Number %d found at index %d\n", number, i);
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

    printf("Number %d not found. Closest number is %d\n", number, random[0]);

    return 0;
}
