![[Pasted image 20241111132342.png]]
# shared preference a way to store our lovely data

SharedPreferences specifically points an XML file in the user’s phone that hold keys and values and provides functions to read and write. You can have multiple SharedPreferences file and in such case, each is managed separately. You can choose to make them private or shared of course.

```
val sharedPreferences =  
activity.getSharedPreferences("file_name", Context.MODE_PRIVATE)
```

technique com.applenotes.MY_SHARED_PREFERENCES

To write, we basically create a SharedPreferences.Editor by just calling “edit()” on our SharedPreferences object.

## Write

```
val editor = sharedPref.edit()  
val newHighScore = 1000  
editor.putInt(getString(R.string.high_score_key), newHighScore)  
editor.apply()
```

## Read

```
val sharedPref = getSharedPreferences("MY_GAME_PREFS", Context.MODE_PRIVATE)  
  
val highScore = sharedPref.getInt(getString(R.string.high_score_key), 0)  
  
if (highScore > 0) {  
println("Your high score is $highScore!")  
} else {  
println("You haven't played yet.")  
}
```

## Problems

1. SharedPreferences editing functions are synchronous and can potentially block the UI.
2. SharedPreferences requires manual and error-prone migration processes.
3. SharedPreferences only supports primitive data types, requiring manual conversion for complex objects.

*Don’t be fooled by their joint use of “_Preferences_” in naming — these have nothing in common and come from two completely separate APIs.
# DataStore

```
val Context.dataStore by preferencesDataStore(name = "user_preferences")
```

## Keys

```
val USER_NAME = stringPreferencesKey("user_name") 
val USER_AGE = intPreferencesKey("user_age")
```
## Write

```
context.dataStore.edit { preferences -> 
preferences[USER_NAME] = userName 
preferences[USER_AGE] = userAge 
}
```

## READ

```
fun getUserPreferences(context: Context): Flow<UserPreferences> {

return context.dataStore.data.map { preferences -> 
val userName = preferences[USER_NAME] ?: "" 
val userAge = preferences[USER_AGE] ?: 0 
}
}
```