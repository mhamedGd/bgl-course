### Essentials 2

**Rigidbody**

![](res/Lecture-4-Essentials2/Aspose.Words.c4746fc1-7f8a-4932-85a6-ad3280962df1.001.png)

Rigidbody in Unity allows your GameObjects to act under the control of physics.

It allows you to interact with the physics of your objects and visualize how Unity is trying to simulate the physics of the real world. 

## Rigidbody properties:

**Use Gravity**

![](res/Lecture-4-Essentials2/Aspose.Words.c4746fc1-7f8a-4932-85a6-ad3280962df1.002.png)

This property determines whether gravity affects your game object or not. If it’s set to false, then the Rigidbody behaves as if it’s in outer space. In the unity interface, you can use arrow keys to navigate your object in the given plane with the help of arrow keys.

If *gravity* is enabled, the object will fall off as soon as it crosses the plane's boundary. However, if it’s disabled, it’ll continue on its path uninterrupted.

<br><br>

**Mass**

![](res/Lecture-4-Essentials2/Aspose.Words.c4746fc1-7f8a-4932-85a6-ad3280962df1.003.png)

This property of the Rigidbody is used for defining the mass of your object. By default, the value is read in kilograms. Different Rigidbodies that have a large difference in masses can cause the physics simulation to be highly unstable. The interaction between objects of different masses occurs in the same manner as it would in the real world. For instance, during a collision, a higher mass object pushes a lower mass object more.

A common misconception that rents users’ minds is that heavy objects will fall faster than lighter ones. This doesn’t hold in the world around us, the speed of fall is dictated by the factors of gravity and drag.

<br><br>


**Drag**

![](res/Lecture-4-Essentials2/Aspose.Words.c4746fc1-7f8a-4932-85a6-ad3280962df1.004.png)
Drag can be interpreted as the amount of air resistance that affects the object when moving from forces. When the drag value is set to 0, the object is subject to no resistance and can move freely.

On the other hand, if the value of the drag is set to infinity, then the object's movement comes to an immediate halt. Essentially, drag is used to slow down an object. The higher the value of drag, the slower the movement of the object becomes. 

Users must keep in mind the fact that they can apply Force to an active Rigidbody only. If the GameObject is inactive, then AddForce will not affect. Additionally, the Rigidbody must not be kinematic as well. Once a force is applied, the state of the Rigidbody is set to awake by default. The value of drag influences the speed of movement of an object under force. 

<br><br>

**Angular Drag**

![](res/Lecture-4-Essentials2/Aspose.Words.c4746fc1-7f8a-4932-85a6-ad3280962df1.005.png)
Drag can be interpreted as the amount of air resistance that affects the object when rotating from torque 0. As was the case with Drag, setting the value of Angular Drag to 0 eliminates the air resistance over here as well.

However, by setting the value of the Angular Drag to infinity, you can’t stop the object from rotating. The purpose of Angular Drag is only to slow down the rotation of the object. The higher the value of the Angular Drag, the slower the rotation of the object becomes. 

<br><br>

**Is Kinematic**

![](res/Lecture-4-Essentials2/Aspose.Words.c4746fc1-7f8a-4932-85a6-ad3280962df1.006.png)

When the *Is Kinematic* property is enabled, the object will no longer be driven by the physics engine. Forces, joints, or collisions will stop having an impact on the Rigibody. In this state, it can only be manipulated by its Transform.

Hitting objects under *Is Kinematic* brings about no change to their state as they can no longer exchange forces. 
This property comes in handy when you want to move platforms or wish to animate a Rigidbody with a HingeJoint attached.

<br><br>

**Interpolate**

![](res/Lecture-4-Essentials2/Aspose.Words.c4746fc1-7f8a-4932-85a6-ad3280962df1.007.png)

Users are advised to use interpolate in situations where they have to synchronize their graphics with the physics of their GameObject.

As the unity graphics are computed in the update function and the physics in the fixed update function, occasionally, they happen to be out of sync. To fix this lag, Interpolate is used. To learn more about Interpolate.

<br><br>

**Constraints**

![](res/Lecture-4-Essentials2/Aspose.Words.c4746fc1-7f8a-4932-85a6-ad3280962df1.008.png)

Constraints are used for imposing restrictions on the Rigidbody’s motion. It dictates which degrees of freedom are allowed for the simulation of the Rigidbody. By default, it is set to *RigibodyConstraints.None*.

