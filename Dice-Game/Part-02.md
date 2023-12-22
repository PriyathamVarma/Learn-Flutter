**Container**

Containers are similar to components which are useful in layout settings

```dart
// This is the main dart file
// IMPORTS
import 'package:flutter/material.dart';

/* main() function executes 
the runApp() function 
which renders the widgets*/

void main() {
  runApp(
    MaterialApp(
      home: Scaffold(
        body:  Container(
          child: const Center(
            child: SizedBox(
              child: Text('Hello Worldss'),
            ),
          ),
        ),
      ),
    ),
  );
}
```
