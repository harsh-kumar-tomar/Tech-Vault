 Serialization: The process of converting an object into a format that can be easily stored or transmitted (e.g., JSON, XML, binary).
 Deserialization: The process of converting the serialized format back into an object.
## lib
1. Kotlin Serialization: Kotlin’s native serialization library.

```
val user = User("John Doe", 30, "john.doe@example.com")  
  
// Serialize to JSON  
val jsonString = Json.encodeToString(user)  
println(jsonString) // {"name":"John Doe","age":30,"email":"john.doe@example.com"}  
  
// Deserialize from JSON  
val deserializedUser = Json.decodeFromString<User>(jsonString)  
println(deserializedUser) // User(name=John Doe, age=30, email=john.doe@example.com)  

```

2. Gson: A popular JSON serialization/deserialization library from Google.

```
val gson = Gson()  
val user = User("John Doe", 30, "john.doe@example.com")  
  
// Serialize to JSON  
val jsonString = gson.toJson(user)  
println(jsonString) // {"name":"John Doe","age":30,"email":"john.doe@example.com"}  
  
// Deserialize from JSON  
val deserializedUser = gson.fromJson(jsonString, User::class.java)  
println(deserializedUser) // User(name=John Doe, age=30, email=john.doe@example.com)  
```

3. Moshi: A modern JSON library for Android and Java from Square.
4. Jackson: A high-performance JSON processor for Java.
5. Protobuf: Protocol Buffers, a binary serialization format.