---
title: "Understanding Execution Context in JavaScript: A Complete Guide with Examples & Call Stack Insights"
seoTitle: "JavaScript Execution Context Explained"
seoDescription: "Learn about the JavaScript execution context, call stack, creation processes, and key environment insights to improve coding skills"
datePublished: Tue May 06 2025 16:40:21 GMT+0000 (Coordinated Universal Time)
cuid: cmacqjt0l000409kyfq2seupn
slug: understanding-execution-context-in-javascript-a-complete-guide-with-examples-and-call-stack-insights
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/qaedPly-Uro/upload/86ee90082cfce78302dd78d0071dc736.jpeg
tags: javascript, callstack, execution-context, javascript-fundamentals, global-context-javascript

---

# JavaScript Execution Context

An **execution context** is the internal environment in which JavaScript code is evaluated and executed. In simpler terms, it’s like a *container* or *box* that holds everything the engine needs to run a piece of code. The [ECMAScript spec](https://chatgpt.com/c/6819a429-2c40-8006-83d6-c671c7f041c7#refs) describes it as a mechanism to track runtime evaluation of code. In practice, an execution context includes the current code to execute, its scope and variables, and the value of `this`. For example, one expert explains that in layman’s terms an execution context “roughly equates to the *environment* a function executes in: variable scope (and scope chain), function arguments, and the value of `this`”.

## Creation and Lifecycle

JavaScript creates a **global execution context** when a script first starts. This happens even if your code is empty – the engine always makes one global context. The creation process has two phases:

* **Creation Phase:** The engine scans the code and allocates memory. It sets up the Global Object (in browsers, `window`) and the `this` binding (initially pointing to the global object). All declared variables and functions are placed into memory: functions are stored and variable names exist with the value `undefined`.
    
* **Execution Phase:** The code runs line by line. Variables are assigned real values and functions may be invoked. When a function is called, a **new function execution context** is created on top of the stack (see Call Stack below).
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1746549595640/d14243e6-0ec2-47d4-b9c3-04b454f2ace9.png align="center")
    

*Figure: Example Global Execution Context at* ***creation*** *phase (memory view).* When a script loads, the engine builds the Global Execution Context. In the **creation phase**, it allocates space for all top-level variables and functions (initially `undefined`) and establishes the global object and `this` binding. In the illustration above (from a simple example), variables `a`, `sum1`, and `sum2` exist but are `undefined`, while the function `add` is registered in memory. In the subsequent **execution phase**, the engine will assign actual values (e.g. `a=20`) and run code.

Every time a function is invoked, the engine creates a new **Function Execution Context**. That function’s context also has a creation phase (allocating space for its local variables and parameters) and an execution phase (running the function body). After the function finishes (hits `return` or ends), its context is **popped** off the stack (destroying its local environment) and control returns to the previous context.

## Types of Execution Contexts

JavaScript defines three main execution context types:

* **Global Execution Context (GEC):** This is the base context for any script. There is exactly one global context per program (per JavaScript realm). It contains all global variables and functions, plus the global object (`window` or `global`) and the initial `this` value (which is the global object in non-strict mode).
    
* **Function Execution Context:** Created whenever a function is called. Each call to a function – even recursive calls – gets its own execution context on the stack. The function’s local variables, parameters, and inner functions reside in this context. The value of `this` inside the context depends on how the function is called (e.g. method call, `new`, or default global).
    
* **Eval Execution Context:** Rarely used, this is created when code is run via `eval()`. It behaves much like a function context but executes string code in its own environment. (Because `eval` is discouraged for security reasons, it’s uncommon in practice.).
    

*(Some sources also mention a fourth type for ES6 modules, but for traditional scripts the above three cover most cases.)*

## Contents of an Execution Context

Each execution context is essentially a set of data structures holding the environment for code execution. Key components include:

* **Lexical Environment:** An object that holds the current scope’s variables and their values. It includes an *environment record* (mapping names to values) and a reference to an *outer* (parent) lexical environment. The *scope chain* is formed by linking these environments from inner to outer, so a function can access variables in its enclosing scopes. For the global context, the outer reference is `null`.
    
* **Variable Environment:** Similar to the lexical environment but specifically holds `var` declarations. In modern implementations, lexical and variable environments are often the same object at first. They track function declarations, variables, and in ES6, `let`/`const` and class bindings in that context.
    
* `this` Binding: Each context fixes the value of `this` inside that environment. In the Global Context, `this` is the global object. In a Function Context, `this` may be the global object (if the function is called normally), `undefined` (in strict mode), or some specific object if the function was called as a method or with `call`/`apply`.
    
* **Arguments Object:** In a function context, there is also an `arguments` object that holds the passed parameters.
    
* **Code and Execution State:** Internally, the context keeps track of *where* in the code it is (especially important for features like generators or async). But for learning purposes, you mainly need to know that all the function’s local data lives here.
    

