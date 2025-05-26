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

Method Chaining method:
#include<iostream>
using namespace std;

class A{
public:
    int x;
    int y;
    
    A& setX(int val)
    {  
        x = val;
        return *this;
    }
    
    A& setY(int val)
    {  
        y = val;
        return *this;
    }
    
    void display()
    {
        cout << "x: " << x << " " << "y: " << y << endl;
    }
};

int main ()
{
    A object;
    object.setX(4).setX(5);
    object.display();
    
}

#include <iostream>
#include <vector>
#include <string>
#include <fstream>
#include <sstream>
#include <algorithm>
using namespace std;

class Book {
    int id;
    string title, author;
    bool available;
public:
    Book(int i=0, string t="", string a="", bool avail=true)
        : id(i), title(t), author(a), available(avail) {}

    int getID() const { return id; }
    bool isAvailable() const { return available; }
    void borrow() { available = false; }
    void ret() { available = true; }
    void display() const {
        cout << id << ": " << title << " by " << author
             << (available ? " [Available]\n" : " [Borrowed]\n");
    }
    string serialize() const {
        return to_string(id)+","+title+","+author+","+to_string(available ? 1 : 0);
    }
    static Book deserialize(const string& line) {
        stringstream ss(line);
        string idS, t, a, avS;
        getline(ss,idS,','); getline(ss,t,','); getline(ss,a,','); getline(ss,avS);
        return Book(stoi(idS), t, a, avS=="1");
    }
};

class Person {
protected:
    string username, password;
public:
    Person(string u = "", string p = "") : username(u), password(p) {}
    virtual ~Person() {}
    string getName() const { return username; }
    bool checkPwd(string p) const { return p == password; }
    virtual string serialize() const = 0;
};

class User : public Person {
    vector<int> borrowed;
public:
    User(string u = "", string p = "") : Person(u, p) {}
    void borrowBook(int id) { borrowed.push_back(id); }
    void returnBook(int id) {
        borrowed.erase(remove(borrowed.begin(), borrowed.end(), id), borrowed.end());
    }
    void display() const {
        cout << username << " borrowed: ";
        for (int i : borrowed) cout << i << " ";
        cout << "\n";
    }
    string serialize() const override {
        string s = username + "," + password + ",";
        for (int i = 0; i < borrowed.size(); i++) {
            s += to_string(borrowed[i]);
            if (i < borrowed.size() - 1) s += ";";
        }
        return s;
    }
    static User deserialize(const string& line) {
        stringstream ss(line);
        string u, p, bor;
        getline(ss, u, ','); getline(ss, p, ','); getline(ss, bor);
        User usr(u, p);
        stringstream bs(bor);
        string id;
        while (getline(bs, id, ';'))
            if (!id.empty()) usr.borrowBook(stoi(id));
        return usr;
    }
};

class Admin : public Person {
public:
    Admin(string u = "", string p = "") : Person(u, p) {}
    string serialize() const override {
        return username + "," + password;
    }
    static Admin deserialize(const string& line) {
        stringstream ss(line);
        string u, p;
        getline(ss, u, ','); getline(ss, p);
        return Admin(u, p);
    }
};

class Library {
    vector<Book> books;
    vector<User> users;
    vector<Admin> admins;

    void save(const string& filename, const vector<string>& lines) {
        ofstream f(filename);
        for(auto& l : lines) f << l << "\n";
    }

    vector<string> load(const string& filename) {
        vector<string> lines;
        ifstream f(filename);
        string line;
        while(getline(f,line)) if(!line.empty()) lines.push_back(line);
        return lines;
    }

    template<typename T>
    void saveAll(const vector<T>& vec, const string& filename) {
        vector<string> lines;
        for (auto& e : vec) lines.push_back(e.serialize());
        save(filename, lines);
    }

    template<typename T>
    vector<T> loadAll(const string& filename, T(*deserialize)(const string&)) {
        vector<T> vec;
        for(auto& l : load(filename)) vec.push_back(deserialize(l));
        return vec;
    }

public:
    Library() {
        books = loadAll<Book>("books.txt", Book::deserialize);
        users = loadAll<User>("users.txt", User::deserialize);
        admins = loadAll<Admin>("admins.txt", Admin::deserialize);

        if(admins.empty()) {
            admins.push_back(Admin("admin","admin"));
            saveAll(admins, "admins.txt");
        }
    }

    void saveAllData() {
        saveAll(books, "books.txt");
        saveAll(users, "users.txt");
        saveAll(admins, "admins.txt");
    }

    void addBook(Book b) {
        for(auto& bk : books)
            if(bk.getID() == b.getID()) {
                cout << "Book ID exists!\n"; return;
            }
        books.push_back(b); saveAllData();
    }

    void removeBook(int id) {
        books.erase(remove_if(books.begin(), books.end(),
            [id](Book& b){return b.getID()==id;}), books.end());
        saveAllData();
    }

    void listBooks() {
        for(auto& b : books) b.display();
    }

    void listAvailable() {
        bool found = false;
        for(auto& b : books)
            if(b.isAvailable()) { b.display(); found = true; }
        if(!found) cout << "No books available.\n";
    }

    Book* findBook(int id) {
        for(auto& b : books)
            if(b.getID()==id) return &b;
        return nullptr;
    }

