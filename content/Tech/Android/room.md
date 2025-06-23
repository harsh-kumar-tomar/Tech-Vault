[[Android]]

Room Database ek Android Jetpack library hai jo SQLite ko ek abstraction layer provide karti hai, taaki hum asani se database ko handle kar sakein bina raw queries likhne ke. Yeh ORM (Object-Relational Mapping) ki tarah kaam karti hai jo SQLite ke upar ek structured layer provide karti hai.

---

Room ek persistence library hai jo teen main components pe kaam karti hai:

1. **Entity** (Database Table ka Representation)
2. **DAO (Data Access Object)** (Queries likhne ke liye Interface)
3. **Database Class** (Jo Room ka entry point hoti hai)

Room ke fayde:  
✅ Compile-time SQL validation (Queries galat likhne pe compile-time error)  
✅ Simple & Clean API  
✅ Lifecycle-aware support  
✅ In-built support for RxJava, LiveData, Flow, etc.  
✅ WorkManager, Paging ke sath achhe se integrate hota hai

Chalo ab ek-ek karke in concepts ko detail me samajhte hain.

---

## **1. Entity (Database Table ka Representation)**

Entity ek model class hoti hai jo ek table ko represent karti hai.

### **Basic Example**

![[Pasted image 20250210182312.png]]

### **Explanation:**

- `@Entity(tableName = "users")` → Table ka naam "users" hoga
- `@PrimaryKey(autoGenerate = true)` → Primary key ko auto-increment karne ke liye
- Class ke har variable ek column represent karta hai

# @entity 
- tableName
- indices
- inheritSuperIndices
- primaryKeys []
- foreign keys
- ignored columns

# @Primary key
- autoGenerate

#### **Advance Concepts:**

1. **Indexes (Faster Query Execution)**
    
    ![[Pasted image 20250210182411.png]]
    
3. **Composite Primary Key**
    
    ![[Pasted image 20250210182443.png]]
    
4. **Embedded Objects (Nested Objects in Table)**
    
    ![[Pasted image 20250210182458.png]]
    

---

## **2. DAO (Data Access Object)**

DAO ek interface hota hai jo queries ko define karta hai. Isme hum CRUD (Create, Read, Update, Delete) operations ke liye SQL likhte hain.

### **Basic DAO Example**


![[Pasted image 20250210182546.png]]

### **Explanation:**

- `@Insert` → Data insert karne ke liye
- `@Update` → Existing data update karne ke liye
- `@Delete` → Data delete karne ke liye
- `@Query("SELECT * FROM users")` → Custom SQL query likhne ke liye

# @Insert
- entity
- onConflict

### **Why Dao ?**

Yeh "Data Access Object" (DAO) naam thoda confusing lag sakta hai, kyunki hum actually **interface** bana rahe hote hain, **object nahi**. Lekin iska naam samajhne ke liye pehle **DAO pattern** ka concept samajhna zaroori hai.

### **1️⃣ DAO ka Full Form & Concept**

**DAO = Data Access Object**  
DAO ek **design pattern** hai jo database access ko **encapsulate** karta hai.

💡 **Encapsulation ka matlab?**  
Matlab yeh ki hum database se related queries ko ek dedicated layer me rakhte hain, jisse **UI aur Business Logic** ka direct database ke saath interaction na ho.

### **2️⃣ Phir Interface Kyu?**

Room me DAO ek **interface hota hai**, lekin **Room khud uska implementation generate karta hai**.

➡️ Jab hum `@Dao` interface likhte hain, to **Room annotation processor** compile-time pe ek **concrete class** ka **object generate** karta hai jo actually queries execute karta hai.

![[Pasted image 20250210185712.png]]

Yeh sirf ek **interface** hai, lekin **Room** iske liye ek **actual class** generate karega, jo database queries execute karegi.

---

### **3️⃣ Object Kahan Se Aaya?**

Jab hum `Room.databaseBuilder()` ka use karke database banate hain, tab Room ek **concrete implementation** provide karta hai, aur hum **DAO ka object** le sakte hain.


![[Pasted image 20250210185928.png]]

👉 **Toh DAO ek interface hota hai, par Room uska implementation object generate karta hai. Is wajah se isse "Data Access Object" kaha jata hai.** 🚀


#### **Advance DAO Concepts**

1. **Conflict Strategy (Duplicate Handling)**
    
    ![[Pasted image 20250210182700.png]]
    
2. **Return Inserted ID**
    
    ![[Pasted image 20250210182723.png]]
    
3. **Multiple Inserts at Once**
    
    ![[Pasted image 20250210182738.png]]
    
4. **LiveData ke saath Data Fetch karna**
    
    ![[Pasted image 20250210182753.png]]
    
5. **Paging Library ke sath Integration**
    
    ![[Pasted image 20250210182819.png]]
    

---

## **3. Room Database Class (Database Entry Point)**

Database class ek abstract class hoti hai jo `RoomDatabase` se extend hoti hai. Isme entities aur DAO ko specify kiya jata hai.

### **Basic Example**

![[Pasted image 20250210182847.png]]
### **Explanation:**

- `@Database(entities = [User::class], version = 1)` → Konse entities ko include karna hai
- `abstract fun userDao(): UserDao` → DAO ko return karne wali method

#### **Database Singleton Pattern**

### **Normal**

![[Pasted image 20250210182929.png]]

or 
### **using hilt**

![[Pasted image 20250210184058.png]]


👉 **Thread safety ke liye Singleton Pattern use kiya jata hai**  
👉 **Database ko ek hi instance me maintain karna better performance deta hai**

---

## **4. Room me Migration ka Concept**

Agar database ki version update hoti hai to migration ka dhyan rakhna padta hai.

### **Without Migration (Data Loss)**

![[Pasted image 20250210183034.png]]

### **With Migration (Data Safe)**

![[Pasted image 20250210183059.png]]

👉 **Migration se purana data safe rahta hai aur naye columns bhi add ho jate hain**








