# Understanding JavaScript Fundamentals 

## a. What is JavaScript, and where is it used 

JavaScript (JS) is a programming language used to build web pages and make them interactive. 
Things like button clicks, animations, updating content without refreshing the page is possible because of JavaScript.

With the introduction of Node.js , JavaScript can run outside of web browsers including servers, on IoT devices etc , making it a go to language for full-stack development .

**Uses of JavaScript**
- Frontend (Interactive websites)
- Backend (Server)
- Mobile apps (React Native uses JS to build android apps) etc.


## b. JavaScript execution flow

JavaScript is a synchronous single-threaded language, everything in JS happens inside an Execution Context .

### Execution Context
Whenever JavaScript code is executed, an Execution Context is created — 
the first one is called the Global Execution Context (GEC).

### Two Phases of Execution Context Creation

**1. Memory Creation Phase**
- Memory is allocated to all variables and functions in the scope
- Variables are set to undefined
- Functions are stored entirely (the whole function code)

**2. Code Execution Phase**
- Code runs line by line
- Variables get their actual assigned values
- Functions execute when invoked

### Call Stack
The Call Stack keeps track of the order in which execution contexts run:
- The Global Execution Context is pushed first
- Each function call pushes a new execution context on top
- When a function finishes, its execution context is popped off
- At the end, the Global Execution Context is also removed 

## c. Running JavaScript:

### 1. Browser
Every browser has a built-in JavaScript engine (Eg :Chrome uses V8) that can run JS code directly. This is how websites become interactive — things like button clicks, form validation, animations all run through this.

### 2. Node.js
Node.js is a specialized runtime environment that lets you execute that exact same language on a server, directly on your computer/server via the command line/terminal.

## d. Understanding compilation vs interpretation 

**Compiled languages** 
- Code is translated entirely into machine code before running, by a compiler
- Produces a separate executable file
- Runs fast since translation is already done
- Must recompile every time the code changes
- Eg: C++ , Rust 

**Interpreted languages** 
- Code is read and executed line by line by an interpreter
- No separate compilation step - just run the file directly
- slower than compiled languages
- Eg: Python 

#### JS
JavaScript is technically a hybrid. Modern engines like V8 use JIT (Just-In-Time) compilation - they compile JS into optimized machine code while it's running, rather than fully beforehand (like C++) or purely line-by-line (like Python).

