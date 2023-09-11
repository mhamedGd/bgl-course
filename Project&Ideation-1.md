# Project & Ideation 1

### [Project Files](https://drive.google.com/file/d/1usUwec9i2LnfamrIaADl2zT2GJfXyjDC/view?usp=sharing)

***Beware that there is a bug with the CourseButton Script, Don't worry about it and continue with what we took and we'll see how we can fix it.***

On this lecture we began our first full game created with the Unity Engine.

It will be a simple platformer where you're able to move horizontally, jump, collect coins, and avoid obstacles. Your goal is to reach an end point.

In this lecture we were able to create:
- Player movement and simple graphics.
- Simple Obstacles.
- Finish Point.
- Simple Finish Screen.
- Player Death.
- Mobile Controls.

What remains:
- Main Menu.
- Coins.
- Obstacle Variations.
- Score System
- Multiple Levels

---
<br><br><br><br><br><br>


# The UI

Have you ever heard of the terms "responsive app"? or "responsive website"? The idea of it is that different devices have different screen sizes, Computers usually these days are (1920x1080 or 1920x1200) in Pixels, While phones varry from (1440x3088) to (1080x2636). The issue here is different screens have different dimensions and so different ratios, and so how are you going to organize the User Interface to accomodate those different devices? Will you create a version for each and every device out there? Or create a few versions for the most used? This would compromise a lot of other devices in favour of the masses.

![Screen Ratios Image](/res/Demo%20Project/screen-ratios.png)
*The numbers are ratios, they don't have a unity*

## Unity provides tools for you to customize your UI in a way that would make it look in a similar manner to most screen sizes:

 ### Anchoring the UI Element:
 An anchor is an origin point, It makes the element stick to that point from its offset no matter how the screen changes its size. For example you can anchor the element towards the lower-left corner of the screen, this way if the screen gets taller the element will move down to the same distance it had originally from the corner.

![Anchor Example](/res/Demo%20Project//anchor-ex.png)

    You can notice in the previous example that before we set the anchor for the image to the lower-left corner it would not move according the screen size changing, but after setting the pivot it would dynamically try to keep the same distance it has from the lower-left corner.


#### How to set the Anchor of an element:

- Select the UI object (in this case an image)
- You will notice in the (Rect Transform) component a box on the top left
- Press the box and you will get the options of the anchors you would set
    
    *The anchor, anchors the object to the border of the parent object. In this case the parent of the Image is the Canvas so it borders it to the lower-left corner of the Canvas*

- Chose the option you want (The 9 options in the middle are for positioning the object, the ones on the right and bottom are for scaling the object with the screen).
- If you want the object to be anchored to an anchor and move there automatically then press the "Alt" key then choose an anchor

![Howto Ancho](/res/Demo%20Project/howto-anchor-1.png)

![Howto Ancho](/res/Demo%20Project/howto-anchor-2.png)


<br><br>

 ### Group Layouts:
 Another great way of achieving **Responsive User Interface** is via using the Group Layouts components.

 Group Layout Component are components that work on UI elements containers to position child objects Horizontally, Vertically, or in a Grid.

 #### How to add a Group Layout Component:
 We will use the **Vertical Layout Group** component to show you how it can be achieved.

 - Create any UI Element, For my case I will create an Empty UI Game Object (You can do it by creating an Empty GameObject inside a Canvas).
 - Anchor it to the Center and change its size to (600, 1000).
 - Add the component **Vertical Layout Group** to the Empty GameObject.
 - Change the property in the component called "Child Alignment** to **Middle Center** and uncheck the 2 bools for **Child Force Expand** called width and height.
 - Add 2 images as children to the object to test it.
 - You will now notice that the 2 images are sitting one on-top of eachother.
 - You can distance them by increasing the **Spacing** property in the component.

 ***Results:***

 ![Results](/res/Demo%20Project/result.png)

 ### It will Dynamically position all the elements sitting inside the Object Called Container without you having to move each element individually.

 ### Any UI Element can have the Group Layout Components not just Empty GameObjects.

 #### The names of the components:
 - **Vertical Layout Group**
 - **Horizontal Layout Group**
 - **Grid Layout Group**

 ---

 ## UI Exercise
 Let's create something similar to the Mobile Controls we created in the Lecture using what we've learned so far.

 - Create an image object inside the canvas.
 - Name it to **Container**.
 - Change its color to black.
 - Change its height to 300.
 - Anchor it to stretch on the bottom end of the screen by pressing **Alt** key and choosing the following
    ![](/res/Demo%20Project/exercise-1.png)
 - Add the **Horizontal Layout Group** component to it.
 - Change the **Child Alignment** property to Middle Center.
 - Uncheck **Child Force Expand** for width and height.
 - Add 3 images as children to **Container**.
 - Increase the **Spacing**.
 - Add an empty game object as a child to **Container**.
 - Drag it to make it the top child.
 - Increase its width in **Rect Transform** to 400.
 - Drag the first 2 of the images (the children inside **Container**) to the empty game object to make them its children.
 - Add to the empty game object A **Horizontal Layout Group** component, repeat what you did to the component on **Container** (Middle Center, Uncheck Child Force Expand, 100 Spacing).

![](/res/Demo%20Project/exercise-2.png)


#### You will notice that my result is different from yours, Your UI Elements would be bigger than mine or smaller depending. Even though you used the same numbers I provided.

The reason for that is the third tool unity provides for **Responsive User Interface**

 ### Canvas Scaler
 Most screens types have different pixel sizes, some screen have large pixels that you can even see the gap between the pixels (e.g Advertisement Screens), Some have extremely small pixels (e.g Phones). So to uniform their size we do the following:

 - On the Canvas you will notice a component called **Canvas Scaler**
 - Change the property **UI Scale Mode** to **Scale With Screen Size**.
 - Give an example of a size of a screen you would use in the Game window (I gave width:1080, height:1920).
 - Change the match property to (0.5) so that it would match the UI Elements with their widths and heights.
 - Now you would notice the same results I received.

 #### What we did now is provide Unity with a resolution reference that would help Unity decide how to scale UI Elements on different screen.
 #### Try different screens on the Simulator and check even IPads and Tablets, You will see that the Images all have the same scale no matter the size of the screen.