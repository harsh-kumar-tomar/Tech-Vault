[[Areas/Tech/Kotlin/Kotlin|Kotlin]] [[Android]]

Coroutine Scope is like time period of that code . So basically it defines the lifecycle of code . 
It is like a thread to run code concurrently with the rest of the code . 
Scopes 


Coroutine Scope (Custom )

viewmodelScope : code lifecycle is tied to viewmodel lifecycle
lifecycleScope : code lifecycle is tied to lifecycle of fragment or activity
GlobalScope : code lifecycle is tied to lifecycle of application . Quite dangerous 

But where to execute , this code main thread or background thread ?

this is specified my Dispatcher 
Dispatcher.Main : in main thread 
Dispatcher.IO : backg thread
Dispatcher.Default : 


there are also two ways to lauch methods 
lauch : normal just run the code 
asyc : when i want to control when to stop the code or coroutine 

fact
## withContext

it is suspending  fuction used to switch temporary to the main thread , so if coroutine is doing some task in the background thread and want to set data to mainthread or UI it can use with context . 
so basically it stops the coruitnescope , switch to main thread and comes back , it also have 

![[yonko-moon.gif|400]]


## launch

launch or asyc

lauch is used to stop a coroutine or in  other words to control the lifecycle of coroutine . so basically any coroutine returns a job , which is it lifecycle . so basically it return a control switch . 
and async return a deffered object which is a special version of job , but returns a value 


![[nezba-stop.gif|300]]


![[flip-that-switch-lisa-alexandra.gif|400]]

async is used to return a value like integer or string 




# that it for today , relax now !!! 

![[dont-care.gif|400]]
