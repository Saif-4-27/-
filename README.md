#include <iostream>
using namespace std;

struct Student {
    int id;
    string name;
    float grade;
};

Student students[100];
int countStudents = 0;

// Add student function
void addStudents() {
    if (countStudents >= 100) {
        cout << "Storage is full!\n";
        return;
    }
    cout << "Enter Student ID: ";
    cin >> students[countStudents].id;
    cin.ignore(); // مهم لحل مشكلة الاسم
    cout << "Enter Student Name: ";
    getline(cin, students[countStudents].name);
    cout << "Enter Student Grade: ";
    cin >> students[countStudents].grade;
    countStudents++;
    cout << "Student added successfully!\n";
}

// Display students
void displayStudents(){
    if (countStudents == 0){
        cout << "No students found.\n";
        return;
    }
    for (int i = 0; i < countStudents; i++) {
        cout << "\nStudent " << i + 1 << endl;
        cout << "ID: " << students[i].id << endl;
        cout << "Name: " << students[i].name << endl;
        cout << "Grade: " << students[i].grade << endl;
    }
}

// Search student
void searchStudent(){
    int id;
    cout << "Enter ID to search: ";
    cin >> id;
    for (int i = 0; i < countStudents; i++) {
        if (students[i].id == id) {
            cout << "Student Found:\n";
            cout << "Name: " << students[i].name << endl;
            cout << "Grade: " << students[i].grade << endl;
            return;
        }
    }
    cout << "Student not found.\n";
}

// Main function
int main () {
    int choice;
    do {
        cout << "\n===== Student Management System =====\n";
        cout << "1. Add Student\n";
        cout << "2. Display Students\n";
        cout << "3. Search Student\n";
        cout << "4. Exit\n";
        cout << "Enter your choice: ";
        cin >> choice;
        switch (choice) {
            case 1:
                addStudents();
                break;
            case 2:
                displayStudents();
                break;
            case 3:
                searchStudent();
                break;
            case 4:
                cout << "Goodbye!\n";
                break;
            default:
                cout << "Invalid choice!\n";
        }
    } while (choice != 4);
    return 0;
}
