[[Programming]]

4. what is Authentication and Authorization ? 
## Authentication -> kaun ho tum
kisi user ki identity verify karna hai. Ye tab hota hai jab aap kisi system mein login karte ho aur apna username aur password daalte ho. System check karta hai ki ye details sahi hain ya nahi. Agar sahi hain, to aapko authenticate kar diya jata hai.

## Authorization -> tum kya kar sakte ho
matlab iske baad aapko kya karne ki permission hai, ye decide karna hai. Ek baar authenticate hone ke baad, system check karta hai ki aapke account ke paas kya rights hain. Kya aap data dekh sakte ho, edit kar sakte ho, ya delete kar sakte ho? Ye sab authorization ke under aata hai.


## singleton
Singleton ek design pattern hai jisme ek class ka sirf ek hi instance create hota hai aur woh globally accessible hota hai. Iska use tab hota hai jab tumhe ek common resource (e.g., database) ko share karna ho.
eg Ek music player app me tumhe ek audio manager chahiye jo ensure kare ki ek hi time par ek song play ho.

**Kotlin** - Kotlin me `object` keyword se direct Singleton implement ho jata hai, thread-safety built-in hoti hai.

### Benfits 
1. Common resources ka efficient management aur memory utilization improve hota hai.

### Problems 
1. Ye tightly coupled code create kar sakta hai jo testing aur scaling me problem create kare.


system design 
it is the process of d
functional -> features of a application 
non funcitonal 

important and non imprtanat features ko balance karna 

# why so serious 
- scalable
- less downtime 
- low latency 
- mutiple copies 
- data consistency 
- load should be evenly diributed 
- reusable 
- work togerether best effiecny 
