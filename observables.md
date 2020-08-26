# Observables

### Implement a broadcast with a `Subject`
`Subjects` implement both the `Observer` and the `Observable` interfaces, meaning that we can use them to both emit values and register subscribers.  
`Subject` has one particularity that prevents us from using it to build `observable data services`: if we subscribe to it we won't get the last value, we will have to wait until some part of the app calls `next()`.  

### `BehaviourSubject` to the rescue
The solution for this is to use a BehaviorSubject. What this type of subject does it that it will return upon subscription the last value of the stream, or an initial state if no value was emitted yet.
```typescript

const behaviourSubject: BehaviorSubject<Type> = new BehaviorSubject(initialState);
```
You can, at any time, retrieve the current value of a `BehaviourSubject`, with
```typescript
behaviourSubject.getValue();
```

### Observables are not shared by default
When we create a subscriber, we are setting up a whole new separate processing chain. The observable is just a definition, a `blueprint` of how a functional processing chain of operators should be set up from the source of the event up until the sink of the event, when that sink (the observer) is attached.

What happens when we subscribe two observers is that two separate processing chains are set up, causing the side effect to be printed twice, once for each chain.

There are ways to define other types of Observables where the side-effect would only be called once (see further). The important is to realize that we should keep two things in mind at all times when dealing with observables:

* Is the observable `hot` or `cold`?
* Is the observable `shared` or not?


### Methods
##### Retry
Is a method that we can chain at the end of an observable and that will retry the subscription to the observable until it gets a response that does not result in an observable error.

```javascript
this.res$ = this.http.loadItems().retry();
```

If you'd like for instance to wait, you could try the `retryWhen` observable method.

```javascript
this.res$ = this.http.loadItems().retryWhen(errors => errors.delay(500));
```

This will wait half second before retrying the opeartion.
