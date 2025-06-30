[[Android]]

![[flood-pipe.gif|300]]
## What 
Memory leak tab hota hai jab app kuch unused objects ko memory me hold karke rakhta hai aur unhe release nahi karta. Ye objects garbage collector se reclaim nahi hote, jiske wajah se memory consumption badhta hai aur app crash ya slow ho sakti hai.

![[error-windows 1.gif]]

## Causes
- **Activity Context Leaks:** Activity ka reference kisi static variable me hold karna.
- **Anonymous Inner Classes:** Inner classes ya lambdas jo outer class ka implicit reference hold karti hain.
- **Listeners and Callbacks:** Properly unregister na karna (e.g., BroadcastReceiver, EventListeners).
- **Static Views:** Views ko static variable me hold karna.
- **Long-Lived Background Threads:** Thread run kar raha ho aur Activity destroy ho jaye.



how to  identify ?
Android Studio ka Profiler ya third-party tool **LeakCanary** ka use karke.

**Garbage Collector memory leak fix kyun nahi karta?**  
 GC un objects ko release karta hai jo no longer reachable hote hain. Lekin agar tumhara code unnecessary references hold karega, toh GC unhe reclaim nahi karega.

**Threads memory leak kaise create karte hain?**  
Agar background thread chal raha ho aur Activity destroy ho jaye, toh thread Activity ka reference hold karke memory leak kar sakta hai.

```
override fun onDestroy() {
    thread.interrupt() 
    super.onDestroy()
}
```

# types of references 


![[point-at-you-point.gif]]
# Strong References

When you create an object in Kotlin, you are using a strong reference by default. A strong reference keeps the object alive as long as the reference to it exists. If there are no more strong references to an object, it becomes eligible for garbage collection

```
class Person(val name: String)  
  
fun main() {  
val person = Person("Mahmoud")  
println(person.name) // Output: Mahmoud  
}
```


## weak reference 

generally used for caching for example 