# Object Oriented Programming 

Functions -> Access -> Data

**Object-oriented programming (OOP)** is a programming paradigm that organizes code around objects, which are self-contained entities that contain data and code. OOP provides several benefits, including improved code organization, reusability, and maintainability.

## Key Concepts of OOP

### Encapsulation: 
Encapsulation is the bundling of data and code into a single unit, known as an object. This helps to protect data from unauthorized access and makes it easier to manage the state of an object.

### Abstraction: 
Abstraction is the process of hiding the implementation details of an object and exposing only the necessary functionality to the outside world. This makes it easier to use objects without having to understand their internal workings.

### Inheritance: 
Inheritance allows one class to inherit the properties and methods of another class. This makes it possible to create hierarchies of classes, which can reduce code duplication and promote code reuse.

### Polymorphism: 
Polymorphism allows objects of different classes to respond to the same method call in different ways. This makes it possible to create flexible and versatile code that can handle different types of objects in a consistent manner.

## Implementing OOP in Dart

Dart supports OOP principles through the use of classes, objects, constructors, and methods.

**Classes:** A class is a blueprint for creating objects. It defines the data and code that each object will have.

**Objects:** An object is an instance of a class. It represents a real-world entity and has its own unique state and behavior.

**Constructors:** A constructor is a special method that is used to initialize the state of an object when it is created.

**Methods:** Methods are functions that are defined within a class. They provide the behavior of an object.

## Example

``` dart

void main(){

  var person = new Person();

  person.firstName = "Varma is a hero";

  person.printName();

}

class Person{

String firstName="Default: First Name";

printName(){
  print(firstName);
}

}


```

## Benefits of OOP in Dart

### OOP provides several benefits for Dart developers, including:

**Improved Code Organization:** OOP helps to organize code into well-defined and reusable classes. This makes it easier to manage large codebases and to understand how different parts of the code work together.

**Reusable Code:** OOP promotes code reuse by allowing developers to create reusable classes and objects. This can save time and effort, and it can also make it easier to maintain code.

**Maintainable Code:** OOP makes it easier to maintain code by making it easier to understand and modify. This is because OOP code is typically more modular and less coupled than procedural code.

## Conclusion

OOP is a powerful and versatile programming paradigm that can be used to write maintainable, reusable, and efficient code in Dart. By understanding the key concepts of OOP and learning how to implement OOP principles in Dart, developers can create more robust and scalable applications.

## Constructor

```dart
void main(){

  var person = new Person("Varma");

  //person.firstName = "Varma is a hero";

  person.printName();

}

class Person{

String firstName="Default: First Name";

// Constructor
Person(name){
  firstName = name;
}

printName(){
  print(firstName);
}

}
```
