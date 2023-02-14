
## What is Object Oriented Programming ?
- Object oriented programming is a programming paradigm based on the concept of "objects", which can contain data, in the form of fields, often known as attributes; and code, in the form of procedures, often known as methods.
- Object oriented programming is a style of programming where we use objects to model real world things that we want to represent inside our programs and/or provide a simple way to access functionality that would otherwise be hard or impossible to make use of.


## OOPs advantages
- OOPs makes it easy to maintain and modify existing code as new objects can be created with small differences to existing ones.
- OOPs provides a clear modular structure for programs which makes it good for defining abstract datatypes in which implementation details are hidden.
- Objects can also be reused within an across applications. The reuse of software also lowers the cost of development. More effort is put into the object-oriented analysis and design, which lowers the overall cost of development.
- It makes software easier to maintain. Since the design is modular, part of the system can be updated in case of issues without a need to make large-scale changes.
- it provides ability to simulate real world scenario. For example, if you have an object of a class named Car, it can have attributes like color, weight, engine, etc. and it can have behaviors like start, accelerate, brake, etc.
- It is easy to debug and test as objects participate in multiple events. The detection of errors is easier than procedural programming.



## Procedure Oriented Programming vs Object Oriented Programming
| Procedure Oriented Programming | Object Oriented Programming |
| --- | --- |
| instructions are written in a sequence | instructions are written in a form of objects |
| procedure oriented | object oriented |
| data and functions are separate | data and functions are together |
| data is global | data is private |
| no concept of class | concept of class |

## Example of Procedure Oriented Programming
- known as inline programming takes a top-down approach, writing a list of instructions to tell the computer what to do step by step it relies on procedure or routine
- ```cpp
    int add(int a, int b){
        return a+b;
    }
    int avr(int a, int b){
        return (a+b)/2;
    }

    int main(){
        int a = 10, b = 20;
        cout<<add(a,b)<<endl; 
        cout<<avr(a,b)<<endl;
        return 0;
    }
   ```
   - output
    - ```cpp
        30
        15
        ```
## Object
is a real-world entity such as a pen, chair, table, keyboard, mouse, etc. An object has two characteristics:
- State: It is represented by attributes of an object. 
- Behavior: It is represented by methods of an object. 
- Example in College Management System
    - Student
        - State: name, rollno, age, address, etc.
        - Behavior: read, write, etc.
    - Teacher
        - State: name, age, address, etc.
        - Behavior: read, write, etc.
    - Department
        - State: name, id, etc.
        - Behavior: read, write, etc.
- Example in Super Market Management System
    - Customer
        - State: name, id, address, etc.
        - Behavior: read, write, etc.
    - Product
        - State: name, id, price, etc.
        - Behavior: read, write, etc.
    - Employee
        - State: name, id, address, etc.
        - Behavior: read, write, etc.

## Class
A class is where Objects come from and It is a template or blueprint from which objects are created. It is a user-defined data type, which holds its own data members and member functions, which can be accessed and used by creating an instance of that class (object).
so A Class is the foundational element that leads to Object-Oriented programming. It is a blueprint or a prototype that defines the variables and the methods common to all objects of a certain kind.
 

## Class vs Stuct
| class | structure |
| --- | --- |
| if class specifier is not used then it is private by default | if structure specifier is not used then it is public by default |
|syntax:``` class class_name{};```|syntax:``` struct struct_name{};```|




## Why use Class?
- Classes are used to create new data types.
- Classes are used to group functions and data that work together.
- Classes are used to hide the implementation details and only show the important things to the user.
- Classes are used to reusibliity of code.


## Class and Objects 
- prototype           
    - ```cpp
        #include <iostream>
        using namespace std;

        class MyClass{
            public:
                int myNum;
                MyClass(){
                    myNum = 0;
                }
                void myMethod(){
                    cout<<"Hello World!"<<endl;
                }
                ~MyClass(){
                    cout<<"Destructor called"<<endl;
                }
        };
    
        int main(){
            MyClass myObj; // create an object of MyClass
            myObj.myNum = 15; // assign value to attribute myNum
            cout<<myObj.myNum<<endl; // print value of myNum
            myObj.myMethod();  // call the method myMethod on the object myObj
            return 0;
        }
        ``` 
