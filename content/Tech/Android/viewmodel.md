
[[Android]]

![[reaction-time 1.gif]]

ViewModel ek lifecycle-aware component hai jo **UI-related data** ko store karta hai aur configuration changes (e.g., screen rotation) ke baad bhi data ko **persist** rakhta hai. Ye Activity ya Fragment ke saath tightly coupled nahi hota. 

UI aur data/business logic ko separate rakhta hai.
Ye Activity/Fragment lifecycle ka respect karta hai aur destroy hone ke baad unnecessary resources release kar deta hai.
Shared ViewModel use karke data Fragment ke beech share kiya ja sakta hai:
ye **decoupling** karta hai UI aur data logic ka, jo testing aur maintainability improve karta hai.

viewmodel only gets distroy when owner gets 

how to acheive same without  using viewmodel ?



by using saveInstance but only store small data not large data

# Diff ways to use ViewModel

# **1️⃣ Basic ViewModel (Without LiveData)**

- Used to store and manage UI-related data across configuration changes.
- Useful for storing **simple state variables**.

### **Implementation**

![[Pasted image 20250209094224.png]]

### **Usage in Activity/Fragment**

![[Pasted image 20250209094249.png]]

✅ **Pros:** Survives configuration changes.  
❌ **Cons:** No reactivity, UI won’t update automatically.

---

# **2️⃣ ViewModel with LiveData (Recommended)**

- **LiveData** makes ViewModel reactive by automatically updating UI when data changes.
- Ideal for **observing changes**.

### **Implementation**

![[Pasted image 20250209094341.png]]
### **Usage in Activity/Fragment**

![[Pasted image 20250209094403.png]]

✅ **Pros:** UI updates automatically.  
❌ **Cons:** Extra complexity compared to a simple ViewModel.

---

# **3️⃣ Shared ViewModel (Between Fragments)**

- Used for sharing data between **multiple fragments** within the same **Activity**.
- Best when **fragments need to communicate**.

### **Implementation**

![[Pasted image 20250209094435.png]]

### **Usage in Fragment A (Sender)**

![[Pasted image 20250209094458.png]]
### **Usage in Fragment B (Receiver)**

![[Pasted image 20250209094518.png]]

✅ **Pros:** Works well for inter-fragment communication.  
❌ **Cons:** Needs `requireActivity()`, and data is lost if the activity is destroyed.

---

# **4️⃣ ViewModel with Repository (Best for Large Apps)**

- **Separates UI logic** from data sources (Database, API, etc.).
- Works well with **Room Database**.

### **Implementation**

#### **Repository (Data Layer)**

![[Pasted image 20250209094554.png]]

#### **ViewModel (Business Logic Layer)**

![[Pasted image 20250209094611.png]]

#### **Usage in Activity/Fragment**

![[Pasted image 20250209094631.png]]

✅ **Pros:** Follows **MVVM architecture**, makes the code clean.  
❌ **Cons:** More setup needed.

---

# 5️⃣ ViewModel with SavedStateHandle (To Survive Process Death)

- **SavedStateHandle** helps ViewModel **retain data** even after the app is killed.
- Useful for form data or **restoring UI state**.

### **Implementation**

![[Pasted image 20250209094832.png]]

### **Usage in Activity/Fragment**

![[Pasted image 20250209094911.png]]

✅ **Pros:** Survives app termination, better than LiveData alone.  
❌ **Cons:** Limited to small UI-related data.

---

# **Comparison Table**

|Type|Use Case|Pros|Cons|
|---|---|---|---|
|**Basic ViewModel**|UI logic, non-reactive data|Simple, lightweight|No automatic UI updates|
|**ViewModel + LiveData**|UI updates automatically|Reactive, survives config changes|More setup|
|**Shared ViewModel**|Communication between fragments|Easy for multi-fragment apps|Needs `requireActivity()`|
|**ViewModel + Repository**|Large apps (MVVM)|Clean architecture, separate concerns|Needs repository setup|
|**ViewModel + Hilt**|Dependency Injection|Reduces boilerplate, auto dependency injection|Requires Hilt setup|
|**ViewModel + SavedStateHandle**|Survive process death|Stores UI state efficiently|Limited data storage|

# Diff ways to declare viewmodel 

## **1️⃣ Default Way (ViewModelProvider)**

The **simplest** and most common way to create a ViewModel.

### **In Activity**

```kotlin
val viewModel = ViewModelProvider(this)[MyViewModel::class.java]
```

### **In Fragment**

```kotlin
val viewModel = ViewModelProvider(this)[MyViewModel::class.java]
```

✅ **Pros:** Simple, works in most cases.  
❌ **Cons:** Not suitable for sharing data between fragments.

---

## **2️⃣ Using ViewModelProvider.Factory (Custom Constructor)**

By default, ViewModel doesn’t allow custom parameters in the constructor.  
To pass dependencies, use **ViewModelProvider.Factory**.

