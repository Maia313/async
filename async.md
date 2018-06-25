
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

If the call stack grows too large and exceeds the amount of memory allocated, a Stack Overflow Error will occur. `This commonly happens when a function calls itself recursively.`

### The Event Queue

The Event Queue is a queue that keeps track of tasks that are waiting to be put on the call stack to be executed. Tasks get added to the Event Queue by Web APIs that run in parallel with the JavaScript run time.

+ Here are `three examples of Web APIs` that add tasks to the event queue:

   + `Timers `- Timers schedule tasks to be added to the event queue 
   + `DOM Event Handlers` - User Interactions such as mouse clicks and keyboard presses are handled by putting tasks on the event queue
   + `Network Requests` - Network requests are processed asynchronously and send back results by putting tasks on the event queue 

### The Event Loop

When the call stack is empty, it takes the first task off the event queue and processes it. The remaining tasks on the queue wait until the call stack is empty again. This cycle is called the Event Loop.