- output
    - ```cpp
        15
        Hello World!
        Destructor called
        ```



## Access Specifiers
keyword that defines the access level of members (attributes and methods) in the class. There are three types of access specifiers in C++:
- public: members are accessible from outside the class.
- private: members cannot be accessed (or viewed) from outside the class.
- protected: members cannot be accessed from outside the class, however, they can be accessed in inherited classes.

## Constructor & Destructor
| Constructor | Destructor |
| --- | --- |
| Constructor is a special member function of a class that is executed whenever we create new objects of that class. | Destructor is a special member function of a class that is executed whenever we delete objects of that class or the program terminates. |
| Constructor is called automatically when the object is created. | Destructor is called automatically when an object in Life time is ended |
| Constructor can be used to set initial values for certain member variables. | Destructor can be used to release memory or perform other cleanup operations when the object is destroyed. |
| Constructor can be overloaded. | Destructor cannot be overloaded. |
| have same name as the class with no return type not even void. | have same name as the class with no return type not even void. |


## Prototype of Constructor
- ```cpp
    class MyClass{
        public:
            int myNum;
            MyClass(){
                // constructor body
                myNum = 0; // set initial value for myNum
            }
    };
    ```

## Prototype of Destructor
- ```cpp
    class MyClass{
        public:
         
            ~MyClass(){
                // destructor body
            }
    };
    ```


## passing objects to methods
- pass the object as an argument to the method and then access the object's attributes and call the object's methods.
- ```cpp
   class Distance{
        private:
            int feet;
            int inches;
        public:
            Distance(){
                feet = 0;
                inches = 0;
            }
            Distance(int f, int i){
                feet = f;
                inches = i;
            }
            void displayDistance(){
                cout<<"F: "<<feet<<" I: "<<inches<<endl;
            }
            void addDistance(Distance d1, Distance d2){
                inches = d1.inches + d2.inches;
                feet = 0;
                if(inches >= 12){
                    inches -= 12;
                    feet++;
                }
                feet += d1.feet + d2.feet;
            }
            Distance addDistance(Distance d1, Distance d2){
                Distance temp;
                temp.inches = d1.inches + d2.inches;
                temp.feet = 0;
                if(temp.inches >= 12){
                    temp.inches -= 12;
                    temp.feet++;
                }
                temp.feet += d1.feet + d2.feet;
                return temp;
            }
    };
    int main(){
        Distance d1(11,10), d2(5,11), d3;
        d3.addDistance(d1,d2);
        d3.displayDistance();
        Distance d4 = d3.addDistance(d1,d2);
        d4.displayDistance();
        return 0;
    }
    ```
- output
    - ```cpp
        F: 17 I: 9
        F: 29 I: 6
        ```

## Encapsulation
- Encapsulation is the process of binding the data and the functions that manipulate the data together.
- Encapsulation is used to achieve data hiding.
- Data hiding is the process of hiding the data from the outside world.
- Data hiding is used to achieve security.
- we access the data using the getter and setter methods.
- Prototype

    - ```cpp
        class Encapsulation{
            private:
                int x;
            public:
                void set(int a){
                    x = a;
                }
                int get(){
                    return x;
                }
        };
        int main(){
            Encapsulation obj;
            obj.set(5);
            cout<<obj.get()<<endl;
            return 0;
        }
        ```
        - output
            - ```cpp
                5
                ```
    
## Static Members
- Static members are shared by all objects of the class.
- Static members are declared using the static keyword.
- Static members are accessed using the scope resolution operator ::.
- Static members can be accessed without creating an object of the class.
- Static members can only access other static members.

- e.g
    - ```cpp
        class MyClass{
            public:
                static int myNum;
                static void myMethod(){
                    cout<<"Hello World!"<<endl;
                }
        };
        int MyClass::myNum = 15;
        int main(){
            MyClass::myMethod();
            cout<<MyClass::myNum<<endl;
            return 0;
        }
        ```
    - output
        - ```cpp
            Hello World!
            15
            ```
        
