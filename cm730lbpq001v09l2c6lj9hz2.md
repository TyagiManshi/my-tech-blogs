---
title: "Functions – Building Blocks of JavaScript"
seoDescription: "Explore the differences between Function Declarations and Function Expressions in JavaScript. Learn about hoisting, scoping, and use cases."
datePublished: Thu Feb 13 2025 07:24:39 GMT+0000 (Coordinated Universal Time)
cuid: cm730lbpq001v09l2c6lj9hz2
slug: functions-as-building-blocks-of-javascript
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1739431365158/f80a965e-e5c5-44cd-97e9-b7e31549e3c1.jpeg
tags: javascript, web-development, functional-programming, hiteshchoudharylco, chaicode

---

Functions are one of the fundamental building blocks of JavaScript. They enable modular, reusable, and maintainable code, allowing developers to create efficient and organized programs. In this blog, we will explore function declarations, function expressions, and their use cases.

---

## Introduction

In JavaScript, functions can be defined in two primary ways: **Function Declarations** and **Function Expressions**. While they might seem similar, they have key differences in terms of hoisting, naming, and usage before definition.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1739431343979/666555c6-8a2d-415e-9f6a-a1adb467cd3b.png align="left")

### Function Declaration

A function declaration is a way to define a function using the `function` keyword without assigning it to a variable. The function must have a name.

**Syntax:**

```javascript
function greet(name) {
    return `Hello, ${name}!`;
}
console.log(greet("Manshi")); // Output: Hello, Manshi!
```

In JavaScript, hoisting is a behavior where variable and function declarations are moved to the top of their containing scope during the compilation phase, before the code is executed. This means that functions and variables can be referenced before they are declared in the code.

Function declarations are fully hoisted, meaning both the function's name and its implementation are moved to the top of their scope. As a result, you can invoke a function declaration before its actual position in the code.

```javascript
console.log(add(2, 3)); // Output: 5

function add(a, b) {
    return a + b;
}
```

Even though `add(2, 3)` is called before the function is defined, it works fine due to hoisting.

Function declarations are either in the global scope (if defined outside a block) or local scope (if inside a block like an `if` statement or loop).

---

### Function Expression

A function expression is when a function is assigned to a variable. The function can be either anonymous (without a name) or named.

**Syntax (Anonymous Function Expression):**

```javascript
const greet = function(name) {
    return `Hello, ${name}!`;
};
console.log(greet("Manshi")); // Output: Hello, Manshi!
```

**Syntax (Named Function Expression):**

```javascript
const greet = function greetFunction(name) {
    return `Hello, ${name}!`;
};
console.log(greet("Manshi")); // Output: Hello, Manshi!
```

* Since `add` is a variable, it follows the hoisting rules of `let` and `const`—it is hoisted but remains uninitialized until the execution reaches the assignment.
    
* Function expressions can be anonymous, unlike function declarations.
    
* Function expressions follow block scoping rules, meaning they exist only within the block where they are defined.
    

---

## Key Differences

| **Feature** | **Function Declaration** | **Function Expression** |
| --- | --- | --- |
| **Hoisting** | Yes | No |
| **Naming** | Required | Optional |
| **Usage Before Define** | Allowed | Not Allowed |

---

## Importance

Functions are incredibly important in programming for several reasons:

* Functions enable code reusability, allowing you to write code once and use it multiple times.
    
* They help in modularizing complex tasks, breaking them into smaller, manageable parts.
    
* Functions improve readability, making code easier to understand with descriptive names.
    
* They provide abstraction, focusing on what a function does instead of how it works.
    
* Functions simplify debugging, as individual tasks can be isolated and tested independently.
    
* They offer flexibility, handling different inputs and outputs as needed.
    
* Functions ensure encapsulation, keeping logic contained and reducing conflicts.
    
* They are essential for event handling in web development, managing user interactions efficiently.
    

---

## Conclusion

Both Function Declarations and Function Expressions are essential concepts in JavaScript. The main differences are **hoisting, naming, and when they can be used in a script.**

* If you need a **globally available function**, use Function Declarations.
    
* If you need a function to be used as a **value, such as in callbacks, event handlers, or inside another function**,use Function Expressions.
    

---

**Now that you’ve got the hang of Function Declarations and Function Expressions, it's time to experiment in your projects! 👍 If this blog helped, give it a like and share! Happy coding! ❤️**