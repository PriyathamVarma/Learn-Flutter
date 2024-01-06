[<-- Part 03](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Expense-App/Part-03.md) | [README -->](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Expense-App/README.md)

# Themeing in Flutter

> main.dart

```dart
// This is the main dart file
// IMPORTS
import 'package:flutter/material.dart';
// Stateful
import 'package:expensez/components/stateful/expenses.dart';

void main() {
  runApp(
    MaterialApp(
      theme: ThemeData().copyWith(),
      home: const ExpenseWidget(),
    ),
  );
}
```

## Own theme

```dart
// This is the main dart file
// IMPORTS
import 'package:flutter/material.dart';
// Stateful
import 'package:expensez/components/stateful/expenses.dart';

void main() {
  runApp(
    MaterialApp(
      theme: ThemeData().copyWith(
        scaffoldBackgroundColor: const Color.fromARGB(255, 255, 94, 7),
        cardColor: Colors.amberAccent,
        
      ),
      home: const ExpenseWidget(),
    ),
  );
}
```

# Responsiveness and adaptiveness

## Locking device orientation

> main.dart

```dart
// This is the main dart file
// IMPORTS
import 'package:flutter/material.dart';
import 'package:flutter/services.dart';
// Stateful
import 'package:expensez/components/stateful/expenses.dart';

void main() {
  WidgetsFlutterBinding.ensureInitialized();
  SystemChrome.setPreferredOrientations([DeviceOrientation.portraitUp])
      .then((fn) {
    runApp(
      MaterialApp(
        theme: ThemeData.dark().copyWith(
          scaffoldBackgroundColor: const Color.fromARGB(255, 255, 94, 7),
          colorScheme: ColorScheme.fromSeed(seedColor: Colors.amberAccent),
          appBarTheme: const AppBarTheme().copyWith(
            backgroundColor: Colors.amberAccent,
            foregroundColor: Colors.amberAccent,
          ),
        ),
        home: const ExpenseWidget(),
      ),
    );
  });
}
```

- This will make the device screen locked in one position

## Updating the UI based on available space

> expense.dart

```dart
/* 
  This is for creating the main
  page that controls the entire
  state of the app
*/

// Imports
// Packages
import "package:expensez/components/stateful/new_epense.dart";
import "package:expensez/components/stateless/expenses_list.dart";
import "package:flutter/material.dart";
import "package:expensez/models/expense.dart";
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
  final List<Expense> _registeredExpenses = [
    Expense(
      title: "Food from butchers",
      amount: 29.00,
      date: DateTime.now(),
      category: Category.food,
    ),
    Expense(
      title: "Rice from spice baazar",
      amount: 14.00,
      date: DateTime.now(),
      category: Category.food,
    ),
  ];

  // Methods

  // Modal Box
  void _openModelBox() {
    showModalBottomSheet(
      context: context,
      builder: (ctx) {
        return NewExpense(_addExpense);
      },
    );
  }

  void _addExpense(Expense expense) {
    setState(() {
      _registeredExpenses.add(expense);
    });
  }

  void _removeExpense(Expense expense) {
    final indexOfExpense = _registeredExpenses.indexOf(expense);
    setState(() {
      _registeredExpenses.remove(expense);
    });
    // SnackBar
    ScaffoldMessenger.of(context).clearSnackBars();
    ScaffoldMessenger.of(context).showSnackBar(
      SnackBar(
        duration: const Duration(seconds: 3),
        content: const Text('Expense Deleted'),
        action: SnackBarAction(
            label: 'Undo',
            onPressed: () {
              setState(() {
                _registeredExpenses.insert(indexOfExpense, expense);
              });
            }),
      ),
    );
  }

  @override
  Widget build(context) {
    final width = MediaQuery.of(context).size.width;
    final height = MediaQuery.of(context).size.height;

    debugPrint('$width,$height');
    Widget mainContent = const Center(
      child: Text("No Expenses,add now"),
    );

    if (_registeredExpenses.isNotEmpty) {
      mainContent = ExpensesList(
        expenses: _registeredExpenses,
        removeExpense: _removeExpense,
      );
    }

    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          title: const Text("Expense Tracker"),
          actions: [
            IconButton(onPressed: _openModelBox, icon: const Icon(Icons.add))
          ],
        ),
        body: Container(
          decoration: const BoxDecoration(),
          child: width < 500
              ? Column(
                  mainAxisAlignment:
                      MainAxisAlignment.start, // Center children vertically
                  children: [
                    Center(child: mainContent),
                  ],
                )
              : Row(
                  mainAxisAlignment:
                      MainAxisAlignment.start, // Center children vertically
                  children: [
                    Center(child: mainContent),
                  ],
                ),
        ),
      ),
    );
  }
}


```




[<-- Part 03](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Expense-App/Part-03.md) | [README -->](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Expense-App/README.md)