## Operator Overloading
- Operator overloading is a special feature of C++ that allows us to use operators like +, -, *, /, etc. on user-defined types.
- e.g 
    - ```cpp
        int a = 10 , b = 20;
        int c = a + b;
        ```
   - I want to add two objects in the same way
    - ```cpp
        Counter c1(10), c2(20), c3;
        c3 = c1 + c2;
        c3.displayCount();
      ```
    - How to do that?

    - ```cpp
        class Counter{
            private:
                int count;
            public:
                Counter(){
                    count = 0;
                }
                Counter(int c){
                    count = c;
                }
                void displayCount(){
                    cout<<"Count: "<<count<<endl;
                }
                Counter operator+(Counter c){
                    Counter temp;
                    temp.count = count + c.count;
                    return temp;
                }
                Counter operator-(Counter c){
                    Counter temp;
                    temp.count = count - c.count;
                    return temp;
                }
                Counter operator*(Counter c){
                    Counter temp;
                    temp.count = count * c.count;
                    return temp;
                }
               
               Counter operator/(Counter c){
                    Counter temp;
                    temp.count = count / c.count;
                    return temp;
                }

                // unary operator without argument 
                Counter operator++(){
                    Counter temp;
                    temp.count = ++count;
                    return temp;
                }
                // put int after operator to make it postfix
                Counter operator++(int){
                    Counter temp;
                    temp.count = count++;
                    return temp;
                }
               // and also for decrement
                Counter operator--(){
                    Counter temp;
                    temp.count = --count;
                    return temp;
                }

                Counter operator--(int){
                    Counter temp;
                    temp.count = count--;
                    return temp;
                }

        };
        int main(){
            Counter c1(10), c2(20), c3;
            c3 = c1 + c2;
            c3.displayCount();
            c3 = c1 - c2;
            c3.displayCount();
            c3 = c1 * c2;
            c3.displayCount();
            c3 = c1 / c2;
            c3.displayCount();
            c3 = ++c1;
            c3.displayCount();
            c3 = c1++;
            c3.displayCount();
            c3 = --c1;
            c3.displayCount();
            c3 = c1--;
            c3.displayCount();
            return 0;
        }
       ```
    - output
        - ```cpp
            Count: 30
            Count: -10
            Count: 200
            Count: 0
            Count: 11
            Count: 10
            Count: 11
            Count: 10
            Count: 9
            Count: 10
        ```
            
## Inheritance
- Inheritance is a mechanism in which one class acquires the property of another class.
- The class whose properties are acquired is called the base class.
- The class that acquires the properties of the base class is called the derived class.
- Inheritance is used to achieve code reusability.
- Reusing existing code saves time and effort.and also makes the program more readable.
- Prototype
    - ```cpp
       class BaseClass{
            // base class
       };
       // : is used to inherit from base class
        class DerivedClass: access-specifier BaseClass{
                // derived class
        };
         ``` 
- access-specifier
    - public
        - public and protected members of the base class becomes public members of the derived class.
        - Prototype:

            - ```cpp
                class Base{
                    public:
                        int a;
                    protected:
                        int b;
                };
                class Derived: public Base{
                    public:
                        void display(){
                            cout<<a<<endl;
                            cout<<b<<endl;
                        }
                };
                int main(){
                    Derived d;
                    d.a = 10;
                    d.b = 20;
                    d.display();
                    return 0;
                }
              ```
    - private
        - public and protected members the base class becomes private members of the derived class.
        - Prototype
        - ```cpp
            class Base{
                public:
                    int a;
                protected:
                    int b;
            };
            class Derived: private Base{
                public:
                    void display(){
                        cout<<a<<endl;
                        cout<<b<<endl;
                    }
            };
            int main(){
                Derived d;
                d.a = 10;
                d.b = 20;
                d.display();
                return 0;
            }
            ```
      
    - protected
        - public and protected members of the base class becomes protected members of the derived class.
        - Prototype :

            - ```cpp
                class Base{
                    public:
                        int a;
                    protected:
                        int b;
                };
                class Derived: protected Base{
                    public:
                        void display(){
                            cout<<a<<endl;
                            cout<<b<<endl;
                        }
                };
                int main(){
                    Derived d;
                    d.a = 10;
                    d.b = 20;
                    d.display();
                    return 0;
                }
                ```

