# Essentials 1

## C# Variables

Variables are containers for storing data values.

In C#, there are different **types** of variables (defined with different keywords), for example:

- int - stores integers (whole numbers), without decimals, such as 123 or -123
- double - stores floating point numbers, with decimals, such as 19.99 or -19.99
- char - stores single characters, such as 'a' or 'B'. Char values are surrounded by single quotes
- string - stores text, such as "Hello World". String values are surrounded by double quotes
- bool - stores values with two states: true or false
-----
Declaring (Creating) Variables

To create a variable, you must specify the type and assign it a value:
### **Syntax**
*type variableName = value;*

Where *type* is a C# type (such as int or string), and *variableName* is the name of the variable (such as **x** or **name**). The **equal sign** is used to assign values to the variable.


### To create a variable that should store text, look at the following example:

***Example***

Create a variable called **name** of type string and assign it the value 
"**John**":

```cs
string name = "John";

void start(){

print(name);

}
```
<br>

### To create a variable that should store a number, look at the following example

***Example***

Create a variable called **myNum** of type int and assign it the value **15**:

```cs
int health = 100;

void start(){

print(health);

}
```
<br>

### You can also declare a variable without assigning the value, and assign the value later:

***Example***

```cs
int myNum;

myNum = 15;

void start(){

print(myNum);

}
```

#### Note that if you assign a new value to an existing variable, it will overwrite the previous value:
***Example***
Change the value of myNum to 20:

```cs
int myNum = 15;

void start(){

myNum = 20; // myNum is now 20

print(myNum);

}
```

-----

## Other Types
A demonstration of how to declare variables of other types:

***Example***

```cs
int myNum = 5;

double speed = 5.99;

char key = 'D';

bool isAlive = true;

string name = "Ali";
```

---
## Methods
A **method** is a block of code which only runs when it is called.
You can pass data, known as parameters, into a method.
Methods are used to perform certain actions, and they are also known as **functions**.
Why use methods? To reuse code: define the code once, and use it many times.

**There are two types**

- Procedure: doesn’t return a value 
- Function: must return a value
-----
### Create a Method

A method is defined with the name of the method, followed by parentheses **()**. Unity provides some pre-defined methods, which you already are familiar with, such as Start(), but you can also create your own methods to perform certain actions:

Example of creating Procedure
```cs
    void MyMethod() 
    {

        // code to be executed

    }
```



**Example Explained**

- **MyMethod()** is the name of the method
- **void** means that this method does not have a return value. You will learn more about return values later in this chapter

***Note:*** In C#, it is good practice to start with an uppercase letter when naming methods, as it makes the code easier to read.

-----
### Call a Method

To call (execute) a method, write the method's name followed by two parentheses **()** and a semicolon ***;***

#### In the following example, MyMethod() is used to print a text (the action), when it is called:

***Example***

Inside Start(), call the myMethod() method:
```cs
    void MyMethod()
    {
        print("I just got executed!");
    }

    void Start()
    {
        MyMethod();
    }

// Outputs "I just got executed!"
```



## Defining a function in C#
When you define a function, you basically declare the elements of its structure. The syntax for defining a method in C# is as follows −
```cs
    <Return Type> <Method Name>(Parameter List) {
        Function  Body
    }
```

Following are the various elements of a function −

- **Access Specifier** − This determines the visibility of a variable or a method from another class.
- **Return type** − A method may return a value. The return type is the data type of the value the method returns. If the method is not returning any values, then the return type is **void**.
- **Method name** − Method name is a unique identifier and it is case sensitive. It cannot be same as any other identifier declared in the class.
- **Parameter list** − Enclosed between parentheses, the parameters are used to pass and receive data from a method. The parameter list refers to the type, order, and number of the parameters of a method. Parameters are optional; that is, a method may contain no parameters.
- **Method body** − This contains the set of instructions needed to complete the required activity.
## Example
Following code snippet shows a function *FindMax* that takes two integer values and returns the larger of the two. It has public access specifier, so it can be accessed from outside the class using an instance of the class.

```cs
    int FindMax(int num1, int num2) {
        int result;

        if (num1 > num2)
        {
            result = num1;
        }else
        {
            result = num2;
        }

        return result;
    }
```

---


