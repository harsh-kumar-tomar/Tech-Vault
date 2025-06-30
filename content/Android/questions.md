[[Android]]

1. what is #recyclerview ?
2. what is inflater ?
3. what is architecture pattern 
4. what is Authentication and Authorization ? 
5. iOS: Concurrency, Persistance, Swift, UIKit, Notifications, Architecture Patterns, and everything around it.        
6) Who is the founder of Android? Andy Rubin.
7) What are the advantages of Android?

**Open-source:** It means no license, distribution and development fee.
**Platform-independent:** It supports Windows, Mac, and Linux platforms.
**Supports various technologies:** It supports camera, Bluetooth, wifi, speech, EDGE etc. technologies.
**Highly optimized Virtual Machine:** Android uses a highly optimized virtual machine for mobile devices, called DVM (Dalvik Virtual Machine).

8.  Does android support other languages than java? yes c/c++
9. What are the core building blocks of android?- Activity
  View
- Intent
- Service
- Content Provider
- Fragment


9. define android package and android app bundle 


2. **Comparison Table:**

| Feature            | APK                                                                                                      | AAB                                                                                                             |
| ------------------ | -------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| **Definition**     | Full app package for direct install                                                                      | Optimized app package for Play Store                                                                            |
| **Size**           | Larger due to all resources included                                                                     | Smaller as Play Store optimizes resources                                                                       |
| **Install Method** | Direct via `.apk` file                                                                                   | Needs to be downloaded from Play Store                                                                          |
| **Performance**    | May waste resources (unused ones)                                                                        | More efficient and lightweight                                                                                  |
| **Use Case**       | For sideloading or distribution outside Play Store                                                       | For Play Store apps                                                                                             |
|                    | ./gradlew assembleRelease<br>                                                                            | ./gradlew bundleRelease                                                                                         |
|                    | Agar tum ek beta app ko manually share karna chahte ho via email ya third-party store, APK use hota hai. | Agar tum Play Store pe app publish karte ho, AAB automatically specific APK generate karega har device ke liye. |
Q: can we share aab outisde google store
**A:** Nahi, Play Store ke bahar sirf APK distribute kiya jata hai.

how aab build diff apk for diff device 
**A:** Play Store Dynamic Delivery feature use karta hai jo architecture aur language specific APK generate karega.

**Q: AAB ka fayda kya hai?**  
**A:** Optimized app size, faster download, aur better performance har device pe.

**Q: AAB ka fayda kya hai?**  
**A:** Optimized app size, faster download, aur better performance har device pe.


why us const keyword 
it replaces where ever it is used in the program , and improve performance 
Directly having the value vs accessing it by calling a variable. 


andorid system is a device running android not android os itself 

## Syncronized block 
The `synchronized` keyword is all about different threads reading and writing to the same variables, objects and resources.
 When you have two threads that are reading and writing to the same 'resource', say a variable named `foo`, you need to ensure that these threads access the variable in an atomic way. Without the `synchronized` keyword, your thread 1 may not see the change thread 2 made to `foo`, or worse, it may only be half changed. This would not be what you logically expect.