## Constructors in Inheritance
- whether derived class's default constructor is called or parameterized constructor is called, the base class's default constructor is always called.
- To call base class's parameterized constructor, we use the member initialization list.
- Prototype: 

      - ```cpp
            class Base{
                public:
                    Base(){
                        cout<<"Base class's default constructor"<<endl;
                    }
                    Base(int x){
                        cout<<"Base class's parameterized constructor"<<endl;
                    }
            };
            class Derived: public Base{
                public:
                    Derived(){
                        cout<<"Derived class's default constructor"<<endl;
                    }
                    Derived(int x): Base(x){
                        cout<<"Derived class's parameterized constructor"<<endl;
                    }
            };
            int main(){
                Derived d1;
                Derived d2(10);
                return 0;
            }
            ```
        - output
            - ```cpp
                Base class's default constructor
                Derived class's default constructor
                Base class's parameterized constructor
                Derived class's parameterized constructor
                ```

## Types of Inheritance
- There are three types of inheritance in C++.
    - Single Inheritance
        - Prototype : 
        ```cpp
            class Base{
                // base class
            };
            class Derived: public Base{
                // derived class
            };
            ```
    - Multiple Inheritance
        - Prototype : 
        ```cpp
            class Base1{
                // base class
            };
            class Base2{
                // base class
            };
            class Derived: public Base1, public Base2{
                // derived class
            };
            ```
    - Hierarchical Inheritance
        - Prototype : 
        ```cpp
            class Base{
                // base class
            };
            class Derived1: public Base{
                // derived class
            };
            class Derived2: public Base{
                // derived class
            };
            ```
    - Multilevel Inheritance
        - Prototype : 
        ```cpp
            class Base{
                // base class
            };
            class Derived1: public Base{
                // derived class
            };
            class Derived2: public Derived1{
                // derived class
            };
            ```
    - Hybrid Inheritance
        - Prototype : 
            - ```cpp
                class Base{
                    // base class
                };
                class Derived1: public Base{
                    // derived class
                };
                class Derived2: public Base{
                    // derived class
                };
                class Derived3: public Derived1, public Derived2{
                    // derived class
                };
                ```



## What is Polymorphism?
- The word polymorphism means having many forms.
- is the ability of an object to take on many forms.
- with polymorphism, class objects belonging to the same hierarchical tree may have the functions with the same name but different behavior.

## Types of Polymorphism
- There are two types of polymorphism in C++.
    - Compile time polymorphism
        - also known as static polymorphism.
        - it is achieved by function overloading and operator overloading.
    - Runtime polymorphism
        - also known as dynamic polymorphism.
        - it is achieved by function overriding.
    

## Overloading Methods and Constructors
- Two or more methods in a class can have the same name as long as their signature are different. 
- Method signature is (No of Args , Type of Args , Order of Args)
- When this occurs, the methods are said to be overloaded , and this applies to constructors as well.
- Method overloading is important because it allows us to create multiple methods with the same name, but different functionality.
- e.g
    ```cpp
        class MyClass{
            public:
                int myNum;
                MyClass(){
                    // constructor body
                    myNum = 0; // initial value for myNum with 0
                }
                MyClass(int x){
                    // paramatrized constructor body
                    myNum = x; // set x into myNum
                }
                void myMethod(){
                    cout<<"Hello World!"<<endl;  // First myMethod that takes no arguments
                }
                void myMethod(int x){
                    cout<<"Hello World!"<<x<<endl; // Second myMethod with same name but has a different signture that takes an int as argument
                }
        };
        ```


## Functions Overriding using Virtual Functions
- Virtual functions are used to achieve runtime polymorphism.
- A virtual function is a function that is declared within a base class and is redefined (Overriden) by a derived class.
- A virtual function can be called through a pointer or a reference to the base class.
- Prototype : 
    - ```cpp
        class Base{
            public:
                virtual void display(){
                    cout<<"Base class's display function"<<endl;
                }
        };
        class Derived: public Base{
            public:
                void display(){
                    cout<<"Derived class's display function"<<endl;
                }
        };
        int main(){
            Base *b;
            Derived d;
            b = &d;
            b->display();
            return 0;
        }
        ```
        - output
            - ```cpp
                Derived class's display function
               ```

