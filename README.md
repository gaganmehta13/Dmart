
Save New Duplicate & Edit Just Text Twitter
// SPPU DSL PROGRAMS




// 01.
// Write a Python program to store marks scored in the subject “Fundamentals of Data Structure” by N students in the class. Write functions to compute the following:
// a) The average score of the class
// b) The highest score and the lowest score of the class
// c) The count of students who were absent for the test
// d) Display the mark with the highest frequency

// Code




def Average(marks, n):
    total = 0
    for i in range(n):
        total += marks[i]
    average = total / n
    return average

def Maximum(marks, n):
    max_marks = marks[0]
    for i in range(1, n):
        if marks[i] > max_marks:
            max_marks = marks[i]
    return max_marks

def Minimum(marks, n):
    min_marks = 999
    for i in range(n):
        if marks[i] < min_marks and marks[i] >= 0:
            min_marks = marks[i]
    return min_marks

def Absent(marks, n):
    cnt = 0
    for i in range(n):
        if marks[i] == -1:
            cnt += 1
    return cnt

def Cntmax(marks, n, s):
    cntmax = 0
    for i in range(n):
        if marks[i] == s:
            cntmax += 1
    return cntmax

marks = []
n = int(input("Enter number of students, if absent please enter -1: "))
for i in range(n):
    m = int(input("Enter your marks: "))
    marks.append(m)

while True:
    print("Please press '1' for average")
    print("'2' for maximum marks")
    print("'3' for minimum marks")
    print("'4' for absent students")
    print("'5' for number of students with maximum marks")
    print("'6' for none")

    opt = int(input("Enter your choice: "))

    if opt == 1:
        avg = Average(marks, n)
        print("Average is:", avg)
    elif opt == 2:
        max_marks = Maximum(marks, n)
        print("Maximum marks:", max_marks)
    elif opt == 3:
        min_marks = Minimum(marks, n)
        print("Minimum marks:", min_marks)
    elif opt == 4:
        cnt = Absent(marks, n)
        print("No. of absent students:", cnt)
    elif opt == 5:
        max_marks = Maximum(marks, n)
        cntmax = Cntmax(marks, n, max_marks)
        print("The number of students having maximum marks:", cntmax)
    elif opt == 6:
        print("This option indicates you have chosen none!")
        break
    else:
        print("Invalid option, please try again.")


---

// 02.
// Write a Python program that computes the net amount of a bank account based on a transaction log from console input. The transaction log format is shown as follows: D 100 W 200 (Withdrawal is not allowed if the balance goes negative. Write functions for withdraw and deposit) D means deposit while W means withdrawal.
// Suppose the following input is supplied to the program:
// D 300, D 300, W 200, D 100
// Then, the output should be: 500

// Code



def deposit(balance, amount):
    return balance + amount

def withdraw(balance, amount):
    if balance >= amount:
        return balance - amount
    else:
        print("Insufficient balance:", balance)
        return balance

account_balance = 10000

while True:
    transaction = input("Enter transaction (e.g., 'D 100' or 'W 200') or 'exit' to quit: ")
    
    if transaction.lower() == 'exit':
        break
    
    try:
        operation, amount_str = transaction.split()
        amount = int(amount_str)
        
        if operation.upper() == "D":
            account_balance = deposit(account_balance, amount)
            print("Current Account balance is:", account_balance)
        elif operation.upper() == "W":
            account_balance = withdraw(account_balance, amount)
            print("Current Account balance is:", account_balance)
        else:
            print("Invalid operation:", operation)
    except ValueError:
        print("Invalid input format. Please enter in the format 'D 100' or 'W 200'.")





---

// 03.
// Write a Python program to perform the following computations on matrices:
// a) Addition of two matrices
// b) Subtraction of two matrices
// c) Multiplication of two matrices
// d) Transpose of a matrix

// Code




def Addition(r, c, m, m1):
    print("Addition of two matrices:")
    result = []
    for i in range(r):
        row = []
        for j in range(c):
            row.append(m[i][j] + m1[i][j])
        result.append(row)

    print("Using nested loops:")
    for row in result:
        print(row)

def Subtraction(r, c, m, m1):
    print("Subtraction of two matrices:")
    result = []
    for i in range(r):
        row = []
        for j in range(c):
            row.append(m[i][j] - m1[i][j])
        result.append(row)

    print("Using nested loops:")
    for row in result:
        print(row)

