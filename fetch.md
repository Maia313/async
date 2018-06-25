
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

### Method

The method attribute is a string that is used to specify the HTTP request method type. 

+ Here is a list of some commonly used method types:

   + `Get - used to retrieve an existing data resource`
   + `Head - used to retrieve HTTP headers`
   + `Post - used to create a new data resource`
   + `Put - used to create a new data resource or modify an existing data resource`
   + `Delete - used to delete a data resource`

Notice how an init object with a method attribute of `"Post"` can be created:
```js
var initObject = {
    method: 'POST'
}
```
#### Body

The body attribute is a JSON string used to send data along with a fetch request. If the body value is an object, it is important to stringify the object that is being sent using `JSON.stringify()` or it will not process correctly. Get and Head HTTP requests can not have bodies.

Notice how an init object with a `body attribute` representing an object can be created:
```js
var myBody = {
    id: 12345,
    name: 'abc',
    age: 21
}

var initObject = {
    body: JSON.stringify(myBody)
}

```

### Headers

The headers attribute is used to add more information about the resource being fetched or the client doing the fetching. A Headers object can be created using the new Headers() constructor and individual headers can be added to the Headers object through the `append()` method.

Notice how `a new Headers object is created and assigned to the headers attribute of the init object`:
```js
var myHeaders = new Headers();
myHeaders.append('Content-Type', 'application/json');

var initObject = {
    headers: myHeaders
}
```
### Mode

The mode attribute is a string that is used to determine whether or not the Fetch request can fetch resources from different servers.

+ In this course we will cover the following two mode types:

   + `same-origin - the Fetch request can only fetch resources from the same server`
   + `cors (cross origin HTTP request) - the Fetch request can fetch resources from different servers`

Notice how an init object is created with a mode attribute set to `'cors'`:
```js
var initObject = {
    mode: 'cors'
}
```
