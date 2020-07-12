# Observable Methods


### Retry

Is a method that we can chain at the end of an observable and that will retry the subscription to the observable until it gets a response that does not result in an observable error.

```javascript
this.res$ = this.httpService.loadItems().retry();
```

If you'd like for instance to wait, you could try the `retryWhen` observable method.

```javascript
this.res$ = this.httpService.loadItems().retryWhen(errors => errors.delay(500));
```

This will wait half second before retrying the opeartion.