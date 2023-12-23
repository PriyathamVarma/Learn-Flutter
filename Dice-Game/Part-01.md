[<- README](https://github.com/PriyathamVarma/Learn-Flutter/new/main/Dice-Game/README.md) | 
[Part 02: Classes, Custom Widgets ->](https://github.com/PriyathamVarma/Learn-Flutter/new/main/Dice-Game/Part-02.md)

**Starting from scratch**

- Clear all the code in main.dart file
  
- add 
```dart
runApp();
```

runApp() is the function that is used to render the UI.

- Now, in Dart, you can't have a standalone function like this. you need to wrap it up into a custom function

```dart

void main(){
  runApp();
}

```

Here main() is the function that executes the code inside it. void is the return type which means that it doesn't return any value but instead executes something. 

- import the necessary packages to run runApp().

```dart
import 'package:flutter/material.dart';
```

- Use the MaterialApp widget

```dart
runApp(MaterialApp());
```

 - Now, inside the MaterialApp() use the home as it renders the widget necessary.

```dart
runApp(MaterialApp(home:Text('Hello World')));
```
Here Text() is another widget which is the one that will be rendered

- Here is the final code

```dart
// This is the main dart file
// IMPORTS
import 'package:flutter/material.dart';

/* main() function executes 
the runApp() function 
which renders the widgets*/

void main() {
  runApp(MaterialApp(home: Text('Hello World')));
}
```

![Hello world screenshot](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Images/Simulator%20Screenshot%20-%20Dice%20Test%20-%202023-12-22%20at%2017.53.35.png)

**Improving code**

- Use const for better performance

```dart
runApp(const MaterialApp(home: Text('Hello World')));
```

- Now, use scaffold widget **Scaffold()** to give a good background for the app

```dart
 runApp(const MaterialApp(home: Scaffold(body: Text('Hello World'))));
```

This will give a better UI look and apperance

![Screenshot after scaffold widget](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Images/Screenshot%202023-12-22%20at%2018.13.30.png)

- Now, to make the text come to the center, use **layout** widgets.

[<- README](https://github.com/PriyathamVarma/Learn-Flutter/new/main/Dice-Game/README.md) | 
[Part 02: Classes, Custom Widgets ->](https://github.com/PriyathamVarma/Learn-Flutter/new/main/Dice-Game/Part-02.md)
