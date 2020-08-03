# Reactive Programming


### Motivation
`Javascript` programming is essentially asynchornousm so it makes total sense to incorporate concepts of functional programming such as `inmutability` of data or `composability`.  
The notion that is missing and which is the heart of `Functional Reactive Programing` might very well be the `stream`. A `stream` is a sequence of values in time, as simple as that. Take for example the following `stream` of numeric values, where each value is issued every one second:
```
---- 0, 1, 2, 3 ,4 .... --->
```
Everything that happens in the browser can be seen as a stream: the sequence of browser events that are triggered when the user interacts with the page, data arriving from the server, timeouts getting triggered.