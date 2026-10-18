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

# JavaScript Loops — Additional Examples

These sections extend the introductory `for` loop lesson with nested loops, loops with arrays, and loops with `if` conditions.

## 7. Nested Loops

### 7.1 Definition

A **nested loop** is a loop placed inside another loop. For each iteration of the outer loop, the inner loop completes its iterations.

### 7.2 Basic Example

```javascript
for (let i = 1; i <= 3; i++) {
    for (let j = 1; j <= 2; j++) {
        console.log("Outer:", i, "Inner:", j);
    }
}
```

**Output:**

```text
Outer: 1 Inner: 1
Outer: 1 Inner: 2
Outer: 2 Inner: 1
Outer: 2 Inner: 2
Outer: 3 Inner: 1
Outer: 3 Inner: 2
```

**How it works:**

1. The outer loop starts with `i = 1`.
2. The inner loop runs fully for `j = 1` and `j = 2`.
3. The outer loop moves to `i = 2`, and the inner loop runs again.
4. This continues until the outer loop finishes.

### 7.3 Real-Life Example: Classrooms and Students

Imagine a university has three classrooms, and you want to print two student numbers for each classroom.

```javascript
for (let classroom = 1; classroom <= 3; classroom++) {
    for (let student = 1; student <= 2; student++) {
        console.log("Classroom " + classroom + ", Student " + student);
    }
}
```

**Output:**

```text
Classroom 1, Student 1
Classroom 1, Student 2
Classroom 2, Student 1
Classroom 2, Student 2
Classroom 3, Student 1
Classroom 3, Student 2
```

### 7.4 Nested Loop Practice

1. Use nested loops to print three rows, with four stars (`*`) in each row.
2. Use nested loops to display the multiplication tables from 1 to 3, with each table showing multipliers from 1 to 5.

## 8. Loops with Arrays

### 8.1 Why Use a Loop with an Array?

An array stores multiple values in one variable. A loop lets us access each value without writing a separate statement for every element.

### 8.2 Example: Display All Subject Names

```javascript
let subjects = ["JavaScript", "Database", "Networking", "Mathematics"];

for (let i = 0; i < subjects.length; i++) {
    console.log(subjects[i]);
}
```

**Output:**

```text
JavaScript
Database
Networking
Mathematics
```

**How it works:**

- `subjects.length` gives the number of elements in the array.
- Array indexes start at `0`, so the first item is `subjects[0]`.
- Each time the loop runs, `i++` moves to the next index.
- The loop stops when `i` is no longer less than `subjects.length`.

### 8.3 Example: Ask the User to Enter Subjects

```javascript
let subjects = [];
let subjectNumber = Number(prompt("How many subjects did you take?"));

for (let i = 0; i < subjectNumber; i++) {
    let subject = prompt("Enter subject number " + (i + 1));
    subjects.push(subject);
}

console.log("Your subjects are:");

for (let i = 0; i < subjects.length; i++) {
    console.log(subjects[i]);
}
```

The first loop collects the subject names and stores them using `push()`. The second loop displays each stored subject.

### 8.4 Example: Calculate the Total of Array Values

```javascript
let marks = [70, 85, 60, 90];
let total = 0;

for (let i = 0; i < marks.length; i++) {
    total = total + marks[i];
}

console.log("Total marks:", total);
```

**Output:**

```text
Total marks: 305
```

### 8.5 Loop-with-Array Practice

1. Create an array containing five student names and use a loop to display each name.
2. Create an array containing five numbers and use a loop to calculate their total.
3. Create an array of subject names and use a loop to display each subject with its numbered position.

## 9. Loops with `if` Conditions

### 9.1 Why Combine a Loop with an `if` Statement?

A loop can visit every value in a sequence or array. An `if` statement lets the program make a decision about each value. Together, they can find matching values, count results, or display only values that meet a condition.

### 9.2 Example: Print Only Even Numbers

```javascript
for (let i = 1; i <= 10; i++) {
    if (i % 2 === 0) {
        console.log(i);
    }
}
```

**Output:**

```text
2
4
6
8
10
```

The expression `i % 2 === 0` checks whether the number is divisible by 2 without a remainder.

### 9.3 Example: Find Students Who Passed

Assume a mark of 50 or higher is a pass.

```javascript
let marks = [35, 72, 48, 90, 55];

for (let i = 0; i < marks.length; i++) {
    if (marks[i] >= 50) {
        console.log(marks[i] + " - Pass");
    } else {
        console.log(marks[i] + " - Fail");
    }
}
```

**Output:**

```text
35 - Fail
72 - Pass
48 - Fail
90 - Pass
55 - Pass
```

The loop checks each mark. The `if...else` statement decides whether to display `Pass` or `Fail`.

### 9.4 Example: Find Subjects with a Specific Name

```javascript
let subjects = ["JavaScript", "Database", "Networking", "JavaScript"];

for (let i = 0; i < subjects.length; i++) {
    if (subjects[i] === "JavaScript") {
        console.log("JavaScript found at index " + i);
    }
}
```

**Output:**

```text
JavaScript found at index 0
JavaScript found at index 3
```

The loop checks every array element and displays the index whenever the subject is `"JavaScript"`.

### 9.5 Loop-and-Condition Practice

1. Use a loop and an `if` statement to print numbers from 1 to 30 that are divisible by 3.
2. Given an array of marks, display only marks that are 50 or higher.
3. Given an array of numbers, count how many numbers are negative.

## 10. Summary

- **Nested loops:** place one loop inside another loop.
- **Loops with arrays:** use an index and `array.length` to visit array elements.
- **Loops with conditions:** use `if` or `if...else` inside a loop to make decisions about each value.

**Reminder:** In a standard index-based array loop, use `i < array.length` rather than `i <= array.length`. The last valid index is `array.length - 1`.


**Next lesson:** The `while` loop — definition, syntax, execution, and real-life examples.