def Transpose(r, c, m):
    print("Transpose of the first matrix:")
    result = []
    for j in range(c):
        row = []
        for i in range(r):
            row.append(m[i][j])
        result.append(row)

    print("Using nested loops:")
    for row in result:
        print(row)

def Transpose1(r, c, m1):
    print("Transpose of the second matrix:")
    result = []
    for j in range(c):
        row = []
        for i in range(r):
            row.append(m1[i][j])
        result.append(row)

    print("Using nested loops:")
    for row in result:
        print(row)

def Multiplication(r, c, m, m1):
    print("Multiplication of matrices:")

    if r == c:
        result = []
        for i in range(r):
            row = []
            for j in range(c):
                sum = 0
                for k in range(c):
                    sum += m[i][k] * m1[k][j]
                row.append(sum)
            result.append(row)

        print("Using nested loops:")
        for row in result:
            print(row)
    else:
        print("Operation invalid: Matrices must be square i.e (n x n) for multiplication.")
m = []
r = int(input("Enter the number of rows: "))
c = int(input("Enter the number of columns: "))
for i in range(r):
    a = []
    for j in range(c):
        ele = int(input("Enter element: "))
        a.append(ele)
    m.append(a)

print("1st matrix is:")
for row in m:
    print(row)
m1 = []
for i in range(r):
    a = []
    for j in range(c):
        ele = int(input("Enter element: "))
        a.append(ele)
    m1.append(a)

print("2nd matrix is:")
for row in m1:
    print(row)
while True:
    print("Please press 1 for matrix addition;")
    print("Please press 2 for matrix subtraction;")
    print("Please press 3 for transpose of matrix 1;")
    print("Please press 4 for transpose of matrix 2;")
    print("Please press 5 for multiplication of matrices;")
    print("Please press 6 for none;")

    opt = int(input("Enter your choice: "))

    if opt == 1:
        Addition(r, c, m, m1)
    elif opt == 2:
        Subtraction(r, c, m, m1)
    elif opt == 3:
        Transpose(r, c, m)
    elif opt == 4:
        Transpose1(r, c, m1)
    elif opt == 5:
        Multiplication(r, c, m, m1)
    elif opt == 6:
        print("You opted for none!")
        break
    else:
        print("Invalid option, please try again.")
---

// 04.
// Write a Python program to store the first-year percentage of students in an array. Write functions for sorting an array of floating-point numbers in ascending order using:
// a) Selection Sort
// b) Bubble Sort
// and display the top five scores.

// Code




def selection_sort(arr):
    n = len(arr)
    for i in range(n):
        min_index = i
        for j in range(i + 1, n):
            if arr[j] < arr[min_index]:
                min_index = j
        arr[i], arr[min_index] = arr[min_index], arr[i]

def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        swapped = False
        for j in range(0, n - i - 1):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
                swapped = True
        if not swapped:
            break

def display_top_scores(arr, top_n=5):
    print(f"Top {top_n} scores:")
    for score in arr[-top_n:]:
        print(score)

percentages = []
num_students = int(input("Enter the number of students: "))

for i in range(num_students):
    score = float(input(f"Enter the percentage for student {i + 1}: "))
    percentages.append(score)

selection_sort(percentages)
print("\nSorted percentages using Selection Sort:")
print(percentages)
display_top_scores(percentages)

bubble_sort(percentages)
print("\nSorted percentages using Bubble Sort:")
print(percentages)
display_top_scores(percentages)




---

// 05.
// Write a Python program to store the second-year percentage of students in an array. Write functions for sorting an array of floating-point numbers in ascending order using:
// a) Insertion Sort
// b) Shell Sort
// and display the top five scores.

// Code




def insertion_sort(arr):
    for i in range(1, len(arr)):
        key = arr[i]
        j = i - 1
        while j >= 0 and key < arr[j]:
            arr[j + 1] = arr[j]
            j -= 1
        arr[j + 1] = key

def shell_sort(arr):
    n = len(arr)
    gap = n // 2
    while gap > 0:
        for i in range(gap, n):
            temp = arr[i]
            j = i
            while j >= gap and arr[j - gap] > temp:
                arr[j] = arr[j - gap]
                j -= gap
            arr[j] = temp
        gap //= 2

def display_top_scores(arr, top_n=5):
    print(f"Top {top_n} scores (from max to min):")
    for score in sorted(arr[-top_n:], reverse=True):
        print(score)

