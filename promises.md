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

### Sequencing Asynchronous Operations

Asynchronous Operations can be sequenced by returning Promises within then() callbacks.

Imagine that there are three asynchronous functions called getRandomNumber(), getNameFromNumber() and getAgeFromName() that return Promises.

+ The functions do the following:

   + `getRandomNumber()` - asynchronously returns a random number
   + `getNameFromNumber` - takes in a number and asynchronously returns a name
   + `getAgeFromName` - takes in a name and asynchronously returns an age 

If we wanted to first call getRandomNumber() to get an number, then call getNameFromNumber() to get a name from that number, and then lastly call getAgeFromName() on the returned name to get an age then we would have to sequence them correctly.

If they were normal synchronous functions then it would be simple and would look like this:
```js
var number = getRandomNumber();
var name = getNameFromNumber(number);
var age = getAgeFromName(name);
```
However, since the functions are asynchronous, the number variable may be undefined by the time getNameFromNumber() is called and the name variable may be undefined by the time getAgeFromName() is called.

Thus, we need to do the following to sequence them correctly:
```js
//getRandomNumber() returns a promise containing a random number
getRandomNumber().then(function(result) {  
    console.log(result) // 42
    return getNameFromNumber(result); //returns a promise containing a string representing a name

}).then(function(result2){
    console.log(result2) //"Bob"
    return getAgeFromName(result2);  //returns a promise containing a number representing an age

}).then(function(result3){
    console.log(result3) //21

}.catch(function(error){
    console.log(error)
});
```
