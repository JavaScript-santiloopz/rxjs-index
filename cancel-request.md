# Cancel Request

Sometimes a network request takes long and maybe the user navigates away, so it is no longer needed.
To cancel a request, simply save the subscription in a variable of type subscription and unsubscribe programmatically.

```javascript
this.subscription = thos.obs$.loadItems().subscribe(
	items => this.items = items,
);

cancel() {
	this.subscription.unsubscribe();
}
```

