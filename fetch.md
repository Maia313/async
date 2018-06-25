
### What is the Fetch API?

The `Fetch API` is an interface that is used to make network requests.

### Why is the Fetch API important?

The `Fetch API` is a much needed improvement over XMLHttpRequest, the old API for making network request. The Fetch API is built into most modern browsers and also returns Promises.

+ What are we going to learn?

   + `How to use the fetch() method to make network requests`
   + `How to extract data from fetch responses`
   + `How to customize network request settings`
   + `How to use Request objects to have more control over the fetch() method.`
   
   
### Basic Fetch Usage

Notice how a `fetch()` method is used to make a simple network request:
```js
fetch("https://jsonplaceholder.typicode.com/todos/1")
    .then(function(result){
       return result.json()  
    })
    .then(function(result){
       console.log(result);
       //logs Object {completed: false, id: 1, title: "delectus aut autem", userId: 1}
    })
    .catch(function(err){
        console.log(err);
});
```
##### Fetch(url)

The `fetch() method takes in an URL endpoint and is used to make a network request`. The fetch() method returns a Promise that contains a Response object.