percentages = []
while True:
    try:
        num_students = int(input("Enter the number of students: "))
        if num_students <= 0:
            raise ValueError("Number of students must be a positive integer.")
        break
    except ValueError as e:
        print(f"Invalid input: {e}. Please try again.")

for i in range(num_students):
    while True:
        try:
            score = float(input(f"Enter the percentage for student {i + 1}: "))
            percentages.append(score)
            break
        except ValueError:
            print("Invalid input. Please enter a valid number.")

insertion_sort(percentages)
print("\nSorted percentages using Insertion Sort:")
print(percentages)
display_top_scores(percentages)

shell_sort(percentages)
print("\nSorted percentages using Shell Sort:")
print(percentages)
display_top_scores(percentages)



---

// 06.
// Write a Python program to store the first-year percentage of students in an array. Write a function for sorting an array of floating-point numbers in ascending order using Quick Sort and display the top five scores.

// Code

def quicksort(arr):
    if len(arr) <= 1:
        return arr
    else:
        pivot = arr[len(arr) // 2]
        left = [x for x in arr if x < pivot]
        middle = [x for x in arr if x == pivot]
        right = [x for x in arr if x > pivot]
        return quicksort(left) + middle + quicksort(right)

def display_top_scores(arr, top_n=5):
    print(f"Top {top_n} scores:")
    for score in arr[-top_n:]:
        print(score)

percentages = []
while True:
    try:
        num_students = int(input("Enter the number of students: "))
        if num_students <= 0:
            raise ValueError("Number of students must be a positive integer.")
        break
    except ValueError as e:
        print(f"Invalid input: {e}. Please try again.")

for i in range(num_students):
    while True:
        try:
            score = float(input(f"Enter the percentage for student {i + 1}: "))
            percentages.append(score)
            break
        except ValueError:
            print("Invalid input. Please enter a valid number.")

sorted_percentages = quicksort(percentages)
print("\nSorted percentages:")
print(sorted_percentages)
display_top_scores(sorted_percentages)



---

// 07.
// The Department of Computer Engineering has a student's club named 'Pinnacle Club'. Students of the second, third, and final year of the department can be granted membership on request. Similarly, one may cancel the membership of the club. The first node is reserved for the president of the club and the last node is reserved for the secretary of the club. Write a C++ program to maintain club member's information using a singly linked list. Store student PRN and Name. Write functions to:
// a) Add and delete members as well as the president or even the secretary.
// b) Compute the total number of members in the club
// c) Display members
// d) Two linked lists exist for two divisions. Concatenate the two lists

// Code



#include <iostream>
#include <string>
using namespace std;
struct Member {
    string prn;
    string name;
    Member* next;
};
class PinnacleClub {
private:
    Member* head;
    Member* tail;

public:
    PinnacleClub() {
        head = nullptr;
        tail = nullptr;
    }

    void addMember(const string& prn, const string& name) {
        Member* newMember = new Member{prn, name, nullptr};
        if (!head) {
            head = newMember;
            tail = newMember;
        } else {
            tail->next = newMember;
            tail = newMember;
        }
    }
    void deleteMember(const string& prn) {
        if (!head) {
            cout << "No members to delete." << endl;
            return;
        }
        Member* current = head;
        Member* previous = nullptr;
        while (current != nullptr && current->prn != prn) {
            previous = current;
            current = current->next;
        }
        if (!current) {
            cout << "Member with PRN " << prn << " not found." << endl;
            return;
        }
        if (current == head) {
            head = head->next;
        } else {
            previous->next = current->next;
        }
        if (current == tail) {
            tail = previous;
        }

        delete current;
        cout << "Member with PRN " << prn << " deleted." << endl;
    }
    int totalMembers() {
        int count = 0;
        Member* current = head;
        while (current != nullptr) {
            count++;
            current = current->next;
        }
        return count;
    }
    void displayMembers() {
        if (!head) {
            cout << "No members in the club." << endl;
            return;
        }

        Member* current = head;
        while (current != nullptr) {
            cout << "PRN: " << current->prn << ", Name: " << current->name << endl;
            current = current->next;
        }
    }
    void concatenate(PinnacleClub& otherClub) {
        if (!head) {
            head = otherClub.head;
            tail = otherClub.tail;
        } else if (otherClub.head) {
            tail->next = otherClub.head;
            tail = otherClub.tail;
        }
        otherClub.head = nullptr;
        otherClub.tail = nullptr;
    }
    ~PinnacleClub() {
        while (head) {
            Member* temp = head;
            head = head->next;
            delete temp;
        }
    }
};
void addMemberInput(PinnacleClub& club) {
    string prn, name;
    cout << "Enter PRN: ";
    cin >> prn;
    cout << "Enter Name: ";
    cin.ignore();
    getline(cin, name);
    club.addMember(prn, name);
}

int main() {
    PinnacleClub divisionA;
    PinnacleClub divisionB;
    int choice;

    do {
        cout << "\nPinnacle Club Menu:\n";
        cout << "1. Add Member to Division A\n";
        cout << "2. Add Member to Division B\n";
        cout << "3. Delete Member from Division A\n";
        cout << "4. Delete Member from Division B\n";
        cout << "5. Display Members of Division A\n";
        cout << "6. Display Members of Division B\n";
        cout << "7. Compute Total Members in Division A\n";
        cout << "8. Compute Total Members in Division B\n";
        cout << "9. Concatenate Division B into Division A\n";
        cout << "0. Exit\n";
        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice) {
            case 1:
                addMemberInput(divisionA);
                break;
            case 2:
                addMemberInput(divisionB);
                break;
            case 3: {
                string prn;
                cout << "Enter PRN of the member to delete from Division A: ";
                cin >> prn;
                divisionA.deleteMember(prn);
                break;
            }
            case 4: {
                string prn;
                cout << "Enter PRN of the member to delete from Division B: ";
                cin >> prn;
                divisionB.deleteMember(prn);
                break;
            }
            case 5:
                cout << "\nMembers of Division A:\n";
                divisionA.displayMembers();
                break;
            case 6:
                cout << "\nMembers of Division B:\n";
                divisionB.displayMembers();
                break;
            case 7:
                cout << "Total members in Division A: " << divisionA.totalMembers() << endl;
                break;
            case 8:
                cout << "Total members in Division B: " << divisionB.totalMembers() << endl;
                break;
            case 9:
                cout << "Concatenating Division B into Division A..." << endl;
                divisionA.concatenate(divisionB);
                cout << "Concatenation complete." << endl;
                break;
            case 0:
                cout << "Exiting..." << endl;
                break;
            default:
                cout << "Invalid choice. Please try again." << endl;
        }
    } while (choice != 0);

    return 0;
}




