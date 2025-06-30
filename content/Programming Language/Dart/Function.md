[[_Dart]]

## Anonymous Function

```dart
(parameterList){
// statements
}
```

that means it can be allocated to the variable also 

```dart
void main() {

var cube = (int number) {
    return number * number * number;
  };

  print("The cube of 2 is ${cube(2)}");
  print("The cube of 3 is ${cube(3)}");
}
```

if function have only one line represent line this 

```dart
void calculateInterest(String message) => print(message);
```

