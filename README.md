#include <stdio.h>
#include <string.h>

#define SUBJECTS 3

typedef struct {
    char name[50];
    int marks[SUBJECTS];
    int total;
    float average;
} Student;

void calculate(Student *s) {
    s->total = 0;
    for (int i = 0; i < SUBJECTS; ++i)
        s->total += s->marks[i];
    s->average = s->total / (float) SUBJECTS;
}

int main(void) {
    Student s;

    printf("Enter student name: ");
    if (fgets(s.name, sizeof s.name, stdin) == NULL) return 0;
    s.name[strcspn(s.name, "\n")] = '\0';  /* remove newline */

    for (int i = 0; i < SUBJECTS; ++i) {
        printf("Enter marks for subject %d: ", i + 1);
        if (scanf("%d", &s.marks[i]) != 1) {
            printf("Invalid input.\n");
            return 1;
        }
    }

    calculate(&s);

    printf("\n--- Student Report ---\n");
    printf("Name   : %s\n", s.name);
    printf("Total  : %d\n", s.total);
    printf("Average: %.2f\n", s.average);

    return 0;
}