There are two modes in Constraints- Freeze Position and Free Rotation. While Freeze Position restricts the movement of the Rigidbody in the X, Y, and Z axes, Freeze Rotation restricts their rotation around the same.

<br><br>

**Collision Detection**

![](res/Lecture-4-Essentials2/Aspose.Words.c4746fc1-7f8a-4932-85a6-ad3280962df1.009.png)

This property is used to keep fast-moving objects from passing through other objects without detecting collisions. For best results, users are encouraged to set this value to *CollisionDetectionMode.ContinuousDynamic* for fast-moving objects. As for the other objects that these need to collide with, you can set them to *CollisionDetectionMode.Continuous*.

These two options are known for having a big impact on physics performance. However, if you don’t have any problems with fast-moving objects colliding with one another, then you can leave it set to the default value of *CollisionDetectionMode.Discrete*. 


<br><br>

## Accessing the Rigidbody component:

To acces the rigidbody first we must add it to the GameObject,here is how: 

1. select the GameObject that we want to add the Rigibody to it
1. from inspector window click the Add component button
   
   ![](res/Lecture-4-Essentials2/Aspose.Words.c4746fc1-7f8a-4932-85a6-ad3280962df1.010.png)

1. search for the Rigidbody component select it and add it

    **![](res/Lecture-4-Essentials2/Aspose.Words.c4746fc1-7f8a-4932-85a6-ad3280962df1.011.png)**


After adding a rigidbody we need to access its properties
first, we need to declare it in the script:

#### [Rigidbody](https://docs.unity3d.com/ScriptReference/Rigidbody.html)
#### [MonoBehaviour](https://docs.unity3d.com/ScriptReference/MonoBehaviour.html)


```cs
    using UnityEngine;

    Rigidbody m_Rigidbody;

    public class Example : MonoBhaviour
    {
        void Start()    
        {   
        }
    }
```


***We need to reference the rigidbody :
in start function using getcomponent which is basically
Gets a reference to a component of type T on the specified GameObject.***

Syntax:
```cs
    m_Rigidbody = gameObject.GetComponent<ComponentType>();
```

```cs
using UnityEngine;
public class Example : MonoBehaviour
{

    Rigidbody m_Rigidbody;

    void Start()
    { 
        //Fetch the [Rigidbody]from the [GameObject] with this script attached
        m_Rigidbody = GetComponent<Rigidbody>();
    }
}
```

<br><br>
<br>

## Rigidbody methods:


**Add Force**

This method is used to add a force to the Rigidbody. Force is always applied continuously along the direction of the force vector. Further, specifying the Force Mode enables the user to change the type of force to acceleration, velocity change, or impulse. 

**syntax:**

```cs
using UnityEngine;

public class Example : MonoBehaviour

{

    Rigidbody m_Rigidbody

    public float jumpForce = 350f;

    void Start()
    {

        //Fetch the [Rigidbody](https://docs.unity3d.com/ScriptReference/Rigidbody.html) from the [GameObject](https://docs.unity3d.com/ScriptReference/GameObject.html) with this script attached

        m_Rigidbody = GetComponent<Rigidbody>();

    }

    void FixedUpdate()
    {

        if (Input.GetKeyDown(KeyCode.Space))
        {
        //Apply a force to this [Rigidbody](https://docs.unity3d.com/ScriptReference/Rigidbody.html) in direction of this GameObjects up axis
            m_Rigidbody.AddForce(Vector3.up * jumpForce);
        }

    }

}
```


