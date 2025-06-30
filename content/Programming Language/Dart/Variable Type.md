[[_Dart]]

String 
int
double
num : to store both int and double
bool
var : to store any value



``` dart
const pi = 3.14;
```
## Error

```dart
var myVariable = 50; // we can also use int instead of var
myVariable = "Hello"; // this will give error
print(myVariable);
```

## Dynamic Type

```dart
dynamic myVariable = 50;
myVariable = "Hello";
print(myVariable);
```


## Enum

```dart
enum Weather{ sunny, snowy, cloudy, rainy}
```

## Final and Const

Final is a runtime constant and Const is a compile time constant . 
final variables are only assigned once at runtime.
In both the cases once the value is assigned , it can't be changed.

final can be used inside the class variables as values are going to get in the runtime , 
while const can't be used 

``` dart
class Car {
  final String brand; // Allowed
  Car(this.brand);
}
```

```dart
class Car {
  const String brand; // ❌ error 'const' variables must be static
  Car(this.brand);
}
```

```dart
class MathConstants {
  static const double pi = 3.14159; // ✅ Allowed
}
void main() {
  print(MathConstants.pi); // 3.14159
}
```