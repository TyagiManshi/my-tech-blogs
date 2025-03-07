---
title: "Event Loop in JavaScript 🎡"
datePublished: Fri Mar 07 2025 05:09:16 GMT+0000 (Coordinated Universal Time)
cuid: cm7ybfydz000j09l7ahpvddbd
slug: event-loop-in-javascript
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1741324041343/02883c7d-855e-4d07-a97d-132041202d84.jpeg
tags: javascript, web-development, event-loop, hiteshchoudharylco, chaicode

---

In the world of JavaScript, the event loop is what makes asynchronous operations possible without blocking the main thread. It’s the heart of how JavaScript handles multiple tasks at once, keeping web applications smooth and responsive.

If you've ever wondered why JavaScript doesn’t freeze when waiting for a network request or a timer to complete, the event loop is the answer. Understanding this concept is key to writing efficient and performant web applications.

Now, if terms like 'asynchronous' or 'call stack' sound intimidating, don’t worry—I’ll break them down so that anyone, regardless of experience level, can grasp how the event loop works. But before we delve into what that means, let’s first understand how JavaScript works and why we even need the event loop.

[![](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExZ3EyajVscHpxajk4cGM5cHlmeDhlODFqN244MW9tNmtyMnQ2dWdodCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/l0MYGkpex3mWWZVni/giphy.gif align="center")](https://www.google.com/search?sca_esv=3ec8625b255dccb3&rlz=1C1YTUH_enIN1091IN1091&sxsrf=AHTn8zqx_0S9wXUDpJHqR12kOOvYKJUvjA:1741275539327&q=why+gif&udm=2&fbs=ABzOT_CWdhQLP1FcmU5B0fn3xuWpA-dk4wpBWOGsoR7DG5zJBtmuEdhfywyzhendkLDnhcoz2MIB1dVLatL09WpR-ccvltN6Az9MhRb9E6EfXL--Jf9MavXSLrzMxJbiLmI9rHPT1po8TZ7NwSS0ZHz07Y7r1sPKPL0Mflvp-_Ysi1RHaSFxsTn2M3nNBYCjxJ8CcVn4bUrl7phomdx1HYwe6uaUDzI5NQ&sa=X&ved=2ahUKEwiK6ujv5PWLAxUPSGcHHXBdAYUQtKgLegQIERAB&biw=1536&bih=730&dpr=1.25#vhid=HJubd-gPgOTuBM&vssid=mosaic)

## JavaScript Works on a Single Thread

Imagine a single waiter at a restaurant taking orders, serving food, and handling payments. Since there is only one waiter (just like JavaScript is single-threaded), they can only serve one customer at a time. Each order must be taken, prepared, and served before moving on to the next one.

```javascript
console.log('Welcome to the restaurant');

function takeOrder(order1, order2) {
  return `Order placed: ${order1} and ${order2}`;
}

const order = takeOrder('Pasta', 'Pizza');
console.log(order);

console.log('Serve the food');

// Expected Output:

// Welcome to the restaurant
// Order placed: Pasta and Pizza
// Serve the food
```

**Explanation:**

1. The waiter welcomes the customer.
    
2. The `takeOrder` function is called, and the order is placed immediately.
    
3. The food is served.
    
4. Each step happens in order, just like JavaScript executes code sequentially.
    

## Handling Delays with Asynchronous Code

Now, what if a dish takes time to cook? Instead of making all customers wait, the waiter moves on to take the next order while the kitchen prepares the dish in the background.

```javascript
console.log('Welcome to the restaurant');

setTimeout(() => {
  console.log('Dish is ready!');
}, 5000);

console.log('Take the next order');

// Welcome to the restaurant
// Take the next order
// Dish is ready!
```

**Explanation:**

1. The waiter welcomes the customer.
    
2. The dish is sent to the kitchen (`setTimeout` schedules an async task).
    
3. Instead of waiting, the waiter takes the next order (`Take the next order` logs immediately).
    
4. Once the dish is ready (after 5 seconds), the waiter serves it (`Dish is ready!`).
    

## Why Do We Need the Event Loop?

If the waiter stood still waiting for the dish to be ready, the entire restaurant would come to a halt. That’s exactly what would happen in JavaScript without the event loop—long-running operations would freeze everything else.

Instead of waiting 5 seconds and blocking other operations, the event loop allows JavaScript to move on and handle other tasks while waiting for the dish (async operation) to be prepared.

---

## What is the Event Loop?

The event loop is a process that enables JavaScript to handle asynchronous operations while maintaining a non-blocking environment, even though it runs on a single thread. It continuously checks the call stack and task queues to decide what should be executed next, allowing asynchronous operations like timers, API calls, and user interactions to run without blocking the main thread.

1. **Call Stack**  
    The **call stack** is a data structure that keeps track of function calls in JavaScript. It follows the **Last In, First Out (LIFO)** principle, meaning the last function pushed onto the stack is the first to be executed.
    
2. **Web APIs**
    
    JavaScript’s runtime environment (browser or Node.js) provides **Web APIs**, such as:
    
    * setTimeout()
        
    * fetch()
        
    * DOM Events
        
    * setInterval()
        
    * AJAX requests
        
    
    These APIs allow JavaScript to perform asynchronous operations by handling tasks in the background.
    
3. **Task Queue (Callback Queue)**  
    When an asynchronous function like `setTimeout()` completes, its callback is placed in the **task queue**. These tasks wait for the **call stack** to be empty before they run.
    
4. **Microtask Queue (Higher Priority)**
    
    Microtasks like Promises go into a separate **microtask queue**. These tasks always run **before** the tasks in the task queue.
    

---

## How the Event Loop Works?

```javascript
console.log("Start");

setTimeout(() => {
  console.log("Task Queue: setTimeout");
}, 2);

Promise.resolve().then(() => {
  console.log("Microtask Queue: Promise");
});

console.log("End");
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1741321628249/315c4a5b-d2c7-4f82-8227-ecf76a9b3e3d.png align="center")

1. The JavaScript engine starts executing the script line by line in the **Call Stack**.
    
2. **"Start"** is printed.
    
3. **setTimeout()** is encountered
    
    * The browser sets a 2-second timer and registers the callback function (`() => console.log("Task Queue: setTimeout")`).
        
    * The function **does not execute now**; instead, it is placed in the **Task Queue** to run later.
        
    * `setTimeout` itself exits, and execution moves forward.
        
4. **Promise.resolve().then(...)** is encountered
    
    * The callback inside `.then()` (`console.log("Microtask Queue: Promise")`) is **added to the Microtask Queue**.
        
    * This function will execute after all synchronous code finishes.
        
5. **"End"** is printed immediately.
    
6. **Call Stack is now empty.** Since all synchronous tasks are done, the **Event Loop checks the Microtask Queue first**.
    
7. **"Microtask Queue: Promise"** is printed from the .then() callback.
    
8. 2 seconds pass, timer expires. The browser moves the setTimeout callback function to the **Task Queue**.
    
9. **Event Loop checks the Call Stack.** Since the Call Stack is empty, it **takes the** setTimeout callback from the Task Queue and runs it.
    
10. Task Queue executes setTimeout callback. **"Task Queue: setTimeout"** is printed.
    

---

**Even though the delay is 0ms, setTimeout does not execute immediately; it waits until the Call Stack is empty and after all Microtasks are completed.**

If the setTimeout delay is 0 milliseconds, the execution flow remains the same because setTimeout always places its callback in the Task Queue, which runs after the Microtask Queue. So, even with 0ms, JavaScript first runs all synchronous code, then executes Promises (Microtask Queue), and only after that, it picks up the setTimeout callback from the Task Queue. This means the output will still be:

Start  
End  
Microtask Queue: Promise  
Task Queue: setTimeout

---

## Task Starvation

Now imagine this, if micro tasks keep popping up without allowing other tasks a chance to run, what happens next ?

In this scenario, the callback queue won’t get the opportunity to execute it’s tasks. This is Startvation of Tasks in the callback queue.

---

**❤️ If you found this helpful, consider sharing it with fellow developers!**  
**💡 Still have questions or insights? Drop them in the comments—I’d love to discuss!**