#include <stdio.h>
#include <stdlib.h>

struct student {
    int id;
    char name[50];
    float marks;
};

void inputStudentData(struct student* s, int n) {
    for (int i = 0; i < n; i++) {
        printf("\nEnter details for student %d:\n", i + 1);

        printf("ID: ");
        scanf("%d", &s[i].id);

        printf("Name: ");
        scanf(" %[^\n]", s[i].name);   // Accepts full name

        printf("Marks: ");
        scanf("%f", &s[i].marks);
    }
}

void displayStudentData(struct student* s, int n) {
    printf("\nStudent Details:\n");
    for (int i = 0; i < n; i++) {
        printf("Student %d: ID=%d, Name=%s, Marks=%.2f\n",
               i + 1, s[i].id, s[i].name, s[i].marks);
    }
}

int main() {
    int n;

    printf("Enter number of students: ");
    scanf("%d", &n);

    if (n <= 0) {
        printf("Invalid number of students!\n");
        return 1;
    }

    struct student* s = (struct student*)malloc(n * sizeof(struct student));

    if (s == NULL) {
        printf("Memory allocation failed\n");
        return 1;
    }

    inputStudentData(s, n);
    displayStudentData(s, n);

    free(s);
    return 0;
}
