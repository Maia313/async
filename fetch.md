
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

### Extracting data from a Response object:

A Response object has several methods that are used to extract the fetched data.

+ Here are the common extraction methods:

   + `json() is used to extract a json object`
   + `text() is used to extract a text string`
   + `blob() is used to extract a file-like object`


### Fetch Init Object

The `fetch()` method can also take in an optional init object. This object applies custom settings to the Fetch request.

Notice how the `fetch()` method is used with an `URL endpoint` and an init object:
```js
//this init object specifies the method, headers, mode and body of the request
var initObject = {
    method: 'POST',
    headers: new Headers(),
    mode: 'cors',
    body: "{}" 
}

//fetch() method used with an URL endpoint and an init object
fetch("https://jsonplaceholder.typicode.com/posts",initObject) 
    .then(function(result){ //result contains a Response object
       return result.json() //returns a promise containing JSON data extracted from the Response object

    })
    .then(function(result){
       console.log(result);
       //logs Object {id: 101}

    })
    .catch(function(err){
        console.log(err);
});
```
+ The following attributes of the init object will be covered in more detail in the next few sections:

   + `method`
   + `body`
   + `headers`
   + `mode`

