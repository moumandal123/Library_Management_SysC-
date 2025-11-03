# Library_Management_SysC-
#include <iostream>
#include <string>
#include <vector>
#include <limits> 

using namespace std;

struct Library {
    int id;
    int std_id;
    string book_name;
    string author_name;
    string std_name;
    int price;
};

int main() {
    vector<Library> lib;
    lib.reserve(20);

    while (true) {
        cout << "\n===== Library Management System =====\n";
        cout << "1. Input Book & Student Details\n";
        cout << "2. Display All Records\n";
        cout << "3. Quit\n";
        cout << "Enter your choice: ";

        int choice;
        if (!(cin >> choice)) {                
            cout << "Invalid input. Please enter a number (1-3).\n";
            cin.clear();
            cin.ignore(numeric_limits<streamsize>::max(), '\n');
            continue;
        }

        cin.ignore(numeric_limits<streamsize>::max(), '\n');

        if (choice == 1) {
            if (lib.size() >= 20) {
                cout << "Library record is full (20 records max).\n";
                continue;
            }

            Library rec;
            cout << "Enter Book Id: ";
            while (!(cin >> rec.id)) {
                cout << "Invalid Book Id. Enter an integer: ";
                cin.clear();
                cin.ignore(numeric_limits<streamsize>::max(), '\n');
            }
            cin.ignore(numeric_limits<streamsize>::max(), '\n'); 

            cout << "Enter Book Name: ";
            getline(cin, rec.book_name);

            cout << "Enter Author Name: ";
            getline(cin, rec.author_name);

            cout << "Enter Student Name: ";
            getline(cin, rec.std_name);

            cout << "Enter Student Id: ";
            while (!(cin >> rec.std_id)) {
                cout << "Invalid Student Id. Enter an integer: ";
                cin.clear();
                cin.ignore(numeric_limits<streamsize>::max(), '\n');
            }

            cout << "Enter Book Price: ";
            while (!(cin >> rec.price)) {
                cout << "Invalid price. Enter an integer: ";
                cin.clear();
                cin.ignore(numeric_limits<streamsize>::max(), '\n');
            }

            lib.push_back(rec);
            cout << "Record added successfully.\n";

            // Ask user whether to return to menu or exit immediately:
            cout << "Do you want to menu or quit? [m/q]: ";
            char ans;
            cin >> ans;
            cin.ignore(numeric_limits<streamsize>::max(), '\n');
            if (ans == 'q' || ans == 'Q') {
                cout << "Exiting program. Goodbye!\n";
                break;
            }
   

        } else if (choice == 2) {
            if (lib.empty()) {
                cout << "No records to display.\n";
            } else {
                cout << "\n===== Library Records =====\n";
                for (size_t i = 0; i < lib.size(); ++i) {
                    cout << "\nRecord " << i + 1 << ":\n";
                    cout << "Book Id: " << lib[i].id << '\n';
                    cout << "Book Name: " << lib[i].book_name << '\n';
                    cout << "Author Name: " << lib[i].author_name << '\n';
                    cout << "Student Name: " << lib[i].std_name << '\n';
                    cout << "Student Id: " << lib[i].std_id << '\n';
                    cout << "Book Price: " << lib[i].price << '\n';
                }
            }
        } else if (choice == 3) {
            cout << "Quitting program.\n";
            break;
        } else {
            cout << "Invalid choice! Please enter 1, 2, or 3.\n";
        }
    }

    return 0;
}
