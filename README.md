# Noah-s-Repository
Test Repository for C++ Class 12/3/2023
#include <iostream>
#include <string>

using namespace std;

// Node structure for the linked list
struct Node {
    string firstName;
    long long phoneNumber;
    Node* next;
    
    // Constructor to initialize the node
    Node(string fName, long long pNumber) : firstName(fName), phoneNumber(pNumber), next(nullptr) {}
};

// Function to perform binary search on the linked list
long long phoneNameSearch(Node* head, const string& name) {
    while (head != nullptr) {
        if (head->firstName == name) {
            return head->phoneNumber; // Name found, return corresponding phone number
        } else if (head->firstName < name) {
            head = head->next; // Search in the right half
        } else {
            break; // The list is sorted, no need to search in the right half
        }
    }
    
    return -1; // Name not found
}

int main() {
    // Creating a linked list of phone numbers and names
    Node* head = new Node("Alice", 1234567890);
    head->next = new Node("Bob", 2345678901);
    head->next->next = new Node("Charlie", 3456789012);
    // Add more nodes as needed

    // Example usage of phoneNameSearch function
    string searchName = "Bob";
    long long result = phoneNameSearch(head, searchName);

    if (result != -1) {
        cout << "Phone number for " << searchName << ": " << result << endl;
    } else {
        cout << "Name not found." << endl;
    }

    // Clean up memory (not necessary for this example, but good practice)
    while (head != nullptr) {
        Node* temp = head;
        head = head->next;
        delete temp;
    }

    return 0;
}
