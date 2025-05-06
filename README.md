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

---
Shakir61/Shakir61 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
