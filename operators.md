# Operators


### Concat
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

### CombineLatest
Takes an arbitrary number of observables as params, subscribes to them and waits
for **all of them to complete**, just to emit the combined results.
