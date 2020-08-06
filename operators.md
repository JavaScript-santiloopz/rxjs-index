# Operators



### map
Probably the most well-known functional programming operator out there, and Observable of course provides it. The map operator simply takes an Observable, and adds a transforming function that processes the output of the stream.

### mapTo
Same as map but transform to a static value defined by us, non dependent from the stream input.

### filter
Is basically a barrier that evaluates a boolean operation and let's the stream flow to continue or just cuts it, in case it evaluates to `false`.

### concat
Takes an arbitrary number of observables as parameters and subscribes to them
**in order and sequentially**, meaning the next one won't be subscribed until the 
currently subscribed observable **completes**.
```js
const concatenated$ = concat(
    observable1$, // |-------C--|
    observable2$, //            |-----C--|
    observable3$, //                     |----------C--|
);
```
Once the third observable completes, the results emit.

### combineLatest
Takes an arbitrary number of observables as params, subscribes to them and waits
for **all of them to complete**, just to emit the combined results.

### switchMap
Gets into the observable pipe and returns (switched to) another observable. In order to prevent it to trigger multiple times, might be a good idea to `cache()` it.  
The main advantage of `switchMap` is that in case multiple values are emmited, `switchMap` takes care of unsubscribing from previous requests and, for example, keep alive only one `http` request at a time, releasing the backend from the overhead of many different http request.


### tap
Allows us to perform a certain operation each time the observable emits a value to it's subscribers. This should be used only for development and testing purposes, for instance, to log the value emmited in the console.

```javascript
const obs$ = Observable.fromEvent(input, 'keyup').pipe(
	.tap(value => console.log(value))
);
```

### take
Take a certain amount of observable reads and then cancel subscription.
```javascript
observable.pipe(
	take(1),
);
```