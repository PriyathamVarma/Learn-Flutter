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


