[<-- Part 01](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Expense-App/Part-01.md) | [Part 03 -->](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Expense-App/Part-03.md)

## Close button

```dart
 ElevatedButton(
                  onPressed: () {
                    Navigator.pop(context);
                  },
                  child: const Text('Close'),
                ),
```

- The context is from the build context in the widget

```dart
@override
  Widget build(BuildContext context) { <---- THIS ONE
    return Scaffold(
//.........
```

## Date picker

<details>
  <summary>Full Code</summary>

```dart
import 'package:flutter/material.dart';
import 'package:intl/intl.dart';

class NewExpense extends StatefulWidget {
  const NewExpense({super.key});

  @override
  State<NewExpense> createState() => _NewExpenseState();
}

class _NewExpenseState extends State<NewExpense> {
  final _titleController = TextEditingController();
  final _priceController = TextEditingController();
  DateTime? _selectedDate;

  @override
  void dispose() {
    _titleController.dispose();
    _priceController.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: Column(
          children: [
            TextField(
              controller: _titleController,
              decoration: const InputDecoration(
                labelText: 'Title',
              ),
            ),
            const SizedBox(height: 16.0),
            Row(
              children: [
                Expanded(
                  child: TextField(
                    controller: _priceController,
                    keyboardType: TextInputType.number,
                    decoration: const InputDecoration(
                      prefixText: '£ ',
                      labelText: 'Price',
                    ),
                  ),
                ),
                const SizedBox(width: 16.0),
                Expanded(
                  child: ElevatedButton(
                    onPressed: () async {
                      // Use showDatePicker to get the selected date
                      _selectedDate = await showDatePicker(
                        context: context,
                        initialDate: DateTime.now(),
                        firstDate: DateTime(2023), // Set a minimum date
                        lastDate: DateTime.now(),
                      );
                      if (_selectedDate != null) {
                        setState(
                            () {}); // Refresh widget to display selected date
                      }
                    },
                    child: Text(_selectedDate == null
                        ? 'Choose Date'
                        : DateFormat('yyyy-MM-dd').format(_selectedDate!)),
                  ),
                ),
              ],
            ),
            const SizedBox(height: 16.0),
            Row(
              children: [
                ElevatedButton(
                  onPressed: () {
                    Navigator.pop(context);
                  },
                  child: const Text('Close'),
                ),
                ElevatedButton(
                  onPressed: () {
                    // Access entered title and price from controllers
                    final title = _titleController.text;
                    final price = double.parse(_priceController.text);
                    final date = _selectedDate;
                    debugPrint('$title, $price,$date');

                    // Handle expense creation logic here (e.g., add to list)
                  },
                  child: const Text('Add Expense'),
                ),
              ],
            ),
          ],
        ),
      ),
    );
  }
}

```  
</details>

## Dropdown

<details>
 <summary>Full Code</summary>

```dart
import 'package:expensez/models/expense.dart';
import 'package:flutter/material.dart';
import 'package:intl/intl.dart';

class NewExpense extends StatefulWidget {
  const NewExpense({super.key});

  @override
  State<NewExpense> createState() => _NewExpenseState();
}

class _NewExpenseState extends State<NewExpense> {
  final _titleController = TextEditingController();
  final _priceController = TextEditingController();
  DateTime? _selectedDate;
  Category _selectedCategory = Category.food;

  @override
  void dispose() {
    _titleController.dispose();
    _priceController.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: Column(
          children: [
            TextField(
              controller: _titleController,
              decoration: const InputDecoration(
                labelText: 'Title',
              ),
            ),
            const SizedBox(height: 16.0),
            Row(
              children: [
                Expanded(
                  child: TextField(
                    controller: _priceController,
                    keyboardType: TextInputType.number,
                    decoration: const InputDecoration(
                      prefixText: '£ ',
                      labelText: 'Price',
                    ),
                  ),
                ),
                const SizedBox(width: 16.0),
                Expanded(
                  child: ElevatedButton(
                    onPressed: () async {
                      // Use showDatePicker to get the selected date
                      _selectedDate = await showDatePicker(
                        context: context,
                        initialDate: DateTime.now(),
                        firstDate: DateTime(2023), // Set a minimum date
                        lastDate: DateTime.now(),
                      );
                      if (_selectedDate != null) {
                        setState(
                            () {}); // Refresh widget to display selected date
                      }
                    },
                    child: Text(_selectedDate == null
                        ? 'Choose Date'
                        : DateFormat('yyyy-MM-dd').format(_selectedDate!)),
                  ),
                ),
              ],
            ),
            const SizedBox(height: 16.0),
            Row(
              children: [
                DropdownButton(
                    value: _selectedCategory,
                    items: Category.values
                        .map(
                          (item) => DropdownMenuItem(
                            value: item,
                            child: Text(
                              item.name.toString(),
                            ),
                          ),
                        )
                        .toList(),
                    onChanged: (value) {
                      setState(() {
                        _selectedCategory = value!;
                      });
                    }),
                ElevatedButton(
                  onPressed: () {
                    Navigator.pop(context);
                  },
                  child: const Text('Close'),
                ),
                ElevatedButton(
                  onPressed: () {
                    // Access entered title and price from controllers
                    final title = _titleController.text;
                    final price = double.parse(_priceController.text);
                    final date = _selectedDate;
                    debugPrint('$title, $price,$date');

                    // Handle expense creation logic here (e.g., add to list)
                  },
                  child: const Text('Add Expense'),
                ),
              ],
            ),
          ],
        ),
      ),
    );
  }
}

```
 
