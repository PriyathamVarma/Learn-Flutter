[<- Part 03: Variables, Functions](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Dice-Game/Part-03.md) |

<hr/>

## Using buttons and multiple constructor functions

<details>

<summary>  Buttons in Flutter </summary>

Flutter offers a variety of buttons to enhance user interaction in your apps.

**Types of Buttons**

- TextButton: A plain button with text content. Ideal for secondary actions or dialogs.

- ElevatedButton: A raised button with a shadow, often used for primary actions.

- OutlinedButton: A button with a border outline and no fill, suitable for subtle actions.

- IconButton: A compact button displaying only an icon.

- FloatingActionButton: A circular button, typically placed near the bottom corner for primary actions.

**Customizing Buttons**

- Styling: Modify button appearance using the style parameter (color, padding, shadow, etc.).

- Theme: Apply global styles using button themes (TextButtonTheme, ElevatedButtonTheme, etc.).

- On Press: Define the button's behavior using the onPressed callback.


> [!TIP]
> Additional Considerations

> Accessibility: Ensure proper text contrast and labels for screen readers.

> State Management: Update button appearance based on user interaction and app state.

> Button Themes: Create custom themes for consistent button styles throughout your app.




**Sample Code**


```dart
// Text Button
TextButton(
  onPressed: () => print('Clicked!'),
  child: Text('Click Me'),
),

// Elevated Button
ElevatedButton(
  onPressed: () => print('Do something important'),
  child: Text('Start Now'),
),

// Floating Action Button
FloatingActionButton(
  onPressed: () => Navigator.pushNamed(context, '/'),
  child: Icon(Icons.add),
),
```


  
</details>


### Stateful widgets

In Flutter, stateful widgets are widgets that can change their appearance or behavior in response to user interactions, data updates, or other events. They manage their own internal state, allowing for dynamic and interactive UI elements.

**Key Concepts**

> State: A stateful widget's state is the information that can change over time, such as the value of a text field, the selection in a list, or the visibility of a widget.

> StatefulWidget class: The base class for stateful widgets.

> State class: A companion class that holds the widget's state and manages its updates.

> setState() method: Used to trigger a rebuild of the widget when its state changes.

**How Stateful Widgets Work** 

> Creation: When a stateful widget is created, Flutter instantiates both the StatefulWidget and its associated State object.

> State Updates: When an event occurs (user interaction, data change, etc.), the setState() method is called within the State object.

> Rebuild: Flutter calls the build() method of the StatefulWidget again, passing the updated State object.

> UI Rendering: The build() method creates a new widget tree based on the current state, and Flutter updates the UI accordingly.

 **Code for stateful widget**

```dart
/* This is a stateful widget
    that will be used to change the
    image randomly 
*/

// Imports
// Packages
import "package:flutter/material.dart";

// Widget
class DiceRoll extends StatefulWidget {
  const DiceRoll({super.key});

  @override
  State<DiceRoll> createState() {
    return _DiceRollState();
  }
}

// The return type of DiceRoll class

class _DiceRollState extends State<DiceRoll> {
  var currentDiceImage = "assets/images/Dice03.png";

  void onPressed() => {
        setState(() {
          // To change the state
          currentDiceImage = "assets/images/Dice01.png";
        }),
        debugPrint("Image changing..."),
      };

  @override
  Widget build(context) {
    return Column(
      mainAxisAlignment: MainAxisAlignment.center, // Center children vertically
      children: [
        //CustomTextContainer("hello"),
        Image.asset(currentDiceImage),
        TextButton(
            onPressed: onPressed,
            child: const Text(
              "Click here",
              selectionColor: Colors.black,
            )),
      ],
    );
  }
}
```

**Random number generator**

```dart
/* 
    This is a stateful widget
    that will be used to change 
    the image randomly 
*/

// Imports
// Packages
import "dart:math";

import "package:flutter/material.dart";

// Widget
class DiceRoll extends StatefulWidget {
  const DiceRoll({super.key});

  @override
  State<DiceRoll> createState() {
    return _DiceRollState();
  }
}

// The return type of DiceRoll class

class _DiceRollState extends State<DiceRoll> {
  var diceRollNumber = 1;

  void onPressed() => {
        // To change the state
        setState(() {
          // Create a Random instance to use its methods
          var random = Random();
          diceRollNumber = random.nextInt(6) + 1;
        }),
        debugPrint("Image changing..."),
      };

  @override
  Widget build(context) {
    return Column(
      mainAxisAlignment: MainAxisAlignment.center, // Center children vertically
      children: [
        //CustomTextContainer("hello"),
        Image.asset("assets/images/Dice0$diceRollNumber.png"),
        TextButton(
            onPressed: onPressed,
            child: const Text(
              "Click here",
              selectionColor: Colors.black,
            )),
      ],
    );
  }
}
```



<hr/>

[<- Part 03: Variables, Functions](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Dice-Game/Part-03.md) |

