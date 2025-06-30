
every [[Class]] and [[Abstract]] class is interface by default 

so once we use implements we must override all methods of that class . we usually use abstract class , instead of concrete class to declare interface

```dart
class InterfaceName {
  // code
}

class ClassName implements InterfaceName {
  // code
}

class ClassName implements Interface1, Interface2, Interface3 {
  // code
}
```


we define int