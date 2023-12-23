# Dice game using Flutter

This is to learn how to create a flutter project for a dice game.

## Analysing a new flutter project

To create a new Flutter project 

```bash
flutter create <name-of-the-app>
```

Here is the basic project

```markdown

<app>
  x
  |
  |--> .dart_tool
  x
  |
  |-> .idea
  x
  |
  |-> android
  x
  |
  |-> build
  x
  |
  |-> ios
  x
  |
  |-> lib
  x    x---> main.dart
  |
  |-> linux
  x  
  |
  |-> macos
  x  
  |
  |-> test
  x  
  |
  |-> web
  x  
  |
  |-> windows
  x  
  |
  |-> .gitignore
  x  
  |
  |-> .metadata
  x  
  |
  |-> analysis_options.yaml
  x  
  |
  |-> dice.iml
  x  
  |
  |-> pubspec.lock
  x  
  |
  |-> pubspec.yaml
  x  
  |
  |-> README.md
  x

```
![Project structure](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Images/Screenshot%202023-12-22%20at%2016.30.40.png)

**Pseudo Code for main.dart file**

This is just an starting template code, to show how the main file is structured. Not relevant for customised projects

```
BEGIN
  DECLARE app AS APPLICATION
  DECLARE homePage AS HOME_PAGE
  DECLARE counter AS INTEGER

  CREATE app
  SET app.title TO "Dice Game"
  SET app.theme.colorScheme TO Colors.deepPurple
  SET app.homePage TO homePage

  CREATE homePage
  SET homePage.title TO "Dice Game"
  SET homePage.counter TO 0

  FUNCTION incrementCounter(homePage)
    homePage.counter = homePage.counter + 1
    REBUILD homePage
  END FUNCTION

  BUILD homePage
    CREATE appBar
      SET appBar.title TO homePage.title
      SET appBar.backgroundColor TO app.theme.inversePrimary
    END CREATE

    CREATE body
      CREATE center
        CREATE column
          ADD text "You have pushed the button this many times:"
          ADD text homePage.counter
        END CREATE
      END CREATE

      CREATE floatingActionButton
        SET floatingActionButton.onPressed TO incrementCounter(homePage)
        SET floatingActionButton.icon TO "add"
      END CREATE
    END CREATE
  END BUILD

  RUN app
END
```
Here is the **actual code**

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        // This is the theme of your application.
        //
        // TRY THIS: Try running your application with "flutter run". You'll see
        // the application has a purple toolbar. Then, without quitting the app,
        // try changing the seedColor in the colorScheme below to Colors.green
        // and then invoke "hot reload" (save your changes or press the "hot
        // reload" button in a Flutter-supported IDE, or press "r" if you used
        // the command line to start the app).
        //
        // Notice that the counter didn't reset back to zero; the application
        // state is not lost during the reload. To reset the state, use hot
        // restart instead.
        //
        // This works for code too, not just values: Most code changes can be
        // tested with just a hot reload.
        colorScheme: ColorScheme.fromSeed(seedColor: Colors.deepPurple),
        useMaterial3: true,
      ),
      home: const MyHomePage(title: 'Dice Game'),
    );
  }
}

class MyHomePage extends StatefulWidget {
  const MyHomePage({super.key, required this.title});

  // This widget is the home page of your application. It is stateful, meaning
  // that it has a State object (defined below) that contains fields that affect
  // how it looks.

  // This class is the configuration for the state. It holds the values (in this
  // case the title) provided by the parent (in this case the App widget) and
  // used by the build method of the State. Fields in a Widget subclass are
  // always marked "final".

  final String title;

  @override
  State<MyHomePage> createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  int _counter = 0;

  void _incrementCounter() {
    setState(() {
      // This call to setState tells the Flutter framework that something has
      // changed in this State, which causes it to rerun the build method below
      // so that the display can reflect the updated values. If we changed
      // _counter without calling setState(), then the build method would not be
      // called again, and so nothing would appear to happen.
      _counter++;
    });
  }

  @override
  Widget build(BuildContext context) {
    // This method is rerun every time setState is called, for instance as done
    // by the _incrementCounter method above.
    //
    // The Flutter framework has been optimized to make rerunning build methods
    // fast, so that you can just rebuild anything that needs updating rather
    // than having to individually change instances of widgets.
    return Scaffold(
      appBar: AppBar(
        // TRY THIS: Try changing the color here to a specific color (to
        // Colors.amber, perhaps?) and trigger a hot reload to see the AppBar
        // change color while the other colors stay the same.
        backgroundColor: Theme.of(context).colorScheme.inversePrimary,
        // Here we take the value from the MyHomePage object that was created by
        // the App.build method, and use it to set our appbar title.
        title: Text(widget.title),
      ),
      body: Center(
        // Center is a layout widget. It takes a single child and positions it
        // in the middle of the parent.
        child: Column(
          // Column is also a layout widget. It takes a list of children and
          // arranges them vertically. By default, it sizes itself to fit its
          // children horizontally, and tries to be as tall as its parent.
          //
          // Column has various properties to control how it sizes itself and
          // how it positions its children. Here we use mainAxisAlignment to
          // center the children vertically; the main axis here is the vertical
          // axis because Columns are vertical (the cross axis would be
          // horizontal).
          //
          // TRY THIS: Invoke "debug painting" (choose the "Toggle Debug Paint"
          // action in the IDE, or press "p" in the console), to see the
          // wireframe for each widget.
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            const Text(
              'You have pushed the button t many times: why?',
            ),
            Text(
              '$_counter',
              style: Theme.of(context).textTheme.headlineMedium,
            ),
          ],
        ),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: _incrementCounter,
        tooltip: 'Increment',
        child: const Icon(Icons.add),
      ), // This trailing comma makes auto-formatting nicer for build methods.
    );
  }
}
```
<hr/>

## Table of contents

| S.No | Link | Remarks |
|- | - | -|
| 1 | [Part 01](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Dice-Game/Part-01.md) | Basic widgets and heirarchy |
| 2 | [Part 02](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Dice-Game/Part-02.md) | Classes and custom widgets |
| 3 | [Part 03](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Dice-Game/Part-03.md) | Variables and functions |




## Resources

1. [Flutter widgets catalog](https://docs.flutter.dev/ui/widgets?gclid=CjwKCAiAhJWsBhAaEiwAmrNyq9wg8Yswi5UbO881KhwKgSkQgmVh_2d1zioUV8Kvq4tTB2P6fe_txxoCfq4QAvD_BwE&gclsrc=aw.ds)
