
[[Activity]] 

navigation is basically switching between views.
navigation can happen between 
1. fragments 
2. activities

navigation is diff for more xml/views way and jetpack compose way 

### **Fragment to fragment**
1. Navigation Component 
2. manual 

### **1. Navigation Component**

tools : NavController + NavGraph  + NavHost

**navController** : exposes methods that allow your app to move between the destinations in the graph

how to share data using navigation component ?

define in navgraph

![[Pasted image 20250215223108.png]]

**send**

![[Pasted image 20250215223118.png]]

**retreive** 

![[Pasted image 20250215223211.png]]


### **2. Manual**

tool : FragmentManager

![[Pasted image 20250215222310.png]]

how to share data ? 

**send**

![[Pasted image 20250215223233.png]]

**retrieve**

![[Pasted image 20250215223259.png]]



some others methods to share data 

### **1. using viewmodel** 

![[Pasted image 20250215223319.png]]

send 

```
viewModel.userName.value = "Harsh"
```

retirieve 

![[Pasted image 20250215223406.png]]


### **2. using interface call via activity** 

![[Pasted image 20250215223504.png]]

![[Pasted image 20250215223519.png]]

```
(activity as? FragmentAListener)?.onDataPass("Harsh")
```



---

## **Activity to Activity** 


### **1. Intent** 

![[Pasted image 20250215222424.png]]

how to share data ?

send data

![[Pasted image 20250215222446.png]]

retrieve data

![[Pasted image 20250215222501.png]]


using another type of intent 

![[Pasted image 20250215222605.png]]

### **2. Activity Result api**

it is used to open some event , and to receive some result 

![[Pasted image 20250215222642.png]]
 
![[Pasted image 20250215222654.png]]


### **3. activity result api** 

similarly , it is used to open some event , and to receive some result 

![[Pasted image 20250215222824.png]]

### **ways to finish activity** 


1. 
```
finish()
```

2. 
![[Pasted image 20250215222913.png]]
