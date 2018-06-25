
### What is Asynchronous Programming?

Asynchronous programming is about processing code on a separate thread and then handling the result once it is done.

### Why is Asynchronous Programming Important?

Asynchronous Programming prevents slow tasks from blocking faster tasks from running. This allows applications to run without frustrating users by stalling.

+ What are we going to learn?

    + `How  asynchronous code differs from synchronous code`
    + `How to user Callback Functions`
    + `How to use Timers`
    + `How to handle DOM Events`
    
+ **The Call Stack**

`The call stack tracks functions that are currently active and are being processed.`

+ The call stack functions in the following way:

   + When a function call is encountered, it is pushed onto the call stack.
   + Any additional functions called within the original function are placed higher up onto the call stack.
   + When a function finishes executing, it is popped off the call stack and the next function on the call stack is processed.

+ **Stack Overflow**

If the call stack grows too large and exceeds the amount of memory allocated, a Stack Overflow Error will occur. This commonly happens when a function calls itself recursively.
