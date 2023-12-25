[<- Part 02: Classes, Custom Widgets](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Dice-Game/Part-01.md) |
[Part 04: Stateful Widgets ->](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Dice-Game/Part-03.md)

<hr/>

## Splitting code into different files

The classes created can be stored in another file 

```
x-> lib
|    |-> main.dart
|    |-> custom_box_container.dart
|
x
```

Now, in the new file 

```dart
/* This widget is simple
   for showing a box with a
   background color and some text */

// IMPORTS
import 'package:flutter/material.dart';

// Custom Widgets
class CustomBoxContainer extends StatelessWidget {
  const CustomBoxContainer({super.key});

  @override
  Widget build(context) {
    return Container(
      decoration: BoxDecoration(
        color: const Color(0xfd7272b5),
        border: Border.all(
          width: 8,
        ),
        borderRadius: BorderRadius.circular(24),
      ),
      child: const Center(
        child: SizedBox(
          child: Text(
            'Hell',
            style: TextStyle(fontSize: 24, color: Colors.black),
          ),
        ),
      ),
    );
  }
}
```

The main file becomes

```dart
// This is the main dart file
// IMPORTS
// PACKAGES
import 'package:flutter/material.dart';

// WIDGETS
import 'custom_box_container.dart';

/* main() function executes 
the runApp() function 
which renders the widgets*/

void main() {
  runApp(
    const MaterialApp(
      home: Scaffold(
        body: CustomBoxContainer(),
      ),
    ),
  );
}
```

**Caution** - Check for proper imports

## Variables

### Definition

Variables are named containers that store data values for use throughout your code.
They allow you to manage and manipulate information dynamically within your Flutter app.

<details>

<summary> Expand </summary>

### Types of Variables

**Global Variables:** Declared outside of any class or function, accessible from anywhere in the app. Use sparingly to avoid namespace pollution.

**Local Variables:** Declared within a function or method, accessible only within that scope.

**Instance Variables:** Declared within a class, accessible to all instances of that class.

**Static Variables:** Declared within a class using the static keyword, shared among all instances of the class.


### Declaring Variables

Use the var, final, or const keywords:
``` var: ``` Declares a variable with an inferred type (can change later).

``` final: ```  Declares a variable that can only be assigned a value once.

``` const: ```  Declares a constant variable with a compile-time constant value.

Example: ```  var name = "Alice"; ``` 

### Common Data Types

``` int: ```  Integers (whole numbers)

``` double: ```  Floating-point numbers (decimals)

``` String: ```  Text

``` bool: ```  Booleans (true or false)

``` List: ```  Ordered collections of items

``` Map: ```  Unordered collections of key-value pairs

### Using Variables in Widgets

Variables are used within widget classes to store and manage data for the UI.

Example:
```Dart
class MyWidget extends StatelessWidget {
  final String message = "Hello, world!";

  @override
  Widget build(BuildContext context) {
    return Text(message);
  }
}
```

### Handling Dynamic Data with State Management

For data that changes over time, use state management techniques:

**StatefulWidgets:** Manage state within individual widgets.

**Provider:** Share state across multiple widgets in a tree.

**BLoC:** Separate business logic from UI for complex apps.
   
</details>


## Configurable widgets

Send data from parent widget to child widget

> main.dart file

```dart
// This is the main dart file
// IMPORTS
// PACKAGES
import 'package:flutter/material.dart';

// WIDGETS
import 'package:dice/custom_box_container.dart';

/* main() function executes 
the runApp() function 
which renders the widgets*/

void main() {
  runApp(
    MaterialApp(
      home: Scaffold(
        body: CustomBoxContainer(0xfd7272b6),
      ),
    ),
  );
}
```

> custom_box_container.dart file

```dart
/* This widget is a simple widget
   for showing a box with a
   background color and some text */

// IMPORTS
// PACKAGES
import 'package:flutter/material.dart';

// Widgets
import 'package:dice/custom_text_container.dart';

// Custom Widgets
// ignore: must_be_immutable
class CustomBoxContainer extends StatelessWidget {
  CustomBoxContainer(this.customText, {super.key});

  int customText;

  @override
  Widget build(context) {
    return Container(
      decoration: BoxDecoration(
        color: Color(customText),
        border: Border.all(
          width: 8,
        ),
        borderRadius: BorderRadius.circular(24),
      ),
      child: Center(
        child: SizedBox(
          child: CustomTextContainer("hell0"),// This is for next child widget
        ),
      ),
    );
  }
}

```

## Using Images

> Create a folder called as assets

> Create a subfolder called images

> Upload all the required images

In pubspec.yaml

```yaml
  assets:
    - assets/images/Dice01.png
    .... reamianing images
```

In the code

```dart

/* This widget is a simple widget
   for showing a box with a
   background color and some text */

// IMPORTS
// PACKAGES
import 'package:flutter/material.dart';

// Widgets
import 'package:dice/custom_text_container.dart';

// Custom Widgets
// ignore: must_be_immutable
class CustomBoxContainer extends StatelessWidget {
  CustomBoxContainer(this.customText, {super.key});

  int customText;

  @override
  Widget build(context) {
    return Container(
      decoration: BoxDecoration(
        color: Color(customText),
        border: Border.all(
          width: 8,
        ),
        borderRadius: BorderRadius.circular(24),
      ),
      child: Center(
        child: SizedBox(
          child: Column(
            children: [
              CustomTextContainer("hello"),
              Image.asset('assets/images/Dice01.png'),
            ],
          ),
        ),
      ),
    );
  }
}


```




### Best Practices

> [!IMPORTANT]
> Choose appropriate variable types and scopes to ensure code readability and maintainability.

> [!TIP]
> Manage state effectively for dynamic data to create interactive and responsive Flutter apps.


<hr/>

[<- Part 02: Classes, Custom Widgets](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Dice-Game/Part-01.md) |
[Part 04: Stateful Widgets ->](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Dice-Game/Part-03.md)
