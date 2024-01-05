# Expense Tracker

This is for creating expense tracker app

```mermaid

graph TD

A[lib] --> B[components]
A --> E[main.dart]
B --> C[stateful]
B --> D[stateless]
C --> F[expenses.dart]
A --> G[Models]
A --> H[Views]

```

> main.dart

<details>
  <summary>Code</summary>

```dart
// This is the main dart file
// IMPORTS
import 'package:flutter/material.dart';
// Stateful
import 'package:expensez/components/stateful/expenses.dart';

void main() {
  runApp(
    const ExpenseWidget(),
  );
}

```  
</details>

> expenses.dart

<details>
  <summary>Code</summary>

```dart
/* 
  This is for creating the main
  page that controls the entire
  state of the app
*/

// Imports
// Packages
import "package:flutter/material.dart";
// Stateless

// Stateful

// Widget
class ExpenseWidget extends StatefulWidget {
  const ExpenseWidget({super.key});

  @override
  State<ExpenseWidget> createState() {
    return _ExpenseWidgetState();
  }
}

// The return type of DiceRoll class

class _ExpenseWidgetState extends State<ExpenseWidget> {
  @override
  Widget build(context) {
    return MaterialApp(
      home: Scaffold(
        body: Container(
          decoration: const BoxDecoration(
            gradient: LinearGradient(
              begin: Alignment.topLeft,
              end: Alignment(0.8, 1),
              colors: <Color>[
                Color(0xff1f005c),
                Color(0xff5b0060),
                Color(0xff870160),
                Color(0xffac255e),
                Color(0xffca485c),
                Color(0xffe16b5c),
                Color(0xfff39060),
                Color(0xffffb56b),
              ], // Gradient from https://learnui.design/tools/gradient-generator.html
              tileMode: TileMode.mirror,
            ),
          ),
          child: const Column(
            mainAxisAlignment:
                MainAxisAlignment.center, // Center children vertically
            children: [
              Center(
                child: Text(
                  'Expensez App',
                  style: TextStyle(fontSize: 24, color: Colors.white),
                ),
              ),
            ],
          ),
        ),
      ),
    );
  }
}

```  
</details>


```mermaid

graph TD


A[lib] --> B[components]
A --> E[main.dart]
B --> C[stateful]
B --> D[stateless]
C --> F[expenses.dart]
A --> G[Models]
A --> H[Views]
G --> I[expense.dart]

```

> models/expense.dart
>> flutter pub add uuid

<details>
  <summary>Code</summary>

```dart

/*
  This model is for expenses
*/

// Imports
import 'package:uuid/uuid.dart';

const uuid = Uuid();

class Expense {
  // Constructor
  Expense({required this.title, required this.amount, required this.date})
      : id = uuid.v4();

  final String id;
  final String title;
  final double amount;
  final DateTime date;
}


```  
</details>



## Resources

1. [UUID package](https://pub.dev/packages/uuid)

