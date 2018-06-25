### What are Promises?

`Promises` are containers for values that are not yet available yet but may eventually become available.

### Why are Promises important?

Promises are becoming the standard way to handle asynchronous functions in JavaScript.

+ What are we going to learn?

   + How to create a Promise
   + How to get the result out of a Promise
   + How to chain Promises together
   + How to handle multiple Promises at the same time

### Creating a new Promise
```js
var promise = new Promise(function(resolve, reject) {

    //do stuff

    var isSuccessful = true;

    if (isSuccessful) { /*if everything is successful*/
        resolve("Success!");
    }
    else {              /*if something went wrong*/
        reject(Error("Failure."));
    }
});
```

The new `Promise() constructor` is called to create a new promise. The constructor takes in a callback function with the arguments resolve and reject:
```js
var promise = new Promise(function(resolve, reject) {
    
});
```

`Resolve()`

The resolve() function is used to change the status of the promise from pending to fulfilled. The value that is passed inside the resolve() function becomes the fulfillment value of the promise.

Once the resolve() function is called, future resolve() and reject() calls no longer have any effect.

`Reject()`

The reject() function is used to change the status of the promise from pending to rejected. The value that is passed inside the reject() function becomes the rejection value of the promise.

Once the reject() function is called, future resolve() and reject() calls no longer have any effect.

The resolve function can take in any object as an argument, but one common practice is to pass in a Error object because it provides a more detailed error report. 
