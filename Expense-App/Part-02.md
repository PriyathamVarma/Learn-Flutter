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

[<-- Part 01](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Expense-App/Part-01.md) | [Part 03 -->](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Expense-App/Part-03.md)
