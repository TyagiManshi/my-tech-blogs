---
title: "Prototypes and Object Inheritance"
datePublished: Fri Feb 21 2025 06:56:54 GMT+0000 (Coordinated Universal Time)
cuid: cm7ef4ft4000u09jlcpfadbof
slug: prototypes-and-object-inheritance
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1740120881197/b160354f-d3ee-4d52-b052-d094eda5cc1a.jpeg
tags: javascript, web-development, software-engineering, object-oriented-programming, hiteshchoudharylco, chaicode

---

We hear this a lot, everything is an object in JavaScript, okay, well, how are you saying that? How to prove everything (like function, array, class & variables) is Object in JavaScript ? Let’s get started with simple example. Open your favourite browser (mine is Chrome) open the inspect window, click on console and create an array like the screenshot shown below.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1740054528878/65dee25d-1399-46ae-9054-0fa4d275ed55.png align="center")

Observe the Image carefully, we just created an array named arr and in the next line if we type arr followed by “.” then we are listed with set of functions which can be used with the arrays like map, concat, length etc. how did all this came ? Every JavaScript developer with basic knowledge is using array and it’s methods everyday, but we have just created Array and how all these functions are made accessible to it.

***Answer is*** ***Prototype: All JavaScript programming constraints inherit properties and methods from a prototype. So, when we say, "everything is an object," it just means JS treats most things with the same structure!***

---

## **What is a Prototype?**

Think of a **prototype** as a **blueprint** for objects. Imagine you are building houses in a neighborhood—each house follows the same blueprint but can have its own unique features. Similarly, in JavaScript, objects are created from other objects using **prototypes**.

Every JavaScript object has an internal link to another object, called its **prototype**. This prototype acts as a **fallback** for properties and methods that the object itself does not have.  
It is a special feature that allows objects to inherit properties and methods from other objects. This means one object can use functions or properties that it did not define itself.  
Let’s understand this with an example:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1740066662665/66f04329-75ed-4d89-97cd-bb197546e776.png align="center")

Here, we created a person object with two properties: name and a greet function.

When we log `person` to the console, we see its properties first. Below that, there's a `[[Prototype]]` section, which links the object to `Object.prototype`. This means `person` can access built-in methods like `toString()`, `hasOwnProperty()`, and more, even though they weren’t defined inside it.

This shows how prototypes help objects inherit properties and methods from other objects, making JavaScript more efficient.

---

## **Prototype Chaining**

When you try to access a property or method on an object, JavaScript first checks if it exists on the object itself. If not, it looks up the prototype chain, checking each prototype until it finds the property or reaches null (the end of the chain). This is called **prototype chaining**.

### How Prototype Chaining Works

Every object has a hidden link (`[[Prototype]]`) that connects it to another object, called its **prototype**. If an object doesn’t have a property, JavaScript checks its prototype, then its prototype's prototype, and so on. The `__proto__` property lets us manually check or modify this hidden link, but it's mainly for debugging.

#### Example of Prototype Chaining:

```javascript
const grandparent = {
  greet: function() {
    console.log("Hello from Grandparent!");
  }
};

const parent = Object.create(grandparent);
const child = Object.create(parent);

child.greet(); // Output: "Hello from Grandparent!"
```

Here’s what happens in the example above:

1. child does not have a greet method.
    
2. JavaScript looks up the prototype chain and finds greet in grandparent.
    
3. The method is executed, demonstrating inheritance through prototype chaining.
    

---

### \_\_proto\_\_ vs prototype

\_\_proto\_\_ and prototype are related to inheritance in JavaScript, but they are used in different ways:

* `__proto__` is a property that exists on all objects. It points to the object’s prototype (or parent). You can use it to access or change an object's prototype.
    
* `prototype` is a property of constructor functions (like classes). It’s used to add methods or properties to all objects created with that constructor.
    

> **<mark>Note: We should never use proto property in the production code.</mark>**<mark><br>However</mark> **<mark> person.__proto__ and Object.prototype </mark>** <mark>references to same object.</mark>

---

### Object Creation and Prototype Linking

In the backend of JavaScript, when we create an object, its properties and methods are connected through `ObjectName.prototype`. This mechanism ensures that instances of an object can inherit shared properties and methods.

#### Example:

```javascript
function Person(name) {
  this.name = name;
}

Person.prototype.sayHello = function() {
  console.log("Hello, my name is " + this.name);
};

const user = new Person("Manshi");
user.sayHello(); // Outputs: Hello, my name is Manshi
```

Here’s how it works:

1. The Person function acts as a constructor.
    
2. Person.prototype holds the shared method sayHello.
    
3. When user.sayHello() is called, JavaScript looks up the prototype chain and executes the method from Person.prototype.
    

In JavaScript, methods can be defined inside an object’s prototype so that all instances share the same method, rather than each object having its own copy.

**Why use prototype methods?** This approach **saves memory** by ensuring all instances share the same method instead of duplicating it.

---

### Overriding Properties in the Prototype Chain

You might be wondering, "Can we create a method with the same name as the Object's prototype?" The answer is yes, and it will return the value that you define in it.

If a property exists both on the object and in the prototype chain, the object's own property takes precedence. This is known as **shadowing**.

