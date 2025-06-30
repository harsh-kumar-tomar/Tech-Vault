[[Java]]

## Reactive programming 
**Reactive Programming** is a programming paradigm oriented around data flows and the propagation of change

## Reactive extension 
**Reactive Extensions** is a library that follows Reactive Programming principles to compose asynchronous and event-based programs by using observable sequence.

## RxJava
is a Java based implementation of Reactive Programming.


## RxAndroid
**RxAndroid** is specific to Android platform which utilises some classes on top of the RxJava library.


Building blocks of RxJava
- Observable : class that emits a stream of data or events 
(class that can be used to perform some action, and publish the result.)

```
Observable observable = Observable.just("A", "B", "C", "D", "E", "F");
```

- Observer : class that receivers the events or data and acts upon
(class that waits and watches the Observable, and reacts whenever the Observable publishes results)

observer have 4 interfaces 
- **onSubscribe():** This method is invoked when the Observer is subscribed to the Observable.
- **onNext():** This method is called when a new item is emitted from the Observable.
- **onError():** This method is called when an error occurs and the emission of data is not successfully completed.
- **onComplete():** This method is called when the Observable has successfully completed emitting all items.

```
new Observer() {
            @Override
            public void onSubscribe(Disposable d) {
                System.out.println("onSubscribe");
            }

            @Override
            public void onNext(Object o) {
                System.out.println("onNext: " + o);
            }

            @Override
            public void onError(Throwable e) {
                System.out.println("onError: " + e.getMessage());
            }

            @Override
            public void onComplete() {
                System.out.println("onComplete");
            }
        };
```
