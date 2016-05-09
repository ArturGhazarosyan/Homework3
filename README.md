# Homework3
//
//  main.cpp
//  OOP hw
//
//  Created by Artur Ghazarosyan on 2/8/16.
//  Copyright © 2016 Artur Ghazarosyan. All rights reserved.
//


#include <iostream>
#include <string>
#include <sstream>
using namespace std;
class Date
{
    private :int day;
    int month;
    int year;
    public : Date();
    void initialize (int,int,int);
    string get_formatted_date();
};
class Student
{
    private : string Firstname;
    string Lastname;
    Date Birthdate;
    string faculty;
    string ID;
    public : Student (string, string, string);
    void set_birth_date (int, int, int);
    void set_name(string, string);
    Student (const Student &);
    string get_birth_date();
    string get_first_name();
    string get_last_name();
    string get_id();
    static int id;
};
int Student :: id=0;
Student::Student(string f_n, string l_n, string f)
{   Firstname=f_n;
    Lastname=l_n;
    faculty=f;
    id++;
    string x = "AUA_" + faculty;
    x += "_";
    string y;
    stringstream ss;
    ss << id;
    ss >> y;
    ID = x + y;
}
void Student::set_birth_date(int x, int y, int z)
{   Birthdate.initialize(x,y,z);  }
void Student::set_name(string f_n, string l_n)
{    Firstname= f_n;
    Lastname=l_n;
}
Student :: Student(const Student & obj)
{   faculty=obj.faculty;
    id++;
    string x = "AUA_" + faculty;
    x += "_";
    string y;
    stringstream ss;
    ss << id;
    ss >> y;
    ID = x + y;
}
string Student::get_first_name()
{    return Firstname;   }
string Student::get_last_name()
{    return Lastname;  }
string Student::get_id()
{    return ID;     }
string Student::get_birth_date()
{    return Birthdate.get_formatted_date();}
void Date::initialize(int x, int y, int z)
{   if (x>=1 && x<=31)
    day=x;
else
    cout <<"incorrect day";
    if (y>=1 && y<=12)
        month=y;
    else
        cout <<"incorrect month";
    if (z>=1900 && z<=2016)
        year=z;
    else
        cout<< "incorrect year";
}
Date::Date()
{   day=1;
    month=1;
    year=1900;
}
string Date::get_formatted_date()
{   string str;
    stringstream ss;
    ss<<year<<','<<month<<'-'<<day;
    ss>>str;
    return str;
}
int main ()

{
    Student s("Aram","Grigoryan", "CS");
    s.set_birth_date(12, 7, 1995);
    Student d(s);
    d.set_name("Anna", "Sargsyan");
    d.set_birth_date(1, 5, 1995);
    cout<<s.get_first_name()<<"   "<<s.get_id()<<endl;
    cout<<s.get_birth_date()<<endl;
    cout<<d.get_first_name()<<"   "<<d.get_id()<<endl;
    cout<<d.get_birth_date()<<endl;
    return 0;
}