    void addUser(User u) {
        for(auto& us : users)
            if(us.getName() == u.getName()) {
                cout << "User exists!\n"; return;
            }
        users.push_back(u); saveAllData();
    }

    void removeUser(string name) {
        users.erase(remove_if(users.begin(), users.end(),
            [&](User& u){return u.getName()==name;}), users.end());
        saveAllData();
    }

    void addAdmin(Admin a) {
        for(auto& ad : admins)
            if(ad.getName() == a.getName()) {
                cout << "Admin exists!\n";
                return;
            }
        admins.push_back(a);
        saveAllData();
    }

    vector<User>& getUsers() { return users; }

    Person* login(string uname, string pwd, string role) {
        if(role == "admin") {
            for (auto& a : admins)
                if (a.getName() == uname && a.checkPwd(pwd))
                    return new Admin(a);
        } else {
            for (auto& u : users)
                if (u.getName() == uname && u.checkPwd(pwd))
                    return new User(u);
        }
        return nullptr;
    }

    bool borrowBook(User& u, int id) {
        Book* b = findBook(id);
        if(b && b->isAvailable()) {
            b->borrow();
            u.borrowBook(id);
            saveAllData();
            return true;
        }
        return false;
    }

    bool returnBook(User& u, int id) {
        Book* b = findBook(id);
        if(b) {
            b->ret();
            u.returnBook(id);
            saveAllData();
            return true;
        }
        return false;
    }
};

void adminMenu(Library& lib, Admin* admin) {
    int c;
    do {
        cout << "\n==============================\n";
        cout << "  Admin Panel - " << admin->getName() << "\n";
        cout << "==============================\n";
        cout << "1) Add Book\n";
        cout << "2) Remove Book\n";
        cout << "3) List All Books\n";
        cout << "4) List All Users\n";
        cout << "5) Add User\n";
        cout << "6) Remove User\n";
        cout << "7) Add Admin\n";
        cout << "0) Logout\n";
        cout << "------------------------------\n";
        cout << "Enter your choice: ";
        cin >> c; cin.ignore();

        if (c == 1) {
            int id; string t, a;
            cout << "Book ID: "; cin >> id; cin.ignore();
            cout << "Title: "; getline(cin, t);
            cout << "Author: "; getline(cin, a);
            lib.addBook(Book(id, t, a));
        } else if (c == 2) {
            int id;
            cout << "Book ID to remove: "; cin >> id; cin.ignore();
            lib.removeBook(id);
        } else if (c == 3) {
            lib.listBooks();
        } else if (c == 4) {
            for (auto& u : lib.getUsers()) u.display();
        } else if (c == 5) {
            string u, p;
            cout << "Username: "; getline(cin, u);
            cout << "Password: "; getline(cin, p);
            lib.addUser(User(u, p));
        } else if (c == 6) {
            string u;
            cout << "Username to remove: "; getline(cin, u);
            lib.removeUser(u);
        } else if (c == 7) {
            string u, p;
            cout << "Admin Username: "; getline(cin, u);
            cout << "Admin Password: "; getline(cin, p);
            lib.addAdmin(Admin(u, p));
        }
    } while (c != 0);
}

void userMenu(Library& lib, User* user) {
    int c;
    do {
        cout << "\n==============================\n";
        cout << "  User Panel - " << user->getName() << "\n";
        cout << "==============================\n";
        cout << "1) View Available Books\n";
        cout << "2) Borrow Book\n";
        cout << "3) Return Book\n";
        cout << "4) My Borrowed Books\n";
        cout << "0) Logout\n";
        cout << "------------------------------\n";
        cout << "Enter your choice: ";
        cin >> c; cin.ignore();

        if (c == 1) {
            lib.listAvailable();
        } else if (c == 2) {
            int id;
            cout << "Enter Book ID to borrow: ";
            cin >> id; cin.ignore();
            if (lib.borrowBook(*user, id))
                cout << "Book borrowed successfully.\n";
            else
                cout << "Book is not available or doesn't exist.\n";
        } else if (c == 3) {
            int id;
            cout << "Enter Book ID to return: ";
            cin >> id; cin.ignore();
            if (lib.returnBook(*user, id))
                cout << "Book returned successfully.\n";
            else
                cout << "Invalid return. Book not found or wasn't borrowed.\n";
        } else if (c == 4) {
            user->display();
        } else if (c != 0) {
            cout << "Invalid choice. Please try again.\n";
        }

    } while (c != 0);
}

int main() {
    Library lib;
    cout << "\nLIBRARY MANAGEMENT SYSTEM\n";
    while(true) {
        string role;
        cout << "\nLogin as (admin/user), or 'exit': ";
        cin >> role; cin.ignore();
        if(role == "exit") break;
        if(role != "admin" && role != "user") { cout << "Invalid role.\n"; continue; }
        string uname, pwd;
        cout << "Username: "; getline(cin, uname);
        cout << "Password: "; getline(cin, pwd);
        Person* person = lib.login(uname, pwd, role);
        if(!person) { cout << "Login failed.\n"; continue; }
        if(Admin* a = dynamic_cast<Admin*>(person)) adminMenu(lib, a);
        else if(User* u = dynamic_cast<User*>(person)) userMenu(lib, u);
        delete person;
    }
    cout << "Bye!\n";
    return 0;
}


---
Shakir61/Shakir61 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
