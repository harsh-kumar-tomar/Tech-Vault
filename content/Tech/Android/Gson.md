[[Kotlin]]

Google Gson is a Java library that can be used to convert Java Objects into their JSON representation. It can also be used to convert a JSON string to an equivalent Java object.


## How to use ?
1. create gson object using gson builder . It is a reusable object.

```
GsonBuilder builder = new GsonBuilder(); 
builder.setPrettyPrinting(); 
Gson gson = builder.create();
```

2. Use fromJson() method to get the Object from the JSON. Pass Json string / source of Json string and object type as parameter.

```
Student student = gson.fromJson(jsonString, Student.class);
```

3. Use toJson() method to get the JSON string representation of an object.

```
jsonString = gson.toJson(student);
```

