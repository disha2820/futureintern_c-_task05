# futureintern_c-_task05
#include <iostream>
#include <string>
#include <vector>
#include <cstdlib>
#include <ctime>

using namespace std;

// Function to generate a random password
string generatePassword(int length, bool useUppercase, bool useLowercase, bool useNumbers, bool useSpecialChars) {
    string uppercase = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    string lowercase = "abcdefghijklmnopqrstuvwxyz";
    string numbers = "0123456789";
    string specialChars = "!@#$%^&*()-_=+[]{}|;:,.<>?/";

    string characterPool = "";
    if (useUppercase) characterPool += uppercase;
    if (useLowercase) characterPool += lowercase;
    if (useNumbers) characterPool += numbers;
    if (useSpecialChars) characterPool += specialChars;

    // Ensure at least one type of character is selected
    if (characterPool.empty()) {
        cout << "Error: At least one character type must be selected!" << endl;
        return "";
    }

    string password = "";
    for (int i = 0; i < length; i++) {
        int randomIndex = rand() % characterPool.size();
        password += characterPool[randomIndex];
    }

    return password;
}

int main() {
    srand(time(0)); // Seed for random number generation

    int length;
    char choice;
    bool useUppercase = false, useLowercase = false, useNumbers = false, useSpecialChars = false;

    cout << "Welcome to the Random Password Generator!" << endl;

    // Get the desired password length from the user
    cout << "Enter the desired password length: ";
    cin >> length;

    // Get user preferences for character types
    cout << "Include uppercase letters? (y/n): ";
    cin >> choice;
    useUppercase = (choice == 'y' || choice == 'Y');

    cout << "Include lowercase letters? (y/n): ";
    cin >> choice;
    useLowercase = (choice == 'y' || choice == 'Y');

    cout << "Include numbers? (y/n): ";
    cin >> choice;
    useNumbers = (choice == 'y' || choice == 'Y');

    cout << "Include special characters? (y/n): ";
    cin >> choice;
    useSpecialChars = (choice == 'y' || choice == 'Y');

    // Generate the password
    string password = generatePassword(length, useUppercase, useLowercase, useNumbers, useSpecialChars);
    if (!password.empty()) {
        cout << "\nGenerated Password: " << password << endl;
    }

    return 0;
}
