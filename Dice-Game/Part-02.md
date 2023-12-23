[<- Part 01: Basic Widgets](https://github.com/PriyathamVarma/Learn-Flutter/new/main/Dice-Game/Part-01.md) |
[Part 03: Variables, Functions ->](https://github.com/PriyathamVarma/Learn-Flutter/new/main/Dice-Game/Part-03.md)

## Container

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
## Custom Widgets

1. Creating Custom Widgets:

**Stateless Widgets:** Used for static UI elements that don't change based on user interaction or data. They are efficient for displaying information without any internal state.
**Example:** A simple Text widget.

**Stateful Widgets:** Used for UI elements that can dynamically change based on user input, data updates, or other events. They manage their internal state to update the UI accordingly.
**Example:** A counter widget with an increment button.

2. Key Concepts:

**Widget Tree:** Flutter apps are composed of a hierarchy of widgets, each representing a portion of the UI. Custom widgets can be combined to create complex layouts and visual elements.
**Building Methods:** Each widget has a build() method that returns its visual representation. Widgets can also have a createState() method if they manage state.
**Properties (Fields):** Define the visual and behavioral characteristics of a widget. They can be customized when using the widget in other parts of the app.

3. Best Practices:

**Reusability:** Create custom widgets for UI elements that are used repeatedly, promoting code organization and maintainability.
**Composition:** Break down complex UIs into smaller, reusable widgets for better readability and easier management.
**Naming Conventions:** Use meaningful names that reflect the widget's purpose for clarity.
**State Management:** Choose appropriate state management techniques (e.g., setState, Provider) depending on the complexity of the widget's state and its interactions with other parts of the app.

4. Benefits of Custom Widgets:

**Reusability:** Write code once and use it multiple times, reducing redundancy and improving consistency.
**Modularity:** Break down UI into smaller, manageable components, making code easier to understand and maintain.
**Flexibility:** Customize appearance and behavior to fit different use cases within your app.
**Abstraction:** Hide implementation details and provide a clear interface for using the widget, simplifying development.

5. Examples of Custom Widgets:

Custom buttons with specific styling and actions
Reusable form fields with validation
Complex UI components like cards, carousels, and navigation drawers
Widgets that encapsulate specific business logic or data interactions

**Actual Code**

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
        body: Container(
          decoration: BoxDecoration(
            color: const Color(0xff7c94b6),
            image: const DecorationImage(
              image: NetworkImage(
                  'https://flutter.github.io/assets-for-api-docs/assets/widgets/owl-2.jpg'),
              fit: BoxFit.cover,
            ),
            border: Border.all(
              width: 8,
            ),
            borderRadius: BorderRadius.circular(24),
          ),
          child: const Center(
            child: SizedBox(
              child: Text(
                'Hello World',
                style: TextStyle(fontSize: 24, color: Colors.black),
              ),
            ),
          ),
        ),
      ),
    ),
  );
}
```

Now, to remove the widget and make it customizable we need to use classes.

## Classes

Classes in Flutter are essential blueprints for creating reusable UI components and encapsulating data and behavior. Here's a comprehensive overview:

1. Types of Classes:

**Stateless Widgets:**
Represent fixed UI elements that don't change based on user interactions or data updates.
Used for static content like text, images, or simple layouts.
Don't maintain any state or internal data.

**Stateful Widgets:**
Represent dynamic UI elements that can change over time in response to user interactions, network data, or other events.
Maintain an internal state object to track changes and trigger UI updates.
Used for interactive elements like buttons, forms, or animations.

2. Key Concepts:

**Class Definition:**
Use the class keyword followed by the class name.
Enclose properties (fields) and methods within curly braces.
**Constructors:**
Special methods (usually named MyWidget()) to initialize objects of the class.
Used to set initial values for properties.
**Properties (Fields):**
Variables declared within the class to store data.
Can be accessed and modified using dot notation (e.g., widget.property).
**Methods:**
Functions defined within the class to perform actions.
Can be called on objects of the class using dot notation (e.g., widget.method()).

3. Inheritance:

Classes can inherit properties and methods from other classes (parent classes).
Use the extends keyword to create a subclass.
Useful for code reuse and organizing code hierarchically.

4. Widget Tree:

Flutter apps are built as a hierarchy of widgets.
Classes are used to create these widgets.
Widgets can be nested to create complex UI structures.

```dart
// Custom Widgets
class BoxContainer extends StatelessWidget {
  const BoxContainer({super.key});

  @override
  Widget build(context) {
    return "Widget code here"
  }
}
```

### Breakdown:

 ```dart
class BoxContainer extends StatelessWidget {:

```
Defines a new custom widget class named BoxContainer.
Extends the StatelessWidget class, indicating it represents a static UI element without internal state.

 ```dart
const BoxContainer({super.key});:
 ```
Constructor for creating instances of the BoxContainer widget.
Accepts an optional key parameter for identifying the widget within the widget tree.

 ```dart
@override:
 ```
Marks the following build method as overriding the inherited version from the parent class.

 ```dart
Widget build(BuildContext context) {:
 ```

Overriden method responsible for building the widget's visual representation.
Takes a BuildContext object providing information about the widget's location in the tree.
return "Widget code here";:

Placeholder for the actual widget code that will define the UI elements within the BoxContainer.
This line should be replaced with the specific widgets and layout you want to create.

## Key Points:

This code demonstrates the basic structure of a custom stateless widget in Flutter.
The build method is the heart of the widget, where you define its visual appearance.
Customize the widget's content and behavior within the build method to achieve the desired UI.

**Final code**

```dart
// This is the main dart file
// IMPORTS
import 'package:flutter/material.dart';

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

[<- Part 01: Basic Widgets](https://github.com/PriyathamVarma/Learn-Flutter/new/main/Dice-Game/Part-01.md) |
[Part 03: Variables, Functions ->](https://github.com/PriyathamVarma/Learn-Flutter/new/main/Dice-Game/Part-03.md)

