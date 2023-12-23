[<- Part 02: Classes, Custom Widgets](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Dice-Game/Part-01.md) |
[Part 04: Variables, Functions ->](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Dice-Game/Part-03.md)

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
/* This widget is a simple widget
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


<hr/>

[<- Part 02: Classes, Custom Widgets](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Dice-Game/Part-01.md) |
[Part 04: Variables, Functions ->](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Dice-Game/Part-03.md)
