[<-- Part-01.md](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Shopping-App/Part-01.md) | [Part 03 -->](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Shopping-App/Part-03.md)

## Validation logic for forms

```mermaid



graph TD

A[lib] --> B[src]
B --> C[ui]
C --> D[screens]
C --> E[common]
C --> F[widgets]
B --> G[models]
B --> H[providers]
B --> I[Data]
I --> J[groceries_data.dart]
G --> K[groceries_model.dart]
H --> L[groceries_provider.dart]
E --> M[appbar_widget.dart]
D --> N[groceries_screen.dart]
E --> O[SideDrawerWidget.dart]

```

> new_item_screen.dart


```dart

 TextFormField(
                  maxLength: 50,
                  decoration: const InputDecoration(
                    label: Text('Enter Qty'),
                  ),
                  validator: (value) {
                    if (value == null || value.isEmpty) {
                      return "No Value entered";
                    }
                    return null;
                  },
                  
                ),

```

## Getting form access via a Global Key

> new_item_screen.dart


```dart

/*
  This is for new item
  adding screen
*/

import 'package:flutter/material.dart';
import 'package:flutter_riverpod/flutter_riverpod.dart';
import 'package:shopping_app/src/data/groceries_data.dart';
// import 'package:shopping_app/src/data/groceries_data.dart';
// import 'package:shopping_app/src/providers/groceries_provider.dart';
import 'package:shopping_app/src/ui/common/appbar_widget.dart';
import 'package:shopping_app/src/ui/common/side_drawer_widget.dart';

class NewItemScreen extends ConsumerStatefulWidget {
  const NewItemScreen({super.key});

  @override
  ConsumerState<NewItemScreen> createState() {
    return _NewItemScreenState();
  }
}

// The return type of DiceRoll class

class _NewItemScreenState extends ConsumerState<NewItemScreen> {
  final _formKey = GlobalKey<FormState>();

  void _saveItem() {
    _formKey.currentState!.validate();
  }

  @override
  Widget build(context) {
    return MaterialApp(
      home: Scaffold(
        appBar: const AppBarWidget(title: "New Item"),
        body: Padding(
          padding: const EdgeInsets.all(12),
          child: Form(
            key: _formKey,
            child: Column(
              children: [
                TextFormField(
                  maxLength: 50,
                  decoration: const InputDecoration(
                    label: Text('Enter Grocery'),
                  ),
                  validator: (value) {
                    if (value == null || value.isEmpty) {
                      return "No Value entered";
                    }
                    return null;
                  },
                ),
                TextFormField(
                  maxLength: 50,
                  decoration: const InputDecoration(
                    label: Text('Enter Qty'),
                  ),
                  validator: (value) {
                    if (value == null || value.isEmpty) {
                      return "No Value entered";
                    }
                    return null;
                  },
                ),
                DropdownButtonFormField(
                  items: [
                    for (final color in availableColors)
                      DropdownMenuItem(
                        value: color,
                        child: Container(
                          width: 100,
                          height: 50,
                          color: color,
                        ),
                      ),
                  ],
                  onChanged: (value) {},
                ),
                Row(
                  children: [
                    ElevatedButton(
                      onPressed: _saveItem,
                      style: ElevatedButton.styleFrom(
                        backgroundColor: Colors.black,
                        foregroundColor: Colors.white,
                        shape: RoundedRectangleBorder(
                            borderRadius: BorderRadius.circular(5)),
                      ),
                      child: const Text('Submit'),
                    ),
                    const SizedBox(width: 20),
                    ElevatedButton(
                      onPressed: () {
                        _formKey.currentState!.reset();
                      },
                      style: ElevatedButton.styleFrom(
                        backgroundColor: Colors.black,
                        foregroundColor: Colors.white,
                        shape: RoundedRectangleBorder(
                            borderRadius: BorderRadius.circular(5)),
                      ),
                      child: const Text('Reset'),
                    ),
                  ],
                )
              ],
            ),
          ),
        ),
        drawer: const SideDrawerWidget(),
      ),
    );
  }
}


```

## Extracting entered values

