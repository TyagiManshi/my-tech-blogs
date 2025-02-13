---
title: "Functions – Building Blocks of JavaScript"
seoTitle: "Understanding JavaScript Functions: Function Declarations vs Function "
seoDescription: "Explore the differences between Function Declarations and Function Expressions in JavaScript. Learn about hoisting, scoping, and use cases."
datePublished: Thu Feb 13 2025 06:58:55 GMT+0000 (Coordinated Universal Time)
cuid: cm72zo8dm000808lae1qrbm79
slug: functions-building-blocks-of-javascript
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1739427569113/ac1eeef0-ced9-4674-bfd5-6f4294e75bb8.jpeg
tags: javascript, web-development, functional-programming, chaicode

---

Functions are one of the fundamental building blocks of JavaScript. They enable modular, reusable, and maintainable code, allowing developers to create efficient and organized programs. In this blog, we will explore function declarations, function expressions and use cases.

---

## Introduction

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1739429858237/7bc1e370-38b0-4217-9eb7-46489f5cbd67.png align="left")

In JavaScript, functions can be defined in two primary ways: **Function Declarations** and **Function Expressions**. While they might seem similar, they have key differences in terms of **hoisting, naming, and usage** before definition.

1. ### Function Declaration
    

A **function declaration** is a way to define a function using the `function` keyword **without assigning it to a variable**. The function must have a name.

**Syntax:**

```javascript
function greet(name) {
    return `Hello, ${name}!`;
}
console.log(greet("Manshi")); // Output: Hello, Manshi!
```

In JavaScript, **hoisting** is a behavior where variable and function declarations are moved to the top of their containing scope during the compilation phase, before the code is executed. This means that functions and variables can be referenced before they are declared in the code.

Function declarations are fully hoisted, meaning both the function's name and its implementation are moved to the top of their scope. As a result, you can invoke a function declaration before its actual position in the code.

```javascript
console.log(add(2, 3)); // Output: 5

function add(a, b) {
    return a + b;
}
```

* Even though `add(2, 3)` is called before the function is defined, it works fine due to **hoisting**.
    
* Function declarations are either in the **global scope** (if defined outside a block) or **local scope** (if inside a block like an if statement or loop).
    

---

2. ### Function Expression
    

A **function expression** is when a function is assigned to a variable. The function can be either **anonymous** (without a name) or **named**.

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

* Since `add` is a **variable**, it follows the hoisting rules of `let` and `const`—it is hoisted but remains **uninitialized** until the execution reaches the assignment.
    
* Function expressions **can be anonymous**, unlike function declarations.
    
* Function expressions follow block scoping rules, meaning they exist **only within the block where they are defined**.
    

---

3. ### Key Differences
    

| Feature | Function Declaration | Function Expression |
| --- | --- | --- |
| Hoisting | Yes | No |
| Naming | Required | Optional |
| Usage Before Define | Allowed | Not Allowed |

---

## Importance

Functions are incredibly important in programming for several reasons:

* Functions enable **code reusability**, allowing you to write code once and use it multiple times.
    
* They help in **modularizing** complex tasks, breaking them into smaller, manageable parts.
    
* Functions improve **readability**, making code easier to understand with descriptive names.
    
* They provide **abstraction**, focusing on what a function does instead of how it works.
    
* Functions simplify **debugging**, as individual tasks can be isolated and tested independently.
    
* They offer **flexibility**, handling different inputs and outputs as needed.
    
* Functions ensure **encapsulation**, keeping logic contained and reducing conflicts.
    
* They are essential for **event handling** in web development, managing user interactions efficiently.
    

---

## Conclusion

Both **Function Declarations** and **Function Expressions** are essential concepts in JavaScript. The main differences are **hoisting**, **naming**, and **when they can be used** in a script.

* If you need a **globally available function**, use **Function Declarations**.
    
* If you need a function to be **used as a value,** **such as in callbacks, event handlers or inside another function**, use **Function Expressions**.
    

---

**Now that you’ve got the hang of Function Declarations and Function Expressions, it's time to experiment in your projects! 👍 If this blog helped, give it a like and share! Happy coding!** ❤️