[[Android]]
lauch mode
there are 4 ways to open an activity 
1. standard
2. single top
3. single task
4. single instance

suppose we have activity a,b,c,d
and originally it is opened as follow a->b->c->d
**standard** 
this method is followed by activity by default 
now if activity is to opened alll overagain new instance of b would be created 
a->b->c->d->b

**singletop**
if activty instance is already present at the top of instance no new instance will be created otherwise new instance will created 
suppose we are openeing new activty b but not present on the top than new instance will be created 
a->b->c->d->b

singletask
here actiivty will have only one instance only in the system 
a->b->c
if we open d , and it is present on sys new instance will be created 
a->b->c->d
suppose if we create we open activity b , and its instance already present in the  system , than new instance will not be created 
a->b 
and all the instance will be poped off 

singleinstance 
suppose d is not present and we create the instance of d 
a->b->c
d

instance of d is created on its separate task if we create the instance of d again than instance of d is reused 


## task
 **a task is what the user experiences as an "application".** It's a group of related activities, arranged in a stack.


# Context

### What 
Context in Android allows us to access application specific classes and resources. It’s an abstract class and its implementation provided by Android Framework’s itself (provided by AMS : Activity Manager Service ). It’s actually a bridge between our app and the Android System.

context
application context
activity context

# Lifecycle
OnCreate(): This is when the view is first created. This is normally where we create views, get data from bundles etc.
OnStart(): Called when the activity is becoming visible to the user. Followed by onResume() if the activity comes to the foreground, or onStop() if it becomes hidden.
OnResume(): Called when the activity will start interacting with the user. At this point your activity is at the top of the activity stack, with user input going to it.
OnPause(): Called as part of the activity lifecycle when an activity is going into the background, but has not (yet) been killed.
OnStop(): Called when you are no longer visible to the user.
OnDestroy(): Called when the activity is finishing
OnRestart(): Called after your activity has been stopped, prior to it being started again





Why would you do the setContentView() in onCreate() of Activity class?
As onCreate() of an Activity is called only once, this is the point where most initialisation should go. It is inefficient to set the content in onResume() or onStart() (which are called multiple times) as the setContentView() is a heavy operation.
