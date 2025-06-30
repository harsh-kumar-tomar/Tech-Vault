```dart

Navigator.push(context,route)

// it pushes the new widget on the top of the existing widget
Navigator.push(context,MaterialPageRoute(builder))

// it replaces the widget
Navigator.pushReplacement(context,MaterialPageRoute(builder))

// it pops the existing screen
Navigator.pop(context)


// to pass data use contructor and widget.property
```

**Route** 
how new screen will appear like transitoin and what screen to show 

**Navigator** 
keep history of pages user have navigated 