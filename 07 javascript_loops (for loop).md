# JavaScript Loops

## 1. Learning Objectives

By the end of this lesson, students should be able to:

- Define a loop in JavaScript.
- Explain why loops are needed.
- Identify the most common types of loops.
- Understand the syntax of a `for` loop.
- Relate loops to real-life situations.

## 2. Introduction to Loops

Imagine you are a lecturer and you want to print the names of five students. You could write:

```javascript
console.log("Ahmed");
console.log("Amina");
console.log("Mohamed");
console.log("Fatima");
console.log("Hassan");
```

This works, but what if you have 100 students? Would you write 100 `console.log()` statements?

That would take time and make your code unnecessarily long. Instead, we can use a loop to repeat instructions automatically.

## 3. Definition of a Loop

A **loop** is a programming structure that allows us to execute a block of code repeatedly, as long as a specified condition is satisfied or for a specified number of repetitions.

For example:

```javascript
for (let i = 1; i <= 5; i++) {
    console.log("Hello, students!");
}
```

**Output:**

```text
Hello, students!
Hello, students!
Hello, students!
Hello, students!
Hello, students!
```

The statement `console.log()` executes five times without us writing it five times.

## 4. Why Do We Need Loops?

Loops are important because they help programmers:

1. **Reduce repetitive code** — avoid writing the same instructions many times.
2. **Save time** — repeat operations automatically.
3. **Process large amounts of data** — for example, hundreds of student records.
4. **Automate tasks** — repeat a task until a condition is met.
5. **Work with arrays** — process each element in a collection.
6. **Build interactive applications** — repeatedly display menus or ask for user input.

### Example: Printing Numbers from 1 to 100

Without a loop, we would need many separate statements. With a loop:

```javascript
for (let i = 1; i <= 100; i++) {
    console.log(i);
}
```

This short program prints every number from 1 to 100.

## 5. Most Common Types of Loops in JavaScript

JavaScript provides several ways to repeat instructions. The three fundamental loop structures are:

### 1. `for` Loop

Used when you know how many times you want to repeat an operation, such as printing numbers from 1 to 10.

### 2. `while` Loop

Repeats a block of code while a condition is `true`. It is useful when the number of repetitions is not known in advance.

### 3. `do...while` Loop

Executes the code block at least once, then checks the condition to decide whether to repeat.

Other iteration techniques include `for...of`, `for...in`, and the array method `forEach()`. We will cover those after learning the three fundamental loops.

## 6. The `for` Loop

### 6.1 Definition

A **`for` loop** is a control structure that repeats a block of code while its condition remains `true`. It is especially useful when the number of repetitions is known or controlled by a counter.

### 6.2 Syntax of a `for` Loop

```javascript
for (initialization; condition; update) {
    // Code to execute repeatedly
}
```

A `for` loop has three main parts:

| Part | Purpose | Example |
|---|---|---|
| Initialization | Creates or initializes the counter | `let i = 1` |
| Condition | Determines whether the loop continues | `i <= 5` |
| Update | Changes the counter after each iteration | `i++` |

### 6.3 Example

```javascript
for (let i = 1; i <= 5; i++) {
    console.log(i);
}
```

**Output:**

```text
1
2
3
4
5
```

### 6.4 How Does It Work?

1. `let i = 1` initializes the counter at 1.
2. `i <= 5` checks whether the counter is less than or equal to 5.
3. `console.log(i)` prints the current value.
4. `i++` increases the counter by 1.
5. The condition is checked again. The loop stops when `i` becomes 6 because `6 <= 5` is `false`.

### 6.5 Real-Life Examples of a `for` Loop

#### Example A: Taking Attendance

A lecturer wants to call out 30 students from a numbered attendance list.

```javascript
for (let student = 1; student <= 30; student++) {
    console.log("Calling student number " + student);
}
```

#### Example B: Counting Products

A shop has 10 products to display by their numbers.

```javascript
for (let product = 1; product <= 10; product++) {
    console.log("Product number " + product);
}
```

#### Example C: Calculating a Total

A student wants to add the numbers from 1 to 5.

```javascript
let total = 0;

for (let i = 1; i <= 5; i++) {
    total = total + i;
}

console.log("Total:", total);
```

**Output:**

```text
Total: 15
```

The loop adds `1 + 2 + 3 + 4 + 5`.

## 7. Student Practice Exercises

1. Write a `for` loop that prints numbers from 1 to 20.
2. Write a `for` loop that prints even numbers from 2 to 30.
3. Write a `for` loop that prints `"Welcome to JavaScript"` ten times.

---

**Next lesson:** The `while` loop — definition, syntax, execution, and real-life examples.