---

// 08.
// Write a C++ program for storing a binary number using doubly linked lists. Write functions:
// a) To compute 1's and 2's complement
// b) To add two binary numbers

// Code

#include <iostream>
#include <string>
using namespace std;

struct Node {
    char bit;
    Node* next;
    Node* prev;
};

class BinaryNumber {
private:
    Node* head;
    Node* tail;

public:
    BinaryNumber() : head(nullptr), tail(nullptr) {}

    void addBit(char bit) {
        Node* newNode = new Node{bit, nullptr, tail};
        if (!head) {
            head = newNode;
            tail = newNode;
        } else {
            tail->next = newNode;
            tail = newNode;
        }
    }

    void display() {
        Node* current = head;
        while (current) {
            cout << current->bit;
            current = current->next;
        }
        cout << endl;
    }

    void onesComplement() {
        Node* current = head;
        while (current) {
            current->bit = (current->bit == '0') ? '1' : '0';
            current = current->next;
        }
    }

    void twosComplement() {
        onesComplement();
        Node* current = tail;
        bool carry = true;

        while (current && carry) {
            if (current->bit == '1') {
                current->bit = '0';
            } else {
                current->bit = '1';
                carry = false;
            }
            current = current->prev;
        }

        if (carry) {
            addBit('1');
        }
    }

    static BinaryNumber add(BinaryNumber& num1, BinaryNumber& num2) {
        BinaryNumber result;
        Node* ptr1 = num1.tail;
        Node* ptr2 = num2.tail;
        bool carry = false;

        while (ptr1 || ptr2 || carry) {
            int sum = carry;
            if (ptr1) {
                sum += (ptr1->bit - '0');
                ptr1 = ptr1->prev;
            }
            if (ptr2) {
                sum += (ptr2->bit - '0');
                ptr2 = ptr2->prev;
            }

            carry = sum > 1;
            result.addBit((sum % 2) + '0');
        }

        reverse(result);
        return result;
    }

    static void reverse(BinaryNumber& binary) {
        Node* current = binary.head;
        Node* temp = nullptr;

        while (current) {
            temp = current->prev;
            current->prev = current->next;
            current->next = temp;
            current = temp;
        }

        if (temp) {
            binary.tail = binary.head;
            binary.head = temp->pre
