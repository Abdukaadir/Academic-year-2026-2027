# Lesson 1: Introduction to JavaScript

![JavaScript](Images/java%20script%20as%20background%20image.jpg)
# Introduction to JavaScript

A **programming language** is a formal language used to give instructions to a computer. Programming languages can be classified by how they are executed:

- **Compiled languages:** Source code is translated into machine code before execution. Examples: C, C++, Rust.
- **Interpreted languages:** Code is processed and executed at runtime. Examples: traditionally Python, PHP, Ruby.
- **JIT-compiled languages:** Modern engines combine interpretation with Just-In-Time compilation. JavaScript uses this approach.

## ECMAScript and JavaScript

**ECMA** stands for **European Computer Manufacturers Association**, an organization now known as **Ecma International**. It develops and maintains standards for information and communication technologies.

**ECMAScript (ES)** is the standardized specification that defines the core features of JavaScript. **JavaScript is an implementation of the ECMAScript standard.** In simple terms, ECMAScript defines the rules, while JavaScript implements those rules.


## 1.1 What Exactly Is JavaScript?

**Goal:** Build a clear picture of what JavaScript is and what it's capable of.

JavaScript is a high-level, interpreted programming language that follows the ECMAScript standard. Alongside HTML and CSS, it's one of the three pillars the modern web is built on — and of the three, it's the one responsible for behavior and interactivity rather than structure or style.

![How HTML, CSS, and JavaScript compare](Images/comare%20html,%20css%20and%20java%20script%20image.jpg)


## Brief History

- **1995:** Brendan Eich created JavaScript at Netscape.
- **1995:** JavaScript was introduced in Netscape Navigator.
- **1997:** ECMAScript 1 (ES1) was standardized.
- **1999:** ECMAScript 3 (ES3) was released.
- **2009:** ECMAScript 5 (ES5) introduced major improvements.
- **2015:** ECMAScript 2015 (ES6) introduced `let`, `const`, arrow functions, classes, modules, and other modern features.
- **2016–Present:** ECMAScript moved to regular annual releases.

Today, JavaScript is used for frontend, backend, mobile, desktop, and full-stack development.

### What Makes JavaScript, JavaScript

- **It's interpreted, not compiled.** Code runs line by line as the browser (or engine) reads it, rather than being compiled into machine code ahead of time.
- **It's dynamically typed.** You don't declare a variable's type up front — JavaScript works out what kind of value it's holding while the program is running.
- **It's event-driven.** Clicks, key presses, mouse movement, scrolling — JavaScript's whole design revolves around reacting to things the user does.
- **It's prototype-based.** Rather than relying purely on classical class hierarchies, objects can inherit properties and methods directly from other objects via prototypes.

## 1.2 Where Does JavaScript Actually Get Used?

**Goal:** Understand just how far JavaScript's reach extends — from the browser tab you're reading this in, to servers, phones, games, and even physical hardware.

### Client-Side Web Development
This is JavaScript's home turf. It's what lets a page update itself, validate a form, or respond to a click — all without forcing a full reload.

- **Form validation** — catching bad input before the form is ever submitted.
- **Interactive maps** — Google Maps, for instance, leans on JavaScript to handle all of its map interactions.



### Server-Side Development
JavaScript stopped being a browser-only language once **Node.js** arrived, letting it run directly on a server and power scalable network applications.

- **REST APIs** — services that receive and respond to HTTP requests.
- **Real-time applications** — think live chat systems or continuously updating data feeds.



### Internet of Things (IoT)
JavaScript's reach even extends past software, into physical devices — frameworks like **Johnny-Five** let it talk to hardware directly.

- **Home automation** — controlling things like smart lights and thermostats.


### Game Development
Browser-based gaming is powered by JavaScript libraries and engines such as **Phaser** and **Babylon.js**.

- **Browser games** — everything from a simple game of tic-tac-toe to full-blown RPGs.

### Mobile App Development
With frameworks like **React Native**, the same JavaScript skills used for the web can be used to ship genuinely native apps on both iOS and Android.

- **Social apps** — portions of Facebook and Instagram are built using React Native.

---
