# javascript101
In preparation for my interviews

An introduction to JavaScript concepts, including its history, features, and practical examples.

---

### **What is JavaScript?**
- **Definition**: JavaScript is a versatile scripting language used for web development. It enables interactivity on web pages, such as dynamic content, animations, and user interactions.
- **Origins**: Created by Brendan Eich in 1993 at Netscape, it was designed to make static HTML web pages interactive.
- **Popularity**: Today, JavaScript is one of the most widely used programming languages, standardized as ECMAScript and supported by all web browsers.

---

### **JavaScript Basics**
1. **Adding JavaScript to a Web Page**:
   - Use the `<script>` tag inside an HTML file.
   - Example:
     ```html
     <script>
       console.log("Hello, World!");
     </script>
     ```
   - You can also include external JavaScript files using the `src` attribute.

2. **Variable Declarations**:
   - **`let`**: Block-scoped, allows reassignment.
     ```javascript
     let x = 10;
     x = 20;
     console.log(x); // Output: 20
     ```
   - **`const`**: Block-scoped, does not allow reassignment.
     ```javascript
     const y = 30;
     // y = 40; // Error: Assignment to constant variable
     ```
   - **`var`**: Function-scoped and hoisted (legacy feature, avoid using).
     ```javascript
     var z = 50;
     console.log(z); // Output: 50
     ```

3. **Semicolons**:
   - Optional in JavaScript, but their use can prevent ambiguities.

---

### **Key JavaScript Concepts**
1. **Dynamic Typing**:
   - Variables do not require explicit type definitions.
   - Example:
     ```javascript
     let value = 10; // Initially a number
     value = "Hello"; // Now a string
     ```

2. **Functions**:
   - Functions can take arguments, return values, and even be assigned to variables.
     ```javascript
     function add(a, b) {
       return a + b;
     }
     console.log(add(2, 3)); // Output: 5
     ```
   - Arrow functions:
     ```javascript
     const multiply = (a, b) => a * b;
     console.log(multiply(2, 3)); // Output: 6
     ```
     Note: you cannot use 'this' keyword when using arrow functions. Arrow functions does not have its own arguments object as well.
     **When to Use Arrow Functions**
     - Simpler Syntax: For concise, single-purpose functions.
     - Avoiding this Confusion: In callbacks or event handlers where you want to preserve the outer this.
     - Functional Programming: Great for array methods like map, filter, and reduce.

3. **Objects and Arrays**:
   - Objects hold key-value pairs:
     ```javascript
     const person = { name: "Alice", age: 25 };
     console.log(person.name); // Output: Alice
     ```
   - Arrays store ordered collections:
     ```javascript
     const numbers = [1, 2, 3];
     console.log(numbers[0]); // Output: 1
     ```

4. **Prototypes and Classes**:
   - JavaScript uses prototypal inheritance, with `class` as syntactic sugar.
     ```javascript
     class Person {
       constructor(name) {
         this.name = name;
       }
       greet() {
         console.log(`Hello, ${this.name}`);
       }
     }
     const alice = new Person("Alice");
     alice.greet(); // Output: Hello, Alice
     ```
---

### **Implicit vs. Explicit Return in JavaScript**

In JavaScript, the distinction between **implicit** and **explicit return** lies in how the function returns a value. This behavior is particularly relevant for **arrow functions**.

---

### **1. Explicit Return**
- In an **explicit return**, the `return` keyword is explicitly used to specify the value to return.
- The function does not return anything unless `return` is explicitly stated.

**Example**:
```javascript
const add = (a, b) => {
  return a + b; // Explicit return
};

console.log(add(2, 3)); // Output: 5
```

**Explanation**:
- The function body is enclosed in `{}` (block syntax).
- The `return` keyword must be used to return a value.

---

### **2. Implicit Return**
- In an **implicit return**, the value is automatically returned without using the `return` keyword.
- This is possible only if the function body is written as a single expression without `{}`.

**Example**:
```javascript
const add = (a, b) => a + b; // Implicit return

console.log(add(2, 3)); // Output: 5
```

**Explanation**:
- The function body is written as a single-line expression.
- The value of the expression (`a + b`) is implicitly returned.

---

### **Key Differences**

| Feature             | Explicit Return                  | Implicit Return                   |
|---------------------|----------------------------------|-----------------------------------|
| **Syntax**           | Requires `return` keyword       | Does not require `return` keyword |
| **Function Body**    | Enclosed in `{}` (block syntax) | Single expression (no `{}`)       |
| **Use Case**         | Multi-line logic or statements  | Simple, concise logic             |

---

### **When to Use Which**
- Use **explicit return** when the function has multiple lines or complex logic:
  ```javascript
  const multiplyAndLog = (a, b) => {
    console.log(`Multiplying ${a} and ${b}`);
    return a * b; // Explicit return is needed for multi-line body
  };
  ```

- Use **implicit return** for short, concise functions with a single expression:
  ```javascript
  const square = x => x * x; // Implicit return
  ```

---

### **Common Pitfalls**
1. **Using `{}` with Implicit Return**:
   - If you mistakenly use `{}` with an implicit return, JavaScript won't return anything.
   ```javascript
   const multiply = (a, b) => { a * b }; // No return, undefined
   console.log(multiply(2, 3)); // Output: undefined
   ```

2. **Correct Usage**:
   - Either use implicit return without `{}`:
     ```javascript
     const multiply = (a, b) => a * b;
     ```
   - Or use explicit return with `{}`:
     ```javascript
     const multiply = (a, b) => {
       return a * b;
     };
     ```

---

### **Advanced Concepts**
1. **Event Loop**:
   - JavaScript uses a non-blocking event loop for asynchronous operations.
   - Example: Using `setTimeout`:
     ```javascript
     console.log("Start");
     setTimeout(() => console.log("Async Task"), 1000);
     console.log("End");
     // Output: Start, End, Async Task
     ```

2. **Promises and `async/await`**:
   - Promises handle asynchronous tasks.
     ```javascript
     fetch("https://api.example.com/data")
       .then(response => response.json())
       .then(data => console.log(data))
       .catch(error => console.error(error));
     ```
   - `async/await` simplifies promise-based code.
     ```javascript
     async function fetchData() {
       try {
         const response = await fetch("https://api.example.com/data");
         const data = await response.json();
         console.log(data);
       } catch (error) {
         console.error(error);
       }
     }
     fetchData();
     ```

3. **Modules**:
   - JavaScript supports modular development.
     ```javascript
     // math.js
     export const add = (a, b) => a + b;

     // main.js
     import { add } from "./math.js";
     console.log(add(2, 3)); // Output: 5
     ```

---

### **Tools and Frameworks**
- **NPM**: A package manager for JavaScript libraries and dependencies.
- **Module Bundlers**: Tools like Webpack or Vite optimize JavaScript files for deployment.
- **Node.js**: A runtime that allows JavaScript to run on the server.

---

### **Modern JavaScript Features**
1. **Dynamic Imports**:
   - Load JavaScript modules only when needed.
     ```javascript
     import("./module.js").then(module => module.someFunction());
     ```

2. **Reactivity**:
   - Frameworks like React make the UI reactive, automatically updating when data changes.

---

Thanks to [101 JavaScript Concepts](https://www.youtube.com/watch?v=lkIFF4maKMU) for the visuals!
