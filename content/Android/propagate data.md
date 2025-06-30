 [[Fragment]] [[Activity]]

how to get data from one side and push that data to another ?



# Live Data

key concepts : lifecycle 

Live Data

```
val readOnlyLiveData: LiveData<String> = MutableLiveData()
```

Mutable Live Data

```
val mutableLiveData = MutableLiveData<String>()
```

change value on the main thread when we are on main thread 

```
mutableLiveData.value = "New Value"  // Sets the value on the ***main thread***.
```

change value on the background thread when we are on worker thread 

```
mutableLiveData.postValue("Another Value")  // Sets the value on a background thread.
```

---



# Methods 

It is lifecycle-aware, meaning it only receives updates when the observer (like an activity or fragment) is in an active state.

Observe 

```
liveDataObject.observe(lifecycleOwner, Observer { data ->
    // Update UI with the new data
})
```

Observe Forever 

Registers an observer that is always active, regardless of the `Lifecycle` state.
it requires manual removal to prevent memory leaks.


```
liveDataObject.observeForever { data ->
    // React to changes outside of lifecycle-aware components
}
```

Remove Observer 

```
liveDataObject.removeObserver(observer)
```

Basic Implementation 

```
// A simplified version of LiveData that specifically holds an Int.

class SimpleLiveData {

    private var data: Int? = null
    private var observer: ((Int) -> Unit)? = null

    // Method to set new data and notify the observer if present.
    fun setValue(value: Int) {
        data = value
        notifyObserver()
    }

    // Method to register an observer.
    fun observe(observer: (Int) -> Unit) {
        this.observer = observer
        // Notify immediately with the latest value if one exists.
        data?.let { observer(it) }
    }

    // Method to notify the observer about the new data.
    private fun notifyObserver() {
        data?.let {
            observer?.invoke(it)
        }
    }
}

```

# Flow