</details>


## Adding Expenses

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
              Center(child: ExpensesList(expenses: _registeredExpenses)),
            ],
          ),
        ),
      ),
    );
  }
}

``` 
</details>

> new_expense.dart

<details>
 <summary>Full Code</summary>

```dart
import 'package:expensez/models/expense.dart';
import 'package:flutter/material.dart';
import 'package:intl/intl.dart';

class NewExpense extends StatefulWidget {
  const NewExpense(this.newExpense, {super.key});

  final void Function(Expense expense) newExpense;

  @override
  State<NewExpense> createState() => _NewExpenseState();
}

class _NewExpenseState extends State<NewExpense> {
  final _titleController = TextEditingController();
  final _priceController = TextEditingController();
  DateTime? _selectedDate;
  Category _selectedCategory = Category.food;

  @override
  void dispose() {
    _titleController.dispose();
    _priceController.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: Column(
          children: [
            TextField(
              controller: _titleController,
              decoration: const InputDecoration(
                labelText: 'Title',
              ),
            ),
            const SizedBox(height: 16.0),
            Row(
              children: [
                Expanded(
                  child: TextField(
                    controller: _priceController,
                    keyboardType: TextInputType.number,
                    decoration: const InputDecoration(
                      prefixText: '£ ',
                      labelText: 'Price',
                    ),
                  ),
                ),
                const SizedBox(width: 16.0),
                Expanded(
                  child: ElevatedButton(
                    onPressed: () async {
                      // Use showDatePicker to get the selected date
                      _selectedDate = await showDatePicker(
                        context: context,
                        initialDate: DateTime.now(),
                        firstDate: DateTime(2023), // Set a minimum date
                        lastDate: DateTime.now(),
                      );
                      if (_selectedDate != null) {
                        setState(
                            () {}); // Refresh widget to display selected date
                      }
                    },
                    child: Text(_selectedDate == null
                        ? 'Choose Date'
                        : DateFormat('yyyy-MM-dd').format(_selectedDate!)),
                  ),
                ),
              ],
            ),
            const SizedBox(height: 16.0),
            Row(
              children: [
                DropdownButton(
                    value: _selectedCategory,
                    items: Category.values
                        .map(
                          (item) => DropdownMenuItem(
                            value: item,
                            child: Text(
                              item.name.toString(),
                            ),
                          ),
                        )
                        .toList(),
                    onChanged: (value) {
                      setState(() {
                        _selectedCategory = value!;
                      });
                    }),
                const Spacer(),
                ElevatedButton(
                  onPressed: () {
                    Navigator.pop(context);
                  },
                  child: const Text('Close'),
                ),
                ElevatedButton(
                  onPressed: () {
                    // Access entered title and price from controllers
                    final title = _titleController.text;
                    final price = double.parse(_priceController.text);
                    final date = _selectedDate;
                    final category = _selectedCategory;
                    debugPrint('$title, $price,$date,$category');
                    widget.newExpense(
                      Expense(
                          title: title,
                          amount: price,
                          date: date!,
                          category: category),
                    );
                    debugPrint('New Expense Added');
                    // Handle expense creation logic here (e.g., add to list)
                  },
                  child: const Text('Add Expense'),
                ),
              ],
            ),
          ],
        ),
      ),
    );
  }
}

``` 
</details>

![Final main screen](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Images/Screenshot%202024-01-06%20at%2002.16.53.png)
![Final dropdown](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Images/Screenshot%202024-01-06%20at%2002.17.04.png)

[<-- Part 01](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Expense-App/Part-01.md) | [Part 03 -->](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Expense-App/Part-03.md)
