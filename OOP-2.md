# Object-Oriented Programming - 2

### [Part 1](https://youtu.be/npBqfu3zpRo?si=OZGztG_XbnZUoPGW) <br>
### [Part 2](https://youtu.be/-z5I_5GadmQ?si=CAEf3LkHLRUOKXuo)

---

## Scoring Coins and Timer

The way we'll be achieving this is via separating the logic of storing the Data and Methods and Manipulating (Changing) them from Visualising it (Showing it on the screen) and for that we'll need a game manager and a UI manager. So we will create 2 scripts on called "GameManager" the other "UIManager".


### Timer

#### Setting up the UI:

For a timer we will first in the "Hierarchy" create a new GameObject of type "Canvas":
 - Click the + symbol in the Hierarchy window.
 - Hover over UI
 - Click on Canvas

In The Canvas We will create a new "Text - TextMeshPro" GameObject:
 - Click the + symbol in the Hierarchy window.
 - Hover over UI
 - Click on Text - TextMeshPro.
 - Name the object "Timer".
 - Repeat the previous steps but call the object "Coins Counter".

**You will probably see a new window that says "import TMP essentials", press that button and then after it finished Exit that window.** *It's important to note that you shouldn't press "import Examples"*.\

**From here you can place the text the way you like it (Top of the screen, Bottom, Top-Right, etc...).** in my project I positioned the Timer to the top of the screen and made the Coins Counter bellow it.
<br><br>

---

#### Creating the GameManager and UIManager:

*GameManager*:
 - Create a new Empty GameObject and attach the GameManager Script on it.

*UIManager*:
 - You can attach this script to anything that remains in the scene and doesn't get destroyed, I prefer that you either attach it to the GameManager object or the Canvas.

in the **GameManager** Script:
 - Create a new variable called "elapsedTime" of type float and make it public:
 ```cs
 public float elapsedTime;
 ```
 - in Update add Time.deltaTime to elapsedTime:
 ```cs
void Update(){
    elapsedTime += Time.deltaTime;
}
 ```
 - Now to register the coins scoring, Create a new variable of type int called totalCoins and make it public:
 ```cs
 public float elapsedTime;
 public int totalCoins;
 ```

 in the **UIManager** script:
  - Add the following line bellow "using UnityEngine":
```cs
using UnityEngine;
using TMPro
```
 - Create 2 new objects (variables) of type "TextMeshProUGUI" both being public, the first one called "timerText", the second called "coinsText":
 ```cs
 public TextMeshProUGUI timerText;
 public TextMeshProUGUI coinsText;
 ```

 - Create a reference to GameManager as a variable:
 ```cs
 public GameManager gm;
 ```
 
 - in Update add the following:

 ```cs
 void Update() {
    timerText.text = gm.elapsedTime.ToString("0.00");
    coinsText.text = gm.totalCoins.ToString();
 }
 ```

 in the **Coin** script:
  - Create a new variable of type GameManager
  ```cs
  public GameManager gm;
  ```
  - in the DoPickup method add the following:
  ```cs
  public override void DoPickup(){
    gm.totalCoins += coinAmount;
  }
  ```

#### Final Step

 - in the UIManager component, drag the "Timer" object to the "timerText" property
 - in the UIManager component, drag the "Coins Counter" object to the "coinsText" property
 - in the UIManager component, drag the "GameManager" object to the "gm" property
 - in the Coin component, drag the "GameManager" object to the "gm" property

**Remember that above I said component, Which means the script we attached to the game object**

**in the Coin object, there is the Coin Component. Remember to change the Coin Amount property to something above zero**


### The Scripts

- **GameManager**
```cs
using System;
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class GameManager : MonoBehaviour
{
    public float elapsedTime;
    public int totalCoins;
    
    private void Update()
    {
        elapsedTime += Time.deltaTime;
    }
}

```

- **UIManager**
```cs
using System;
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using TMPro;

public class UIManager : MonoBehaviour
{
    public GameManager gm;

    public TextMeshProUGUI timer;
    public TextMeshProUGUI coins;

    private void Update()
    {
        timer.text = gm.elapsedTime.ToString("0.00");
        coins.text = gm.totalCoins.ToString();
    }
}

```

- **Coin**
```cs
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Coin : Pickups
{
    public int coinAmount;
    public GameManager gm;

    public override void DoPickup()
    {
        gm.coinsCounter += coinAmount;
    }
}

```