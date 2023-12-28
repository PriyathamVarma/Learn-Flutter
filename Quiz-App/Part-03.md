[<-- Part-02.md](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Quiz-App/Part-01.md) | [Part 04 -->](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Quiz-App/Part-04.md)


# Lists

## Mapping Lists and spread operator

Mapping lists in Flutter involves transforming each item in a list into a different type of widget or object—crucial for creating dynamic and data-driven UIs.

**Methods for Mapping Lists:**

> ListView.builder

Ideal for scrollable lists with many items.
Optimizes performance by building only visible items.

```Dart
ListView.builder(
    itemCount: items.length,
    itemBuilder: (context, index) {
      return Text(items[index]);
    },
)
```


> map Function

Suitable for non-scrollable scenarios where you need to transform a list into a different list of widgets.

```Dart
Column(
    children: items.map((item) => Text(item)).toList(),
)
```

> for Loop

While not strictly mapping, it allows manual iteration and widget creation for each item.

```Dart
Column(
    children: [
      for (var item in items) Text(item)
    ],
)
```
> [!IMPORTANT]
> Key Points:
> Choose the method based on list size and UI requirements.

- ListView.builder is preferred for long, scrollable lists.
- map is useful for transforming lists into different lists.
- for loops offer more control but less conciseness.

Always consider performance implications.

**Sample code**

> quiz_questions_screen.dart

```dart
/* This is the widget for questions
*/

// Imports
// Packages
//import "dart:math";

import "package:flutter/material.dart";

// Widgets
import 'package:quiz_app/stateless_widgets/button_widgets/elevated_button.dart';

// Data
import 'package:quiz_app/data/quiz_questions.dart';

// Widget
class QuestionsWidget extends StatefulWidget {
  const QuestionsWidget({super.key});

  @override
  State<QuestionsWidget> createState() {
    return _QuestionsWidgetState();
  }
}

// The return type of DiceRoll class

class _QuestionsWidgetState extends State<QuestionsWidget> {
  @override
  Widget build(context) {
    final currentQuestion = questions[0];

    return Column(
      mainAxisAlignment: MainAxisAlignment.center, // Center children vertically
      children: [
        Center(
          child: Text(
            currentQuestion.question,
            style: const TextStyle(fontSize: 24, color: Colors.white),
          ),
        ),
        ...currentQuestion.options.map(
          (item) {
            return ElevatedButtonWidget(
              answerText: item,
              answerFunction: () {
                debugPrint("Pressed q1");
              },
            );
          },
        ).toList(),
      ],
    );
  }
}
```
## Question Index 

```dart
/* This is the widget for questions
*/

// Imports
// Packages
//import "dart:math";

import "package:flutter/material.dart";

// Widgets
import 'package:quiz_app/stateless_widgets/button_widgets/elevated_button.dart';

// Data
import 'package:quiz_app/data/quiz_questions.dart';

// Widget
class QuestionsWidget extends StatefulWidget {
  const QuestionsWidget({super.key});

  @override
  State<QuestionsWidget> createState() {
    return _QuestionsWidgetState();
  }
}

// The return type of DiceRoll class

class _QuestionsWidgetState extends State<QuestionsWidget> {
  // Changing the question
  var currentQuestionIndex = 0;

  // Next question method
  void nextQuestion() {
    setState(() {
      if (currentQuestionIndex < questions.length - 1) {
        currentQuestionIndex += 1;
      }
    });

    debugPrint('$currentQuestionIndex');
  }

  @override
  Widget build(context) {
    final currentQuestion = questions[currentQuestionIndex];

    return Column(
      mainAxisAlignment: MainAxisAlignment.center, // Center children vertically
      children: [
        Center(
          child: Text(
            currentQuestion.question,
            style: const TextStyle(fontSize: 24, color: Colors.white),
          ),
        ),
        ...currentQuestion.options.map(
          (item) {
            return ElevatedButtonWidget(
              answerText: item,
              answerFunction: nextQuestion,
            );
          },
        ).toList(),
      ],
    );
  }
}
```

[<-- Part-02.md](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Quiz-App/Part-01.md) | [Part 04 -->](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Quiz-App/Part-04.md)