**AddForce**([Vector3](https://docs.unity3d.com/ScriptReference/Vector3.html) **force**);
***Here is an example of using AddForce function to make a player jump.***

```cs
using UnityEngine;

public class Example : MonoBehaviour
{
    Rigidbody m_Rigidbody;
    public float jumpForce = 350f;

    void Start()
    {
        m_Rigidbody = GetComponent<Rigidbody>();
    }

    void FixedUpdate()
    {
        if(Input.GetKeyDown(KeyCode.Space))
        {
            m_Rigidbody.AddForce(Vector3.up * jumpForce);
        }
    }
}
```

---

## Create Basic Movement

The movement basically is changing the position of GameObject and there are many ways to move a GameObject in Unity 3D, let’s use one of the simplest ways.

In order to move a GameObject, you need to specify a direction in which to translate it through space, and to represent a direction, you need to specify the three dimensions (x, y, z). To do this easily, Unity 3D provides us with a special data type called Vector3.
so what is a Vector3?

### Vector3

It represents 3D vectors and points holding three floats values(x,y,z).

This structure is used throughout Unity to pass 3D positions and directions around. It also contains functions for doing common vector operations.

**Static Properties**

We can use the static properties as shortcuts for setting the properties of the Vector3:

|[back](https://docs.unity3d.com/ScriptReference/Vector3-back.html)|Shorthand for writing Vector3(0, 0, -1).|
| :- | :- |
|[down](https://docs.unity3d.com/ScriptReference/Vector3-down.html)|Shorthand for writing Vector3(0, -1, 0).|
|[forward](https://docs.unity3d.com/ScriptReference/Vector3-forward.html)|Shorthand for writing Vector3(0, 0, 1).|
|[left](https://docs.unity3d.com/ScriptReference/Vector3-left.html)|Shorthand for writing Vector3(-1, 0, 0).|
|[one](https://docs.unity3d.com/ScriptReference/Vector3-one.html)|Shorthand for writing Vector3(1, 1, 1).|
|[right](https://docs.unity3d.com/ScriptReference/Vector3-right.html)|Shorthand for writing Vector3(1, 0, 0).|
|[up](https://docs.unity3d.com/ScriptReference/Vector3-up.html)|Shorthand for writing Vector3(0, 1, 0).|
|[zero](https://docs.unity3d.com/ScriptReference/Vector3-zero.html)|Shorthand for writing Vector3(0, 0, 0).|
###
### Properties
We can set the value of the Vector3 separately using the properties:	

|[x](https://docs.unity3d.com/ScriptReference/Vector3-x.html)|X component of the vector.|
| :- | :- |
|[y](https://docs.unity3d.com/ScriptReference/Vector3-y.html)|Y component of the vector.|
|[z](https://docs.unity3d.com/ScriptReference/Vector3-z.html)|Z component of the vector.|

Declaring (Creating) 
Declaring a Vector3 it’s the same way as declaring any variable:
### **Syntax**
```cs
Vector3 nameOfTheVariable;
```
You can declare it and give it initial value:
```cs
Vector3 nameOfTheVariable = new Vector3(float,float,float);
```
### Example
Create a **Vector3** called “direction” and assign its values **x=2.5,y=8,z=26.3**:
```cs
Vector3 direction = new Vector3(2.5f,8f,26.3f);

void start(){

}
```

**Or** You can Create it and assign its values in the Start function
```cs
Vector3 direction;

void start(){

    direction = new Vector3(2.5f,8f,26.3f);

}
```


**Or** We can use the static properties as shortcuts for setting the values of the Vector3
```cs
Vector3 direction;

void start(){

    direction = Vector3.up; 
    //note: vector3.up means Vector3(0,1,0);

}
```


Alright, now we know how to represent a direction it's time to use it, where we're going to use the direction?
As mentioned earlier, movement primarily involves changing the position of a GameObject. The position is a property of the Transform component. Therefore, to change the position of an object, we need to access its Transform component and utilize it using the function provided by Unity 3D, there is a function called “Translate” which help us to translate the position of GameObject through the space.


<br><br>
## [Transform](https://docs.unity3d.com/ScriptReference/Transform.html).Translate
### **Description**
**Moves the transform in the direction and distance of translation.**

**Syntax**
---
```cs
transform.Translate(Vectore3);
```
**examples:**
```cs
    void Update
    {
        // Move the object forward along its z axis
        transform.Translate(Vector3.forward);
    }
```
```cs
using UnityEngine;
using System.Collections;

public class ExampleClass : MonoBehaviour
{

    void Update()
    {
        // Move the object forward along its z axis 1 unit/second.
        transform.Translate(Vector3.forward) * Time.deltaTime
    }

}
```


In the above example, the object will move too fast because it moves every frame. To ensure it moves at a 1 unit per second, we need to multiply it by a value called 'deltaTime'.this value is property of class called “Time”

### now let’s add speed factor to  control its speed movement 


```cs
using UnityEngine;
using System.Collections;

public class ExampleClass : MonoBehaviour
{
    float speed = 5.8f;

    void Update()
    {
        // Move the object forward along its z axis 5.8 unit/second.
        transform.Translate(Vector3.forward) * speed * Time.deltaTime
    }

}
```