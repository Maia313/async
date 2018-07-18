
**1**. What is Asynchronous Programming?

> Asynchronous programming is about processing code on a separate thread and then handling the result once it is done.

**2**. Why is Asynchronous Programming Important?

> Asynchronous Programming prevents slow tasks from blocking faster tasks from running. This allows applications to run without frustrating users by stalling.

+ What are we going to learn?

    + `How  asynchronous code differs from synchronous code`
    + `How to use Callback Functions`
    + `How to use Timers`
    + `How to handle DOM Events`
    
**3**. **The Call Stack**

`The call stack tracks functions that are currently active and are being processed.`

+ The call stack functions in the following way:

   + When a function call is encountered, it is pushed onto the call stack.
   + Any additional functions called within the original function are placed higher up onto the call stack.
   + When a function finishes executing, it is popped off the call stack and the next function on the call stack is processed.

**4**. **Stack Overflow**

If the call stack grows too large and exceeds the amount of memory allocated, a Stack Overflow Error will occur. `This commonly happens when a function calls itself recursively.`

**5**. The Event Queue

> The Event Queue is a queue that keeps track of tasks that are waiting to be put on the call stack to be executed. Tasks get added to the Event Queue by Web APIs that run in parallel with the JavaScript run time.

+ Here are `three examples of Web APIs` that add tasks to the event queue:

   + `Timers `- Timers schedule tasks to be added to the event queue 
   + `DOM Event Handlers` - User Interactions such as mouse clicks and keyboard presses are handled by putting tasks on the event queue
   + `Network Requests` - Network requests are processed asynchronously and send back results by putting tasks on the event queue 

**6**. The Event Loop

> When the call stack is empty, it takes the first task off the event queue and processes it. The remaining tasks on the queue wait until the call stack is empty again. This cycle is called the Event Loop.

`Asynchronous Programming` is achieved in JavaScript by using Web APIs that process code on separate threads. The Web API's send their processed results back as tasks on the event queue. These tasks are defined by callback functions passed into the Web APIs. This allows JavaScript to achieve multi-threading in a single threaded run time.

**7**. Synchronous vs Asynchronous Programming

Imagine trying to run a slow task synchronously. It will take a long time to finish processing and will prevent other tasks from running.

**8**. SetTimeout()

The `setTimeout()` method is used to schedule a task to be put on the event queue after a given amount of time. The first parameter to `setTimeout()` is the callback function that is going to be executed. The second parameter is the amount of time to wait before putting the task on the event queue. `setTimeout()` is non-blocking and other code may run while the `setTimeout()` task is waiting to be executed.

**9**. DOM Events

DOM Event Listeners happen in parallel with the JavaScript run time. When an event occurs, the event listener detects the event and executes an event handler to put a task on the event queue. The task will eventually make its way to the call stack to be executed.

If multiple events are detected, multiple tasks will be put on the event queue in the order in which they occurred. When the call stack is empty, the first task on the event queue is pushed onto the call stack. When this task finishes, the cycle continues and the next task on the event queue is pushed onto the call stack. Thus, if a certain task takes a long time to finish, the tasks behind it on the event queue will have to wait.