MDN summarizes the bindings tracked: *“execution context tracks… variables defined with* `var`, `let`, `const`, `function`, `class`, etc., and the `this` reference”. In other words, **all** names (identifiers) available in that context, plus `this`, are recorded.

## Call Stack and Context Management

JavaScript uses a **call stack** (execution stack) to manage execution contexts. This is a LIFO (Last-In-First-Out) stack where the global context starts at the bottom. When a script runs, its global context is pushed first. When a function call occurs, the engine creates a new context for that function and **pushes** it onto the top of the stack. That new context becomes the running context. When the function returns, its context is **popped** off the stack and the previous context resumes as the running context.

For example, consider this code:

```js
function foo(x) {
  const y = 10;
  return x + y;
}
function bar(z) {
  return foo(z * 2);
}
const result = bar(5);
console.log(result);
```

1. **Global Context:** The engine starts by creating the global context. It sees `foo`, `bar`, and `result` declared. Initially, `result` is `undefined`.
    
2. **Call** `bar(5)`: A new Function Context for `bar` is created and pushed onto the stack. In this context, `z` is `5`.
    
3. **Inside** `bar`, call `foo(z*2)`: Evaluate `z * 2` (`10`), then push a new Function Context for `foo`. Now the stack has Global → bar → foo. In the `foo` context, `x=10`.
    
4. **Execute** `foo`: Inside `foo`, it computes `y = 10` (local), then returns `x + y = 20`. The `foo` context is then popped off the stack. Control returns to `bar`.
    
5. **Return to** `bar`: The call to `foo` gave `20`. `bar` returns that value. The `bar` context is popped off the stack.
    
6. **Back to Global:** The return value (20) is assigned to `result`, and `console.log(result)` runs in the global context. Once the script ends, the global context is popped as well (call stack is empty), and execution finishes.
    

MDN describes this stacking process step by step. The key idea: **the call stack holds all active execution contexts, and only the top context is currently running**.

## Real-World Analogy

One way to picture this is a stack of plates in a cafeteria:

* **Each plate = an execution context:** Each function call gets its own “plate” (context) with its own data (variables, parameters).
    
* **Putting a plate on top = calling a function:** When a function is invoked, put a new plate on the stack.
    
* **Taking a plate off = finishing a function:** When the function returns, remove (pop) that top plate, revealing the one beneath (the caller’s context).
    

The *global context* is the bottom plate (and never removed until the program ends). Inside each “plate” (context), you have all the ingredients (variables, scope) needed for that function to run.

## Example Walkthrough

Consider this concrete example to see contexts in action:

```js
var x = 2;
function add(y) {
  var z = x + y;
  return z;
}
var result = add(3);
console.log(result);
```

1. **Global Creation:** Global context is created. Variables `x`, `add`, and `result` are hoisted. Initially `x=undefined`, `add` is the function, and `result=undefined` (before execution).
    
2. **Global Execution:** The engine runs the code: assigns `x = 2`. Now the global context has `x=2`, and the function `add` ready.
    
3. **Function Call (**`add(3)`): A new context for `add` is created on the stack. In this context, the parameter `y` is `3` and a local `z` is prepared (initially `undefined`). The `add` context also has access to the outer (global) lexical environment, so it can see `x=2`.
    
4. `add` Execution: Inside `add`, compute `z = x + y = 2 + 3 = 5`. Then `return z` (value `5`).
    
5. **Return from** `add`: The `add` context is popped off the stack. Control goes back to the global context, and the returned value `5` is assigned to `result`.
    
6. **Global Continues:** Now `result = 5`. The engine executes `console.log(result)`, outputting `5`. After this, the script ends, and the global context is popped off the stack.
    

Throughout this process, you can trace which context is running and what each contains. For example, when inside `add`, the local variables are `y=3` and `z=5`, and `x` comes from the global lexical environment. The **scope chain** ensures `add` finds `x` in the outer context.

## Summary

* **Execution Context:** A container/environment that holds the information needed to run code (scope, variables, `this`).
    
* **Creation:** Global context is created at program start (phase 1: allocate, phase 2: run). Each function call creates a new context.
    
* **Types:** Global, Function, and Eval contexts.
    
* **Contents:** Each context includes a Lexical Environment (scope with variable bindings) and `this` binding (plus arguments for functions).
    
* **Call Stack:** A LIFO stack that tracks contexts. New contexts push on top when functions run, and pop off when functions return.
    

Understanding execution contexts and the call stack is crucial for deeper insights into JavaScript behavior (like hoisting, closures, and `this` binding).

### References

* ECMAScript Specification – Execution Contexts (ECMA-262)
    
* MDN Web Docs – JavaScript execution model
    
* Coralogix Blog – *Understanding the Execution Context in JavaScript*
    
* Prototyp Blog – *What is Execution Context in JavaScript*
    
* StackOverflow discussion – *Execution Context vs Scope*.