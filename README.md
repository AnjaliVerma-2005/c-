# c-
#include <iostream>
#include <iomanip>
#include <vector>
#include <limits> // For numeric_limits

using namespace std;

// Structure to hold course information
struct Course {
    string name;
    int creditHours;
    float grade; // Grade on a scale of 5.0
    float gradePoints;
};

int main() {
    int numCourses;
    float totalGradePoints = 0.0;
    int totalCredits = 0;

    cout << "===== CGPA CALCULATOR =====\n";
    cout << "Enter number of courses: ";
    cin >> numCourses;

    vector<Course> courses(numCourses);

    // Input data for each course
    for (int i = 0; i < numCourses; i++) {
        cout << "\nEnter details for Course " << i + 1 << ":\n";

        cout << "Course name: ";
        cin.ignore(numeric_limits<streamsize>::max(), '\n'); // Flush the input buffer
        getline(cin, courses[i].name);

        cout << "Credit hours: ";
        cin >> courses[i].creditHours;

        cout << "Grade earned (e.g., 4.5 out of 5.0): ";
        cin >> courses[i].grade;

        // Calculate grade points for this course
        courses[i].gradePoints = courses[i].grade * courses[i].creditHours;

        totalGradePoints += courses[i].gradePoints;
        totalCredits += courses[i].creditHours;
    }

    // Calculate CGPA
    float cgpa = totalGradePoints / totalCredits;

    // Output results
    cout << "\n===== RESULT SUMMARY =====\n";
    cout << fixed << setprecision(2);
    for (int i = 0; i < numCourses; i++) {
        cout << "Course: " << courses[i].name
             << ", Credit Hours: " << courses[i].creditHours
             << ", Grade: " << courses[i].grade
             << ", Grade Points: " << courses[i].gradePoints << "\n";
    }

    cout << "\nTotal Credit Hours: " << totalCredits;
    cout << "\nTotal Grade Points: " << totalGradePoints;
    cout << "\nYour CGPA is: " << cgpa << " / 5.00\n";

    return 0;
}
