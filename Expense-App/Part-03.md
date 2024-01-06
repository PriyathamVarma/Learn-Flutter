[<-- Part 02](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Expense-App/Part-02.md) | [Part 04 -->](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Expense-App/Part-04.md)

## Using dismissable widgets

- Dismissable is the widget name that can be swiped off
  

> expenses_list.dart

<details>
  <summary>Full Code</summary>

```dart
/*
  This is for taking in the list
  and rendering them
*/

import 'package:expensez/components/stateless/expense_item.dart';
import 'package:expensez/models/expense.dart';
import 'package:flutter/material.dart';

class ExpensesList extends StatelessWidget {
  const ExpensesList({super.key, required this.expenses});

  final List<Expense> expenses;

  @override
  Widget build(BuildContext context) {
    return ListView.builder(
      shrinkWrap: true,
      itemCount: expenses.length,
      itemBuilder: (ctx, index) => Dismissible(
          key: ValueKey(expenses[index]), child: ExpenseItem(expenses[index])),
    );
  }
}

```  
</details>  

- The problem over here is that when swiped and again the data is added you get an error
- This is because there is a mismatch between the existing data and rendered data

> expenses.dart

<details>
  <summary>Full Code</summary>

This is the new addition

```dart
void _removeExpense(Expense expense) {
    setState(() {
      _registeredExpenses.remove(expense);
    });
  }
```

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
    setState(() {
      _registeredExpenses.remove(expense);
    });
  }

  @override
  Widget build(context) {
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
          child: Column(
            mainAxisAlignment:
                MainAxisAlignment.start, // Center children vertically
            children: [
              Center(
                  child: ExpensesList(
                expenses: _registeredExpenses,
                removeExpense: _removeExpense,
              )),
            ],
          ),
        ),
      ),
    );
  }
}

```

</details> 

> expenses_list.dart

<details>
  <summary>Full Code</summary>

```dart
/*
  This is for taking in the list
  and rendering them
*/

import 'package:expensez/components/stateless/expense_item.dart';
import 'package:expensez/models/expense.dart';
import 'package:flutter/material.dart';

class ExpensesList extends StatelessWidget {
  const ExpensesList(
      {super.key, required this.expenses, required this.removeExpense});

  final List<Expense> expenses;
  final void Function(Expense expense) removeExpense;

  @override
  Widget build(BuildContext context) {
    return ListView.builder(
      shrinkWrap: true,
      itemCount: expenses.length,
      itemBuilder: (ctx, index) => Dismissible(
        onDismissed: (direction) {
          removeExpense(expenses[index]);
        },
        key: ValueKey(expenses[index]),
        child: ExpenseItem(expenses[index]),
      ),
    );
  }
}

```  
</details>  

## Showing and managing Snackbars

> expenses.dart

<details>
  <summary>Full Code</summary>

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
          child: Column(
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
</details>  

> [!WARNING]
> Check the above code. Not working

[<-- Part 02](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Expense-App/Part-02.md) | [Part 04 -->](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Expense-App/Part-04.md)
