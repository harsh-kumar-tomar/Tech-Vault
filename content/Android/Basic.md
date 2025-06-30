[[Android]]

Android uses [[DVM]] (Dalvik Virtual Machine ) rather using [[JVM]](Java Virtual Machine).

## Steps in build process 

First step involves compiling the resources folder (/res) using the [[aapt]] (android asset packaging tool) tool. These are compiled to a single class file called R.java. This is a class that just contains constants.
Second step involves the java source code being compiled to .class files by javac, and then the class files are converted to Dalvik bytecode by the “dx” tool, which is included in the sdk ‘tools’. The output is classes.dex.
The final step involves the android apkbuilder which takes all the input and builds the apk (android packaging key) file.


## Android Application architecture

[[Service]] − It will perform background functionalities
Intent − It will perform the inter connection between activities and the data passing mechanism
Resource Externalization − strings and graphics
Notification − light, sound, icon, notification, dialog box and toast
Content Providers − It will share the data between applications
