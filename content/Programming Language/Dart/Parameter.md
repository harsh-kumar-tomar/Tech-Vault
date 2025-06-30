### How Parameters work in [[Function]] ?


we must pass parameter in same order .
## 1. Positional Argument

```dart
void printInfo(String name, String gender) {
  print("Hello $name your gender is $gender.");
}
```

## 2. Default Value to Positional Argument 

Uses square braces to give default value

```dart
void printInfo(String name, String gender, [String title = "sir/ma'am"]) {
  print("Hello $title $name your gender is $gender.");
}
```

## 3.  Optional Argument

similar to the the above one.

```dart
void printInfo(String name, String gender, [String? title]) {
  print("Hello $title $name your gender is $gender.");
}
```
## 4. Named Argument 

Uses Curly braces to differentiate . It does not give default value 

```dart
void printInfo({String? name, String? gender}) {
  print("Hello $name your gender is $gender.");
}
```

## 5. Required Named Argument 

uses Required keyword

```dart
void printInfo({required String name, required String gender}) {
  print("Hello $name your gender is $gender.");
}
```