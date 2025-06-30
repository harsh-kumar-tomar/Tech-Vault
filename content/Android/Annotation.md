[[Programming]] 

Annotation ek special type ka "metadata" hota hai jo hum apne code ke upar lagate hain to provide **extra information**

## Annotation Processing

Annotation processing ka kaam hota hai annotations ko process karna aur unse related code generate karna ya validation karna. 
Ye process Android aur Java applications me code ko simplify aur automate karne ke liye kaam aata hai.


#### **Annotation Processing Ke Steps:**

1. **Annotations Lagana:** Aap apni class ya methods par annotations lagate ho.
  
```
    @MyCustomAnnotation("This is a test")
    public void testMethod() 
    {     // Some logic } 
```

2. **Annotation Processor Banana:** Aap ek annotation processor likhte ho jo annotations ko read kare aur unse kuch kaam kare (jaise code generate karna).

3. **Generated Code:** Processor aapka code padhta hai aur usse related code generate karta hai.


Annotation processing se aapko boilerplate code likhne ki zarurat nahi padti. Ye Android ke libraries aur frameworks me bahut zyada use hota hai.

### **Annotation Processor Kaise Kaam Karta Hai?**

1. **Compile Time Par Run Hota Hai**: Annotation processor source code ko padhta hai aur uske basis par code generate karta hai.
    
2. **Code Generation**: Processor ne jo code generate kiya hai, wo app ke final build me include hota hai.
    
3. **Tool: JavaPoet**: Ye ek popular library hai jo code generation ke liye use hoti hai.

### **Why Are Annotations Useful?**

- **Boilerplate Code Kam Hota Hai**: Aap repetitive code likhne se bachte ho.
- **Compile-Time Errors**: Annotations galtiyan compile-time par pakad leti hain.
- **Code Maintainable Aur Clean Hota Hai**.