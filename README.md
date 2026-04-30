# OOPS-in-CPP 
This repository contains my daily learning of OOPS in C++.

## What is OOPS?
It is an approach or programming pattern where the program are structured around the object rather than function or logic.
How to access data members from a class??
class student
{
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

### Constructor
-> Constructor is a special function that is invoked automatically at the time the object is created.
-> Constructor does not have any return type
-> Constructor should be of same name as of class name
-> Constructor is used to initialize the value

eg:

class Customer
{
    public:
    string name;
    int account_number;
    int balance;
    
    Customer()
    {
        cout<<"Contructor is called";
    }
};

int main()
{
    Customer C;
    
}
## Types of constructor
# 1.Default Constructor:
Constructor that takes no argument and is used to initialize the object with the default value.
#include <iostream>
using namespace std;

class Customer 
{
public:
    string name = "Abhi";
    int account_number = 2020202020;
    int balance = 1111111;

    // Default Constructor
    Customer() 
    {
        cout << "Name is: " << name 
             << " Account Number is: " << account_number 
             << " Balance is: " << balance;
    }
};

int main() {
    Customer C;   // default constructor called
}

# 2.Parameterized Constructor
  A constructor that takes arguments to initialize object values.
  #include <iostream>
using namespace std;

class Customer 
{
public:
    string name;
    long long account_number;
    int balance;

    Customer(string name, long long account_number, int balance) \
    {
        this->name = name;
        this->account_number = account_number;
        this->balance = balance;
    }

    void display() 
    {
        cout << "Name: " << name << endl;
        cout << "Account Number: " << account_number << endl;
        cout << "Balance: " << balance << endl;
    }
};

int main() {
    Customer C("Katrina", 2222222222, 1000000000);
    C.display();
}

# what does this keyword do??
This keyword store and point to the address of the object for which it was created.

## Copy Constructor
A constructor which is used to initialize the object of one class using another object of same class.
Copy Constructor is created by default.If we are creating copy constructor the we must pass the refrence so that it could easily refer to constructor in which we have to copy.
#include <iostream>
using namespace std;

class Customer 
{
public:
    string name;
    int account_number;
    int balance;

    // Parameterized Constructor
    Customer(string name, int account_number, int balance)
    {
        this->name = name;
        this->account_number = account_number;
        this->balance = balance;
    }

    // Copy Constructor
    Customer(Customer &B) 
    {
        name = B.name;
        account_number = B.account_number;
        balance = B.balance;
    }

    void display() 
    {
        cout << "Name: " << name << endl;
        cout << "Account Number: " << account_number << endl;
        cout << "Balance: " << balance << endl;
    }
};

int main()
{
    Customer C("Katrina", 222222222, 1000000000);

    Customer C2(C);   

    C2.display();
}

# Contructor overloading
Multiple constructor within the same class but with different parameter.

#include <iostream>
using namespace std;

class Student {
public:
    string name;
    int age;

   
    Student() {
        name = "Unknown";
        age = 0;
    }

  
    Student(string n) {
        name = n;
        age = 0;
    }

  
    Student(string n, int a) {
        name = n;
        age = a;
    }

    void display() {
        cout << "Name: " << name << ", Age: " << age << endl;
    }
};

int main() {
    Student s1;                
    Student s2("Abhishek");     
    Student s3("Rahul", 21);    

    s1.display();
    s2.display();
    s3.display();
}

### Destructor
Destructor is an instance member that is invoked automatically when the object is to be destroyed
#include <iostream>
using namespace std;

class Student {
public:
    Student() {
        cout << "Constructor called";
    }

    ~Student() {
        cout << "Destructor called\n";
    }
};

int main() {
    Student s1;
}

Destructor free up the heap memory or dynamically allocated memory.

### Calling order of Constructor And Destructor

Constructor → called in same order as object creation
Destructor → called in reverse order

#include <iostream>
using namespace std;

class A {
public:
    A() {
        cout << "Constructor A\n";
    }
    ~A() {
        cout << "Destructor A\n";
    }
};

class B {
public:
    B() {
        cout << "Constructor B\n";
    }
    ~B() {
        cout << "Destructor B\n";
    }
};

int main() {
    A obj1;
    B obj2;
}

output: Constructor A
Constructor B
Destructor B
Destructor A

### Static data member
-> They are attribute of class or class member
-> They are declared using static keyword
->only one copy of that variable or member is created to the entire class and shared by all object

# Syntax:
Data_type class_name :: variable_name 


#include <iostream>
using namespace std;

class Customer
{
    public:
    static int total_customer;
    string name;
    int roll_no;
    Customer(string name,int roll_no)
    {
        this->name=name;
        this->roll_no=roll_no;
        total_customer++;
    }
    void display()
    {
        cout<<"Name is:"<<name<<" Roll_No:"<<roll_no<<endl;
        cout<<total_customer<<endl;
        
    }
};
int Customer::total_customer=0;

int main()
{
    Customer c1("Shreya",49);
    Customer c2("Abhi",2);
    c1.display();
    c2.display();
    Customer c3("Manish",4);
    c3.display();
    c2.display();
}

## Static function
A function that belongs to the object not to the class.
-> Does not need an object to call

eg:class_name :: function_name;

#include <iostream>
using namespace std;

class Student {
public:
    static void show() {
        cout << "This is a static function";
    }
};

int main() {
    Student::show();  
}

### Encapsulation
Encapsulation is the process of binding data and functions together and restricting direct access to data using access specifiers.
Restricting direct access to data.
It is also called data hiding


### Abstraction
The process of showing only the essential information to the user and hiding the internal Implementation
In C++ using:
Classes
Access specifiers (private, public)
Abstract classes (advanced)

### Inheritance
The process of inheriting the property and characteristic of a parent class(base class) to a child class(sub class).

| Modifier  | Outside Class | Same Class | Derived Class |
|-----------|--------------|------------|---------------|
| Public    | Yes          | Yes        | Yes           |
| Protected | No           | Yes        | Yes           |
| Private   | No           | Yes        | No            |

## Strictness in modifier
Private>Protected>Public

| Base Class Member | Inheritance Type | Access in Derived Class |
|-------------------|-----------------|-------------------------|
| Public            | Public          | Public                  |
| Public            | Private         | Private                 |
| Public            | Protected       | Protected               |
| Protected         | Public          | Protected               |
| Protected         | Protected       | Protected               |
| Protected         | Private         | Private                 |
| Private           | Any             | Not Accessible          |

# Example how can we inherit the property 
#include <iostream>
using namespace std;
class Human
{
    public:
    string name;
    int age;
    int wt;
};
class Student: public Human
{
   
