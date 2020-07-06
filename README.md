# RxJs index


### Observables over promises
* Easier to chain and compose
* Extended API
* Cancellable
* Retriable

### Operators
* `take`: take a certain amount of observable reads and then cancel subscription.
```javascript
observable.pipe(
	take(1),
);
```