### **ViewModel with Constructor**

![[Pasted image 20250209100259.png]]

### **Create Factory**

kotlin

CopyEdit

`class MyViewModelFactory(private val repository: UserRepository) : ViewModelProvider.Factory {     override fun <T : ViewModel> create(modelClass: Class<T>): T {         if (modelClass.isAssignableFrom(MyViewModel::class.java)) {             @Suppress("UNCHECKED_CAST")             return MyViewModel(repository) as T         }         throw IllegalArgumentException("Unknown ViewModel class")     } }`

### **Usage in Activity and Fragment **

![[Pasted image 20250209100335.png]]

✅ **Pros:** Allows passing dependencies.  
❌ **Cons:** Extra boilerplate, better to use **Hilt** for dependency injection.

---

## **3️⃣ Using Activity ViewModel in Fragment (Shared ViewModel)**

Used to share data between multiple fragments inside the **same Activity**.

### **Declare in Fragment A**

`val viewModel = ViewModelProvider(requireActivity())[SharedViewModel::class.java]`

### **Declare in Fragment B**

`val viewModel = ViewModelProvider(requireActivity())[SharedViewModel::class.java]`

✅ **Pros:** Easy way to **share data** between fragments.  
❌ **Cons:** Data is lost when the Activity is destroyed.

---

## **4️⃣ ViewModel with Hilt (Recommended for Large Apps)**

Hilt automatically injects dependencies into ViewModel.

### **Enable Hilt in `Application`**

kotlin

CopyEdit

`@HiltAndroidApp class MyApplication : Application()`

### **ViewModel with Injected Repository**

kotlin

CopyEdit

`@HiltViewModel class MyViewModel @Inject constructor(private val repository: UserRepository) : ViewModel() {     val userName: LiveData<String> = repository.getUserName() }`

### **Declare in Activity**

kotlin

CopyEdit

`@AndroidEntryPoint class MainActivity : AppCompatActivity() {     private val viewModel: MyViewModel by viewModels() }`

### **Declare in Fragment**

kotlin

CopyEdit

`@AndroidEntryPoint class MyFragment : Fragment() {     private val viewModel: MyViewModel by viewModels() }`

✅ **Pros:** Best for dependency injection, less boilerplate.  
❌ **Cons:** Requires **Hilt setup**.

---

## **5️⃣ Using SavedStateHandle (For Process Death Recovery)**

Use **SavedStateHandle** if you need to retain UI state even after process death.

### **ViewModel Implementation**

kotlin

CopyEdit

`class MyViewModel(state: SavedStateHandle) : ViewModel() {     val userName = state.getLiveData("userName", "Default Name")      fun updateUserName(name: String) {         userName.value = name     } }`

### **Declaration in Fragment**

kotlin

CopyEdit

`val viewModel = ViewModelProvider(this, SavedStateViewModelFactory(requireActivity().application, this))     .get(MyViewModel::class.java)`

✅ **Pros:** Survives process death.  
❌ **Cons:** Only works for small UI-related data.

---

## **6️⃣ ViewModel with Kotlin Property Delegation (by viewModels)**

Kotlin provides a **cleaner** way to initialize ViewModel.

### **In Activity**

kotlin

CopyEdit

`val viewModel: MyViewModel by viewModels()`

### **In Fragment**

kotlin

CopyEdit

`val viewModel: MyViewModel by viewModels()`

✅ **Pros:** Less boilerplate, easy to use.  
❌ **Cons:** Cannot be used for shared ViewModels.

---

## **7️⃣ Shared ViewModel in Fragment (Using by activityViewModels)**

If **multiple fragments need the same ViewModel**, use `by activityViewModels()`.

### **In Fragment A**

kotlin

CopyEdit

`val viewModel: SharedViewModel by activityViewModels()`

### **In Fragment B**

kotlin

CopyEdit

`val viewModel: SharedViewModel by activityViewModels()`

✅ **Pros:** Cleaner alternative to `ViewModelProvider(requireActivity())`.  
❌ **Cons:** Only works within the **same Activity**.

---

## **Comparison Table**

|Method|Usage|Pros|Cons|
|---|---|---|---|
|`ViewModelProvider(this)`|Standard ViewModel|Simple to use|No dependency injection|
|`ViewModelProvider.Factory`|Custom Constructor|Allows dependencies|Extra boilerplate|
|`ViewModelProvider(requireActivity())`|Shared ViewModel|Easy for fragment communication|Data lost on activity destruction|
|`by viewModels()`|Cleaner ViewModel Declaration|Less boilerplate|Not for shared ViewModel|
|`by activityViewModels()`|Shared ViewModel (Fragments)|Cleaner than `requireActivity()`|Only works in the same activity|
|**Hilt ViewModel (`@HiltViewModel`)**|Dependency Injection|Best for large apps|Requires Hilt setup|
|`SavedStateHandle`|Survive process death|Keeps UI state after kill|Only for small UI data|