## abstraction 
- Abstraction is the process of hiding the implementation details and showing only the functionality to the user.
- Abstraction is achieved by using abstract classes and interfaces.
- ```cpp
    #include<iostream>
    using namespace std;
    class Shape{
        public:
            virtual void draw() = 0;
    };
    class Rectangle: public Shape{
        public:
            void draw(){
                cout<<"Drawing Rectangle"<<endl;
            }
    };
    class Circle: public Shape{
        public:
            void draw(){
                cout<<"Drawing Circle"<<endl;
            }
    };
    int main(){
        Shape *s;
        Rectangle r;
        Circle c;
        s = &r;
        s->draw();
        s = &c;
        s->draw();
        return 0;
    }
    ```
    - output
        - ```cpp
            Drawing Rectangle
            Drawing Circle
            ```
- In the above example, we have an abstract class Shape and two classes Rectangle and Circle which inherit the Shape class.
- The draw() method is declared as a pure virtual function in the Shape class.
- The pure virtual function is defined in the derived classes.
- The main() function creates a pointer of the Shape class and calls the draw() method using the pointer.
- The pointer is assigned to the address of the Rectangle object, so the draw() method of the Rectangle class is called.
- The pointer is assigned to the address of the Circle object, so the draw() method of the Circle class is called.



## Pure Virtual Functions
- A pure virtual function is a virtual function that is declared within a base class but is not defined (implemented).
- A pure virtual function is declared by assigning the value 0 to it.
- A class that contains a pure virtual function is called an abstract class.
- Prototype : 
    - ```cpp
        class Base{
            public:
                virtual void display() = 0;
        };
        class Derived: public Base{
            public:
                void display(){
                    cout<<"Derived class's display function"<<endl;
                }
        };
        int main(){
            Base *b;
            Derived d;
            b = &d;
            b->display();
            return 0;
        }
        ```
        - output
            - ```cpp
                Derived class's display function
               ```


## Function Overriding
- Function overriding is a feature that allows a derived class to override a function of its base class.
- It is the redefinition of the base class's function in the derived class with the same signature.
- It is used to achieve runtime polymorphism.
- Prototype : 
    - ```cpp
        class Base{
            public:
                void display(){
                    cout<<"Base class's display function"<<endl;
                }
        };
        class Derived: public Base{
            public:
                void display(){
                    cout<<"Derived class's display function"<<endl;
                }
        };
        int main(){
            Derived d;
            d.display();
            return 0;
        }
        ```
        - output
            - ```cpp
                Derived class's display function
               ```
## Friend Function & Friend Class
- A friend function of a class is defined outside that class's scope but it has the right to access all private and protected members of the class.
- It cannot be called from the object of that class. It can only be called from within its scope using the scope resolution operator.
- Prototype : 
    - ```cpp
        class Base{
            private:
                int a;
            protected:
                int b;
            public:
                int c;
                friend void display(Base);
        };
        void display(Base b){
            cout<<b.a<<endl;
            cout<<b.b<<endl;
            cout<<b.c<<endl;
        }
        int main(){
            Base b;
            b.a = 10;
            b.b = 20;
            b.c = 30;
            display(b);
            return 0;
        }
        ```
        - output
            - ```cpp
                10
                20
                30
               ```
- A friend class of another class is a class which is given the right to access the private and protected members of the other class.
- It is declared using the keyword friend in the class definition.
- Prototype : 
    - ```cpp
        class Base{
            private:
                int a;
            protected:
                int b;
            public:
                int c;
                friend class Derived;
        };
        class Derived{
            public:
                void display(Base b){
                    cout<<b.a<<endl;
                    cout<<b.b<<endl;
                    cout<<b.c<<endl;
                }
        };
        int main(){
            Base b;
            b.a = 10;
            b.b = 20;
            b.c = 30;
            Derived d;
            d.display(b);
            return 0;
        }
        ```
        - output
            - ```cpp
                10
                20
                30
               ```

# The End
- I hope this will help you to understand the OOPs concept in C++.
- If you have any doubt or suggestion, please add it in my repo. (Thanks)