    int roll_number;
    int fees;
};
int main()
{
    Student A;
    A.roll_number=6;
    
}


# Example 2:
That means:

protected members of Human become private inside Student
They are still accessible inside Student class, which is why your code works

#include <iostream>
using namespace std;

class Human {
protected:
    string religion, color;   // protected
    string name;              // protected
    int age, weight;          // protected
};

class Student : private Human {
private:
    int roll_number, fees;

public:
    Student(string name, int age, int weight, int roll_number) {
        this->name = name;
        this->age = age;
        this->weight = weight;
        this->roll_number = roll_number;
    }

    void display() {
        cout << "Name: " << name << endl;
        cout << "Age: " << age << endl;
        cout << "Weight: " << weight << endl;
        cout << "Roll Number: " << roll_number << endl;
    }
};

int main() {
    Student A("Rohit", 18, 60, 23);
    A.display();
    return 0;
}

## Types of Inheritance
# Single Inheritance
Single inheritance means one derived (child) class inherits from one base (parent) class.
#include <iostream>
using namespace std;


class Animal {
public:
    void eat() {
        cout << "Animal is eating" << endl;
    }
};


class Dog : public Animal {
public:
    void bark() {
        cout << "Dog is barking" << endl;
    }
};

int main() {
    Dog d;
    d.eat();   // inherited function
    d.bark();  // own function
    return 0;
}
Output :Base class constructor called
Derived class constructor called
# Call order of constructor
Base class constructor runs first, then derived class constructor
eg
#include <iostream>
using namespace std;

class A {
public:
    A() { cout << "A constructor\n"; }
};

class B {
public:
    B() { cout << "B constructor\n"; }
};

class C : public A, public B {
public:
    C() { cout << "C constructor\n"; }
};

int main() {
    C obj;
}

Output: A constructor
        B constructor
        C constructor

#include <iostream>
using namespace std;

class A {
public:
    A(int x) { cout << "A: " << x << endl; }
};

class B {
public:
    B(int y) { cout << "B: " << y << endl; }
};

class C : public A, public B {
public:
    C() : B(20), A(10) {   // order written here is different!
        cout << "C constructor" << endl;
    }
};

int main() {
    C obj;
}

Output:
A: 10
B: 20
C constructor

#include <iostream>
using namespace std;

class A {
public:
    A(int x) { cout << "A: " << x << endl; }
};

class B {
public:
    B(int y) { cout << "B: " << y << endl; }
};

class C : public A, public B {
public:
    C() : B(20), A(10) {   // order written here is different! no matter it will continue i the order it is inheriting the property
        cout << "C constructor" << endl;
    }
};

int main() {
    C obj;
}

output:
B: 20
A: 10
C constructor

## MultiLevel Inheritance
Multilevel inheritance means a class is derived from another derived class, forming a chain.

#include <iostream>
using namespace std;

// Base class
class Animal {
public:
    void eat() {
        cout << "Animal is eating" << endl;
    }
};

// Derived class 1 (inherits Animal)
class Dog : public Animal {
public:
    void bark() {
        cout << "Dog is barking" << endl;
    }
};

// Derived class 2 (inherits Dog)
class Puppy : public Dog {
public:
    void weep() {
        cout << "Puppy is weeping" << endl;
    }
};

int main() {
    Puppy p;

    p.eat();   // from Animal
    p.bark();  // from Dog
    p.weep();  // own function

    return 0;
}

# Multiple Inheritance
Multiple inheritance means a class inherits from more than one base (parent) class.
#include <iostream>
using namespace std;

// Base class 1
class Father {
public:
    void showFather() {
        cout << "This is Father class" << endl;
    }
};

// Base class 2
class Mother {
public:
    void showMother() {
        cout << "This is Mother class" << endl;
    }
};

// Derived class
class Child : public Father, public Mother {
public:
    void showChild() {
        cout << "This is Child class" << endl;
    }
};

int main() {
    Child c;

    c.showFather(); // from Father
    c.showMother(); // from Mother
    c.showChild();  // own function

    return 0;
}

# Hierarchical inheritance
Hierarchical inheritance means multiple derived (child) classes inherit from the same base (parent) class.
#include <iostream>
using namespace std;

// Base class
class Animal {
public:
    void eat() {
        cout << "Animal is eating" << endl;
    }
};

// Derived class 1
class Dog : public Animal {
public:
    void bark() {
        cout << "Dog is barking" << endl;
    }
};

// Derived class 2
class Cat : public Animal {
public:
    void meow() {
        cout << "Cat is meowing" << endl;
    }
};

int main() {
    Dog d;
    Cat c;

    d.eat();   // from Animal
    d.bark();  // Dog's own

    c.eat();   // from Animal
    c.meow();  // Cat's own

    return 0;
}

        








