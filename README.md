# OOPS-in-CPP
This repository contains my daily learning of OOPS in C++.
## Day 1
## What is OOPS?
It is an approach or programming pattern where the program are structured around the object rather than function or logic.
How to access data members from a class??
class student{
public:
string name,
int age,
int card
}
int main()
{
student s1;
s1.name="Abhishek";
s1.age=20;
s1.card=22;
}
## By default modifier in class is private

## what is class?
A class is blueprint of an object.
A class is also called as user defined data type

## How can we access through private modifiers??
#include <iostream>
using namespace std;

class Student {
private:
    string name;
    int age;
    int rollNumber;
    char grade;

public:
   
    void setName(string n) {
        name = n;
    }

    void setAge(int a) {
        if (a > 0) {
            age = a;
        }
    }

    void setRollNumber(int r) {
        rollNumber = r;
    }

    void setGrade(char g) {
        grade = g;
    }

    // Getter functions (to access values)
    string getName() {
        return name;
    }

    int getAge() {
        return age;
    }

    int getRollNumber() {
        return rollNumber;
    }

    char getGrade() {
        return grade;
    }
};

int main() {
    Student s1;

    
    s1.setName("Abhishek");
    s1.setAge(20);
    s1.setRollNumber(101);
    s1.setGrade('A');

  
    cout << "Name: " << s1.getName() << endl;
    cout << "Age: " << s1.getAge() << endl;
    cout << "Roll Number: " << s1.getRollNumber() << endl;
    cout << "Grade: " << s1.getGrade() << endl;

    return 0;
}
## what is object??
An entity that has state and behaviour
## example 
If bank is a class then Customer accounts,
Specific banks,
Individual bank entities are object


## Padding Concept??
Padding means extra unused memory added by the compiler to make data properly aligned in memory

class a{
char c;
int b;

}
int main()
{
a obj1;
cout<<sizeof(obj1);
}

sizeof obj1 is not 5 byte
## Why not 5 byte and what is the correct answer?? 
char → 1 byte → multiple of 1
short → 2 bytes → multiple of 2
int → 4 bytes → multiple of 4
double → 8 bytes → multiple of 8

c _ _ _ b b b b
0 1 2 3 4 5 6 7
After char (1 byte)
Compiler adds 3 bytes padding
Then int (4 bytes)
Final Size = 8 bytes

## Why Empty Class Have size of 1 Byte in C++?
class A {

};

int main() 
{
    cout << sizeof(A);
}

output:1 byte
## Reason:
Every object must occupy at least 1 byte so that it has unique identity in memory