This happens because JavaScript first checks if the method we are calling exists in the object itself. If it doesn't, JavaScript then looks in the object's prototype.

```javascript
const animal = {
  sound: "Roar"
};

const lion = Object.create(animal);
lion.sound = "Growl";

console.log(lion.sound); // Outputs: "Growl"
```

---

## Prototypal Inheritance

If you’re coming from a language like Java, C++, or Python, you might be wondering: *How does JavaScript’s inheritance differ?* Instead of using class-based inheritance, JavaScript follows a prototypal model. But what does that really mean for you?

#### How Do Objects Inherit Properties?

In classical inheritance, you define a class, create objects (instances) from it, and each instance has its own copy of methods and properties. In JavaScript, however, objects inherit properties dynamically from other objects through the prototype chain.

#### Is One More Flexible Than the Other?

Yes! Prototypal inheritance is more flexible. In classical inheritance, once you define a class structure, it’s fixed unless you rewrite it. With JavaScript’s prototype-based approach, you can extend objects dynamically at runtime.

#### What About Multiple Inheritance?

JavaScript allows you to mix behaviors from multiple objects easily using prototypes, while classical inheritance often struggles with this due to rigid class structures.

#### Example**:**

```javascript
const vehicle = {
  move: function() {
    console.log("Vehicle is moving");
  }
};

const car = Object.create(vehicle);
car.drive = function() {
  console.log("Car is driving");
};

car.move(); // Output: "Vehicle is moving"
car.drive(); // Output: "Car is driving"
```

Here’s how it works:

1. car is created using Object.create(vehicle), meaning it inherits from vehicle.
    
2. car gets access to the move method from vehicle.
    
3. drive is added to car, making it unique to car but not available on vehicle.
    

---

## ES6 Class-Based Inheritance – A More Structured Approach

So far, we have explored how JavaScript objects inherit properties through **prototypes**. With ES6, JavaScript introduced **class-based syntax**, making inheritance more structured while still using prototypes under the hood.

### Why ES6 Classes?

ES6 classes provide a more readable and structured way to define object-oriented code. They offer a syntax that is more familiar to developers coming from languages like Java and C++, while still preserving JavaScript’s prototype-based nature.

The key benefits of ES6 classes include:

* A cleaner and more intuitive way to define objects and inheritance
    
* Built-in constructor functions for initializing objects
    
* More maintainable code for larger applications
    

Consider a simple example using ES6 classes:

```javascript
class Animal {
  constructor(name) {
    this.name = name;
  }
  speak() {
    console.log(`${this.name} makes a sound.`);
  }
}

const dog = new Animal("Buddy");
dog.speak(); // Output: Buddy makes a sound.
```

---

### Extending a Class with `extends`

In ES5, inheritance required manually setting up the prototype chain using `Object.create()`. With ES6, the `extends` keyword allows one class to inherit from another in a more structured manner.

#### Example: Creating a Dog class that inherits from Animal

```javascript
class Dog extends Animal {
  constructor(name, breed) {
    super(name); // Calls the parent class constructor
    this.breed = breed;
  }
  bark() {
    console.log(`${this.name} barks.`);
  }
}

const myDog = new Dog("Buddy", "Golden Retriever");
myDog.speak(); // Output: Buddy makes a sound.
myDog.bark();  // Output: Buddy barks.
```

---

### Understanding super in ES6 Inheritance

1. When a class extends another class, the child constructor must call super() first before using “this”.
    
2. super() calls the parent class constructor and sets up this for the child class.
    
3. If you don’t call super(), JavaScript will throw a ReferenceError when trying to use this inside the child's constructor.
    
4. If you don’t define a constructor in the child class, JavaScript automatically calls super() for you.
    
5. super() must match the parent class constructor parameters.
    

```javascript
class Bird extends Animal {
  constructor(name, canFly) {
    super(name);
    this.canFly = canFly;
  }
  speak() {
    super.speak(); // Calls Animal's speak method
    console.log(`${this.name} is chirping.`);
  }
}

const parrot = new Bird("Kiwi", true);
parrot.speak(); 
// Output:
// Kiwi makes a sound.
// Kiwi is chirping.
```

---

### ES5 vs ES6 Inheritance – Key Differences

| **ES5 (Prototype-Based)** | **ES6 (Class-Based)** |
| --- | --- |
| `function Constructor()` creates a function to act as a constructor. | `class ClassName {}` defines a class for the constructor. |
| `Object.create(Parent.prototype)` manually links child to parent. | `extends` keyword simplifies inheritance between classes. |
| [`Parent.call`](http://Parent.call)`(this, args)` manually invokes the parent constructor. | `super(args)` is used to call the parent constructor. |
| `Constructor.prototype.method = function() {}` adds methods to the constructor's prototype. | `method() {}` defines methods directly inside the class. |

---

### Is ES6 Truly Class-Based?

While ES6 provides class syntax, JavaScript remains a prototype-based language. Classes in JavaScript do not create a separate class hierarchy like in Java or C++; rather, they are syntactical sugar over prototype-based inheritance.

---

### Once you understand prototypes, JavaScript becomes way more powerful and flexible. Keep experimenting, and you’ll be a pro in no time! Happy coding! ❤️