Abstract [[Class]]

```dart
abstract class ClassName {
  //Body of abstract class

  method1();
  method2();
}
```

we can define constructor in abstract class

```dart
abstract class Bank {
  String name;
  double rate;

  // Constructor
  Bank(this.name, this.rate);

  // Abstract method
  void interest();

  //Non-Abstract method: It have an implementation
  void display() {
    print('Bank Name: $name');
  }
}
```



