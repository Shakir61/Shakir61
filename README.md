Inheritance task # 1:

#include <iostream>
using namespace std;

class Super{
private:
    int storage;
public:
    void put (int value){ storage = value; }
    int get ( void ){ return storage; }
};

class Sub: public Super{
 public:
     void print (void){ cout << "Storage variable: " << storage << endl; }
};

int main()
{
    Sub object;
    
    object.put(100);
    object.put(object.get() + 1);
    
    cout << object.get() << endl;
    
    // object.storage = 0;   it will not work as it reamins hidden.
    object.print();
    
 return 0;    
}

Inheritance task # 2:

#include<iostream>
using namespace std;

class A{
   int x;
   int y;
public:
   int z;
   void printA (){ cout << x << " " << y << " " << endl; }
   void setA (int a, int b, int c){ x = a; y = b; z = c; }
};

class B: public A{
   int var1;
public:
   int var2;
   void setB (int a, int b){ var1 = a; var2 = b; }
   void printB (){ cout << var1 << " " << var2 << endl; }
   
};

int main ()
{
    A objA;
    B objB;
}

Inheriatnce task no # 3: 

#include<iostream>
using namespace std;

class Person{
    int age;
    string name;
public:
    Person (int age, string name)
    {
        this->age = age; 
        this->name = name; 
    }
    
    void displayPerson ()
    {
        cout << "Name: " << name << endl;
        cout << "Age: " << age << endl;
    }
};

class Student: public Person{
    char grade;
    
public:
    Student (int age, string name, char grade): Person(age, name) { this->grade = grade; }
    
    void displayStudent()
    {
        displayPerson();
        cout << "Grade: " << grade << endl; 
    }
};

int main (){

    Student S1(20, "ShakirUllah", 'A');
    
    S1.displayStudent();
    
    return 0;
}

Inheritance task # 3:

#include <iostream>
using namespace std;

class Book{
    string title;
    string author;
    
public:
    Book(string title, string author)
    {
        this->title = title;
        this->author = author;
    }
    
    void displayInfo()
    {
        cout << "Book title: " << title << endl;
        cout << "Book author: " << author << endl;
    }
};

class PrintedBook: public Book{
    int pages;
    
public:
    PrintedBook(int pages, string title, string author): Book (title, author)
    {
        this->pages = pages;
    }
    
    void displayInfo()
    {
        Book::displayInfo();
        cout << "Book pages: " << pages << endl;
    }
    
};

int main() {
    
    PrintedBook PB1(500, "Fundamentals of C++", "Shakir Ullah");
    PB1.displayInfo();
    
    return 0;
}

Inheritance Task # 4:

#include <iostream>
using namespace std;

class Person{
    string name;
    int age;
public:
    Person(string Name, int Age): name(Name), age(Age){ }
    
    virtual void displayInfo()
    {
        cout << "Person Name: " << name << endl;
        cout << "Person Age: " << age << endl;
    }
};

class Employee: public Person{
    int employeeID;
    string position;
    
public: 
    Employee(string Name, int Age, int employee_ID, string Position): Person(Name, Age), employee_ID(employeeID), Position(position){ }
    
    
};

class Manager: public Employee{
    
};
int main() {
    
    PrintedBook PB1(500, "Fundamentals of C++", "Shakir Ullah");
    PB1.displayInfo();
    
    return 0;
}

Operator Overloading Function:
#include <iostream>
using namespace std;

class Time
{
    int second;
    int minute;
    int hour;
    
public:
    Time (int S = 0, int M = 0, int H = 0)
    {
        second = S;
        minute = M;
        hour = H;
    }
    
    Time operator+(Time var)
    {
        Time result;
        result.second = second + var.second;
        result.minute = minute + var.minute;
        result.hour = hour + var.hour;
        
        return result;
    }
    
    Time operator-(Time var)
    {
        Time result;
        result.second = second - var.second;
        result.minute = minute - var.minute;
        result.hour = hour - var.hour;
        
        return result;
    }
    
    void displayAdd ()
    {
        cout << "Addition: " << second << ", " << minute << ", " << hour << endl;
    }
    
    void displaySub ()
    {
        cout << "Subtraction: " << second << ", " << minute << ", " << hour << endl;
    }
};

int main() {
    
    Time T1 (55, 32, 11);
    Time T2 (50, 42, 12);
    
    Time T3;
    
    T3 = T1 + T2;
    T3.displayAdd();
    
    Time T4(30, 23, 4);
    Time T5(40, 45, 8);
    Time T6;
    
    T6 = T5 - T4;
    T6.displaySub ();
    return 0;
}

---
Shakir61/Shakir61 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
