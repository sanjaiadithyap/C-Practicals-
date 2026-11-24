#include <iostream>
#include <vector>
#include <string>
#include <algorithm>
using namespace std;

class Student
{
public:
    string name;
    int marks;
    char grade;
};

int main()
{
    vector<Student> students = {
        {"Arun", 85, ' '},
        {"Bala", 72, ' '},
        {"Kumar", 91, ' '},
        {"Ravi", 65, ' '}
    };

    // Lambda to assign grades
    auto assignGrade = [](Student &s)
    {
        if (s.marks >= 90)
            s.grade = 'A';
        else if (s.marks >= 80)
            s.grade = 'B';
        else if (s.marks >= 70)
            s.grade = 'C';
        else
            s.grade = 'F';
    };

    for_each(students.begin(), students.end(), assignGrade);

    // Sort by marks (highest first)
    sort(students.begin(), students.end(),
         [](const Student &a, const Student &b)
         {
             return a.marks > b.marks;
         });

    cout << "Name\tMarks\tGrade" << endl;
    cout << "---------------------\n";

    for (const auto &s : students)
    {
        cout << s.name << "\t"
             << s.marks << "\t"
             << s.grade << endl;
    }

    return 0;
}