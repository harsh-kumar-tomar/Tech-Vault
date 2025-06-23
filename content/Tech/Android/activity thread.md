
**ActivityThread** [[Android]] framework ka ek **main component** hai jo ek app ka **main UI thread** control karta hai. Har ek Android app ek **separate process** me chalta hai aur uske andar ek **ActivityThread** hota hai jo us process ka **main execution loop** handle karta hai

## **Role of ActivityThread**

1. **App Process ko Start Karta Hai**
    
    - Jab tum ek app launch karte ho, to `zygote` process ek naya **Linux process fork** karta hai aur `ActivityThread` ka `main()` method call hota hai.
2. **Main (UI) Thread Ko Run Karta Hai**
    
    - Ye **Looper** aur **MessageQueue** ka use karke UI thread ko manage karta hai.
    - Har activity aur UI-related kaam isi main thread pe chalte hain.
3. **Lifecycle Methods Ko Call Karta Hai**
    
    - Jab tumhari activity create hoti hai to `ActivityThread` internally `handleLaunchActivity()` method call karta hai, jo tumhari activity ka `onCreate()` call karne ka kaam karta hai.
    - Isi tarah, `onPause()`, `onResume()`, `onDestroy()` sab `ActivityThread` hi call karta hai.
4. **IPC (Inter-Process Communication) Handle Karta Hai**
    
    - Android me **ActivityManagerService (AMS)** naam ka ek system service hota hai jo har app ke lifecycle ko control karta hai.
    - `ActivityThread` AMS ke saath **Binder IPC** ka use karke communicate karta hai.