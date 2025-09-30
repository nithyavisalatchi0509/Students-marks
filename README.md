
#include <stdio.h>

struct Student {
    char name[20];
    int marks;
};

int main() {
    struct Student s;
    printf("Enter name and marks: ");
    scanf("%s %d", s.name, &s.marks);
    printf("Name: %s, Marks: %d\n", s.name, s.marks);
    return 0;
}
