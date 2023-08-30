# Object-Oriented Programming - 1

<br>

## Classes and Objects:

### What is a class?

- ***Class and object are basic building blocks in object-oriented programming languages. A class is written by a programmer in a defined structure to create an object (computer science) in an object oriented programming language. It defines a set of properties and methods that are common to all objects of one type.***
<br> - **Simple Wikipedia**

- ***In object-oriented programming, a class is an extensible program-code-template for creating objects, providing initial values for state (member variables) and implementations of behavior (member functions or methods).***
<br> - **Wikipedia**

- ***In programming, particularly in object-oriented programming (OOP), a class is a blueprint or template for creating objects. An object is an instance of a class, containing real values instead of variables. The class defines the state (data members) and behavior (methods) that the created objects possess.***
<br> - **Phind - Model GPT-4**

The former definitions are what a class is officially, and to simplify it. A Class is a way to store code. in a Class you can store variables and methods. Think of it as a file in which your code is in. The difference here is that you can't access your file directly to get the code you've written in C#, but you can access a class.

Let's consider the following scenario, You write the following scripts
```cs
using UnityEngine;

public class Source : MonoBehvaiour {

    void Start() {

    }

    void Update() {

    }

    public void PrintHello() {
        print("Hello Hello")
    }
}
```

```cs
using UnityEngine;

public class User : MonoBehvaiour {

    void Start() {
        PrintHello();
    }

    void Update() {

    }
}
```

You have 2 scripts (Source and User), in Source you have a public method called "PrintHello", and you want to call it in the other script called "User". **How do you achieve that???**

To answer that question, We need to detour a bit from the question and go into something you're more familiar with.

```cs
Rigidbody rb;

void Start() {
    rb = GetComponent<Rigidbody>();

    rb.AddForce(Vector3.up);
}
```

**What does this code do?** It makes the object bounce up on the start of the game.

but... What is rb.AddForce? Ok AddForce is a method but what is rb? and What is Rigidbody? Why is it written the same way you would write a variable?
<br> Let's break this down....
- just like 
```cs
int number;
```
is a variable,
so is 
```cs
Rigidbody rb;
```
but not entirely.. You see we previously studied that there are only a limited number of variable types (bool, int, float, and char) and that is true, while something like "Rigidbody" is a way of storing a class in the same way you store a primitive variable. We call them **Objects**.

Objects aren't something new to you, we've been using objects for a while actually. "string" is an object, If you thought that a string was a primitive like int or bool then you're wrong. A string is basically a series of chars and it contains useful methods to manipulate text.

Now, isn't this cool? You can basically create your own variable types! How about we create a custom type and make it do something for us?
Let's go
```cs
using UnityEngine;

public class Tashreeb : Monobehaviour {
    public void EatTashreeb() {
        print("I ate Tashreeb");
    }
}
```
I just created a script with a method called "EatTashreeb", You can consider this class a variable type like (int, bool, float...). You can now try adding it in your script the same way you'd do a variable.

```cs
using UnityEngine;

public class Test : MonoBehaviour {
    Tashreeb tashreeb;

    void Start() {
        tashreeb = new Tashreeb();
        tashreeb.EatTashreeb(); // Output: "I ate Tashreeb"
    }
}
```

"tashreeb = new Tashreeb()" is the way you assign objects (class variables). It's the same as saying "int i = 3" but since a class isn't a value we need to specifically say this is a new **Tashreeb** object.

with **Tashreeb** we can now write code (variables and methods) and store them to use them in other script files.

***Notice how we wrote the keyword "public" before void EatTashreeb(), That's because we cannot access any method or variable of a class from outside unless they're public.***

You can also assign the object tashreeb outside of **Start**
```cs
    Tashreeb tashreeb = new Tashreeb();
```

We can now go back to the original example and explain how it works.

```cs
using UnityEngine;

public class Source : MonoBehvaiour {

    void Start() {

    }

    void Update() {

    }

    public void PrintHello() {
        print("Hello Hello")
    }
}
```

```cs
using UnityEngine;

public class User : MonoBehvaiour {

    void Start() {
        PrintHello();
    }

    void Update() {

    }
}
```

We know now that in order to call the method **PrintHello** from another class we need an object of the class. We declare it like this:

```cs
using UnityEngine;

public class User : MonoBehvaiour {
    
    Source iLikeIceCream = new Source(); // Just like a variable you can name the object anything you like

    void Start() {
        iLikeIceCream.PrintHello();
    }

    void Update() {

    }
}
```

**class Source** is the one that holds the code you store and **class User** is the one that uses the custom type you created.

---

**You will notice a warning in the Console in Unity (Yellow in color), This is because you are not allowed to assign a class that has " : MonoBehaviour" this way. To get rid of this warning do either**:

- Remove ": MonoBehaviour" in script **Source**, but this will make you lose the ability to call any method that belongs to Unity.
    ```cs
    using UnityEngine;

    public class Source {
        // Start and Void will not work because they need ": MonoBehaviour"
        void Start() {

        }

        void Update() {

        }

        public void PrintHello() {
            print("Hello Hello") //This line will have an error because print is a method belonging to Unity
        }
    }
    ```
- Use "gameObject.AddComponent<Source>()" instead of "new Source()" in **User**.
    ```cs
    using UnityEngine;

    public class User : MonoBehvaiour {
        
        Source iLikeIceCream; // Just like a variable you can name the object anything you like

        void Start() {
            iLikeIceCream = gameObject.AddComponent<Source>(); // You can only call this inside a method
            iLikeIceCream.PrintHello();
        }

        void Update() {

        }
    }
    ```
<br>

**The reaseon this warning happens is because "iLikeIceCream" will be just a block of memory in the code and will not be attached to any GameObject in the scene, so it will require some experience in Unity to be able to handle it, so it's adviced that you use "gameObject.AddComponent<>()" to assign an Object of a Class as long as the Class has ": MonoBehaviour"**


---
**TO BE CONTINUED**