```dart

/*
  This is for new item
  adding screen
*/

import 'package:flutter/material.dart';
import 'package:flutter_riverpod/flutter_riverpod.dart';
import 'package:shopping_app/src/data/groceries_data.dart';
// import 'package:shopping_app/src/data/groceries_data.dart';
// import 'package:shopping_app/src/providers/groceries_provider.dart';
import 'package:shopping_app/src/ui/common/appbar_widget.dart';
import 'package:shopping_app/src/ui/common/side_drawer_widget.dart';

class NewItemScreen extends ConsumerStatefulWidget {
  const NewItemScreen({super.key});

  @override
  ConsumerState<NewItemScreen> createState() {
    return _NewItemScreenState();
  }
}

// The return type of DiceRoll class

class _NewItemScreenState extends ConsumerState<NewItemScreen> {
  final _formKey = GlobalKey<FormState>();

  var _enteredGroceryItem = " ";
  var _enteredQty = "";
  var _enteredColor = Colors.white;

  void _saveItem() {
    _formKey.currentState!.validate();
    _formKey.currentState!.save();
    debugPrint('$_enteredGroceryItem,$_enteredQty, $_enteredColor');
  }

  @override
  Widget build(context) {
    return MaterialApp(
      home: Scaffold(
        appBar: const AppBarWidget(title: "New Item"),
        body: Padding(
          padding: const EdgeInsets.all(12),
          child: Form(
            key: _formKey,
            child: Column(
              children: [
                TextFormField(
                  maxLength: 50,
                  decoration: const InputDecoration(
                    label: Text('Enter Grocery'),
                  ),
                  validator: (value) {
                    if (value == null || value.isEmpty) {
                      return "No Value entered";
                    }
                    return null;
                  },
                  onSaved: (value) {
                    _enteredGroceryItem = value!;
                  },
                ),
                TextFormField(
                  maxLength: 50,
                  decoration: const InputDecoration(
                    label: Text('Enter Qty'),
                  ),
                  validator: (value) {
                    if (value == null || value.isEmpty) {
                      return "No Value entered";
                    }
                    return null;
                  },
                  onSaved: (value) {
                    _enteredQty = value!;
                  },
                ),
                DropdownButtonFormField(
                  items: [
                    for (final color in availableColors)
                      DropdownMenuItem(
                        value: color,
                        child: Container(
                          width: 100,
                          height: 50,
                          color: color,
                        ),
                      ),
                  ],
                  onChanged: (value) {
                    _enteredColor = value!;
                  },
                ),
                Row(
                  children: [
                    ElevatedButton(
                      onPressed: _saveItem,
                      style: ElevatedButton.styleFrom(
                        backgroundColor: Colors.black,
                        foregroundColor: Colors.white,
                        shape: RoundedRectangleBorder(
                            borderRadius: BorderRadius.circular(5)),
                      ),
                      child: const Text('Submit'),
                    ),
                    const SizedBox(width: 20),
                    ElevatedButton(
                      onPressed: () {
                        _formKey.currentState!.reset();
                      },
                      style: ElevatedButton.styleFrom(
                        backgroundColor: Colors.black,
                        foregroundColor: Colors.white,
                        shape: RoundedRectangleBorder(
                            borderRadius: BorderRadius.circular(5)),
                      ),
                      child: const Text('Reset'),
                    ),
                  ],
                )
              ],
            ),
          ),
        ),
        drawer: const SideDrawerWidget(),
      ),
    );
  }
}

```

## Passing data between screens

> new_item_screen.dart

```dart

/*
  This is for new item
  adding screen
*/

import 'package:flutter/material.dart';
import 'package:flutter_riverpod/flutter_riverpod.dart';
import 'package:shopping_app/src/data/groceries_data.dart';
import 'package:shopping_app/src/models/groceries_model.dart';
import 'package:shopping_app/src/ui/common/appbar_widget.dart';
import 'package:shopping_app/src/ui/common/side_drawer_widget.dart';

class NewItemScreen extends ConsumerStatefulWidget {
  const NewItemScreen({super.key});

  @override
  ConsumerState<NewItemScreen> createState() {
    return _NewItemScreenState();
  }
}

// The return type of DiceRoll class

class _NewItemScreenState extends ConsumerState<NewItemScreen> {
  final _formKey = GlobalKey<FormState>();

  var _enteredGroceryItem = " ";
  var _enteredQty = "";
  var _enteredColor = Colors.white;

  void _saveItem() {
    _formKey.currentState!.validate();
    _formKey.currentState!.save();
    debugPrint('$_enteredGroceryItem,$_enteredQty, $_enteredColor');
    Navigator.of(context).pop(
      Grocery(
          grocery: _enteredGroceryItem,
          color: _enteredColor,
          quantity: _enteredQty),
    );
  }

  @override
  Widget build(context) {
    return MaterialApp(
      home: Scaffold(
        appBar: const AppBarWidget(title: "New Item"),
        body: Padding(
          padding: const EdgeInsets.all(12),
          child: Form(
            key: _formKey,
            child: Column(
              children: [
                TextFormField(
                  maxLength: 50,
                  decoration: const InputDecoration(
                    label: Text('Enter Grocery'),
                  ),
                  validator: (value) {
                    if (value == null || value.isEmpty) {
                      return "No Value entered";
                    }
                    return null;
                  },
                  onSaved: (value) {
                    _enteredGroceryItem = value!;
                  },
                ),
                TextFormField(
                  maxLength: 50,
                  decoration: const InputDecoration(
                    label: Text('Enter Qty'),
                  ),
                  validator: (value) {
                    if (value == null || value.isEmpty) {
                      return "No Value entered";
                    }
                    return null;
                  },
                  onSaved: (value) {
                    _enteredQty = value!;
                  },
                ),
                DropdownButtonFormField(
                  items: [
                    for (final color in availableColors)
                      DropdownMenuItem(
                        value: color,
                        child: Container(
                          width: 100,
                          height: 50,
                          color: color,
                        ),
                      ),
                  ],
                  onChanged: (value) {
                    _enteredColor = value!;
                  },
                ),
                Row(
                  children: [
                    ElevatedButton(
                      onPressed: _saveItem,
                      style: ElevatedButton.styleFrom(
                        backgroundColor: Colors.black,
                        foregroundColor: Colors.white,
                        shape: RoundedRectangleBorder(
                            borderRadius: BorderRadius.circular(5)),
                      ),
                      child: const Text('Submit'),
                    ),
                    const SizedBox(width: 20),
                    ElevatedButton(
                      onPressed: () {
                        _formKey.currentState!.reset();
                      },
                      style: ElevatedButton.styleFrom(
                        backgroundColor: Colors.black,
                        foregroundColor: Colors.white,
                        shape: RoundedRectangleBorder(
                            borderRadius: BorderRadius.circular(5)),
                      ),
                      child: const Text('Reset'),
                    ),
                  ],
                )
              ],
            ),
          ),
        ),
        drawer: const SideDrawerWidget(),
      ),
    );
  }
}


```


[<-- Part-01.md](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Shopping-App/Part-01.md) | [Part 03 -->](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Shopping-App/Part-03.md)


