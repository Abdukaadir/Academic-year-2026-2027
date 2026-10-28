# JavaScript Loops — The `while` Loop

## 1. Learning Objectives

By the end of this lesson, students should be able to:

- Define a `while` loop in JavaScript.
- Explain when to use a `while` loop instead of a `for` loop.
- Understand the syntax of a `while` loop.
- Trace how a `while` loop executes step by step.
- Avoid infinite loops.
- Relate `while` loops to real-life situations.

## 2. Introduction to the `while` Loop

In the previous lesson, we used the `for` loop when we knew how many times to repeat an action. But what if we do **not** know how many times the code should run?

Imagine you are a lecturer and you keep asking a student to enter a password **until** the correct password is typed. You do not know whether the student will need 1 attempt or 10 attempts.

Or imagine you save money every month **until** you reach 1000 dollars. You do not know in advance how many months it will take.

In situations like these, we use a `while` loop.

## 3. Definition of a `while` Loop

A **`while` loop** is a control structure that repeats a block of code **as long as** a specified condition is `true`. The condition is checked **before** each repetition.

If the condition is `false` from the beginning, the code inside the loop never runs.

## 4. Syntax of a `while` Loop

```javascript
while (condition) {
    // Code to execute repeatedly
}
```

A `while` loop is built from the following parts:

| Part | Purpose | Example |
|---|---|---|
| Initialization | Created **before** the loop to prepare the variable | `let i = 1;` |
| Condition | Determines whether the loop continues | `i <= 5` |
| Update | Changes the variable **inside** the loop body | `i++` |

> **Important:** Unlike the `for` loop, the initialization and the update are **not** written in the loop header. We must write them ourselves.

### Example

```javascript
let i = 1;

while (i <= 5) {
    console.log(i);
    i++;
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

## 5. How Does It Work?

1. `let i = 1;` creates the counter before the loop starts.
2. `i <= 5` is checked. If it is `true`, the loop body runs.
3. `console.log(i)` prints the current value.
4. `i++` increases the counter by 1.
5. The program returns to the condition and checks it again.
6. When `i` becomes 6, `6 <= 5` is `false`, so the loop stops.

### Tracing Table

| Iteration | Value of `i` | Condition `i <= 5` | Output |
|---|---|---|---|
| 1 | 1 | true | 1 |
| 2 | 2 | true | 2 |
| 3 | 3 | true | 3 |
| 4 | 4 | true | 4 |
| 5 | 5 | true | 5 |
| — | 6 | false | Loop stops |

## 6. Comparing `for` and `while`

The same task can be written with both loops.

**Using `for`:**

```javascript
for (let i = 1; i <= 5; i++) {
    console.log("Hello");
}
```

**Using `while`:**

```javascript
let i = 1;

while (i <= 5) {
    console.log("Hello");
    i++;
}
```

| Feature | `for` loop | `while` loop |
|---|---|---|
| Best used when | The number of repetitions is known | The number of repetitions is not known in advance |
| Initialization | Inside the loop header | Before the loop |
| Update | Inside the loop header | Inside the loop body |
| Condition checked | Before each iteration | Before each iteration |

## 7. Real-Life Examples of a `while` Loop

### Example A: Countdown

A lecturer counts down the last 5 seconds of an exam.

```javascript
let seconds = 5;

while (seconds > 0) {
    console.log(seconds);
    seconds--;
}

console.log("Time is up!");
```

**Output:**

```text
5
4
3
2
1
Time is up!
```

### Example B: Saving Money

A student saves 100 dollars each month and wants to reach at least 500 dollars.

```javascript
let savings = 0;
let month = 0;

while (savings < 500) {
    savings = savings + 100;
    month++;
    console.log("Month " + month + ": " + savings + " dollars");
}
```

**Output:**

```text
Month 1: 100 dollars
Month 2: 200 dollars
Month 3: 300 dollars
Month 4: 400 dollars
Month 5: 500 dollars
```

### Example C: Calculating a Total

A student wants to add the numbers from 1 to 5.

```javascript
let i = 1;
let total = 0;

while (i <= 5) {
    total = total + i;
    i++;
}

console.log("Total:", total);
```

**Output:**

```text
Total: 15
```

### Example D: Asking the User Until the Input Is Valid

The program keeps asking until the user enters a mark between 0 and 100.

```javascript
let mark = Number(prompt("Enter a mark (0 - 100):"));

while (mark < 0 || mark > 100) {
    mark = Number(prompt("Invalid mark. Enter a mark (0 - 100):"));
}

console.log("Your mark is " + mark);
```

Here we do not know how many times the user will enter a wrong value, so a `while` loop is the right choice.

## 8. Infinite Loops

An **infinite loop** is a loop that never stops because its condition never becomes `false`.

### Example of a Mistake

```javascript
let i = 1;

while (i <= 5) {
    console.log(i);
    // i++ is missing!
}
```

Because `i` never changes, `i <= 5` stays `true` forever, and the program keeps printing `1`.

### How to Avoid Infinite Loops

1. Always **update** the variable used in the condition.
2. Make sure the update moves the variable **toward** making the condition `false`.
3. Check the condition carefully. For example, `i--` with `i <= 5` and `i` starting at 1 will never stop.

> If your program freezes in the browser, close the tab or stop the program, then check the loop condition and update.

## 9. Additional Examples

### 9.1 `while` with Arrays

```javascript
let subjects = ["JavaScript", "Database", "Networking", "Mathematics"];
let i = 0;

while (i < subjects.length) {
    console.log(subjects[i]);
    i++;
}
```

**Output:**

```text
JavaScript
Database
Networking
Mathematics
```

Remember that array indexes start at `0`, so we use `i < subjects.length`, not `i <= subjects.length`.

### 9.2 `while` with an `if` Condition: Print Even Numbers

```javascript
let i = 1;

while (i <= 10) {
    if (i % 2 === 0) {
        console.log(i);
    }
    i++;
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

### 9.3 Finding the First Failing Mark

```javascript
let marks = [70, 85, 45, 90, 30];
let i = 0;

while (i < marks.length && marks[i] >= 50) {
    i++;
}

if (i < marks.length) {
    console.log("First failing mark is " + marks[i] + " at index " + i);
} else {
    console.log("All students passed.");
}
```

**Output:**

```text
First failing mark is 45 at index 2
```

The loop stops as soon as it finds a mark below 50.

### 9.4 Counting the Digits of a Number

```javascript
let number = 4721;
let count = 0;

while (number > 0) {
    number = Math.floor(number / 10);
    count++;
}

console.log("Number of digits:", count);
```

**Output:**

```text
Number of digits: 4
```

Each repetition removes the last digit by dividing by 10.

## 10. Student Practice Exercises

1. Write a `while` loop that prints numbers from 1 to 20.
2. Write a `while` loop that prints even numbers from 2 to 30.
3. Write a `while` loop that prints numbers from 10 down to 1.
4. Write a `while` loop that calculates the total of numbers from 1 to 100.
5. Create an array of five student names and use a `while` loop to display each name.
6. Use a `while` loop and an `if` statement to print numbers from 1 to 30 that are divisible by 3.
7. Write a program that keeps asking the user to enter a number until the user enters a positive number.
8. Find and fix the mistake:

```javascript
let i = 10;

while (i > 0) {
    console.log(i);
    i++;
}
```

---

# JavaScript Loops — The `do...while` Loop

## 11. Learning Objectives

By the end of this lesson, students should be able to:

- Define a `do...while` loop in JavaScript.
- Understand the syntax of a `do...while` loop.
- Explain the difference between `while` and `do...while`.
- Identify situations where the code must run at least once.
- Relate `do...while` loops to real-life situations.

## 12. Introduction to the `do...while` Loop

Imagine a lecturer enters the classroom. The lecturer **must** greet the students at least once, and then decide whether to continue the lecture.

Or think of an ATM menu. The menu must be displayed **at least once** so the user can choose an option. Only after that, the program checks whether the user wants to continue.

With a `while` loop, if the condition is false at the start, the code never runs. A `do...while` loop solves this: it runs the code **first**, then checks the condition.

## 13. Definition of a `do...while` Loop

A **`do...while` loop** is a control structure that executes a block of code **at least once**, and then repeats it as long as a specified condition is `true`. The condition is checked **after** each repetition.

## 14. Syntax of a `do...while` Loop

```javascript
do {
    // Code to execute at least once
} while (condition);
```

| Part | Purpose | Example |
|---|---|---|
| `do` block | Code that runs first, then repeats | `console.log(i); i++;` |
| Condition | Checked **after** the block runs | `i <= 5` |
| Update | Changes the variable inside the block | `i++` |

> **Important:** Do not forget the semicolon `;` after `while (condition)`.

### Example

```javascript
let i = 1;

do {
    console.log(i);
    i++;
} while (i <= 5);
```

**Output:**

```text
1
2
3
4
5
```

## 15. How Does It Work?

1. `let i = 1;` creates the counter.
2. The code inside `do { }` runs first and prints `1`.
3. `i++` increases the counter to 2.
4. `i <= 5` is checked **after** the block.
5. If the condition is `true`, the loop repeats. If it is `false`, the loop stops.
6. The loop stops when `i` becomes 6.

## 16. Difference Between `while` and `do...while`

Look at what happens when the condition is false from the beginning.

**Using `while`:**

```javascript
let i = 10;

while (i <= 5) {
    console.log("Hello from while");
    i++;
}
```

**Output:**

```text
(no output)
```

**Using `do...while`:**

```javascript
let i = 10;

do {
    console.log("Hello from do...while");
    i++;
} while (i <= 5);
```

**Output:**

```text
Hello from do...while
```

The `do...while` loop ran **once**, even though `10 <= 5` is `false`.

| Feature | `while` loop | `do...while` loop |
|---|---|---|
| When the condition is checked | **Before** the loop body | **After** the loop body |
| Minimum number of executions | 0 times | At least 1 time |
| Semicolon after the condition | Not required | Required |
| Best used when | The code may not need to run at all | The code must run at least once |

## 17. Real-Life Examples of a `do...while` Loop

### Example A: Displaying a Menu

```javascript
let choice;

do {
    choice = prompt("Menu:\n1. View marks\n2. View schedule\n3. Exit\nEnter your choice:");
    console.log("You selected option " + choice);
} while (choice !== "3");

console.log("Goodbye!");
```

The menu is displayed at least once, and it keeps appearing until the user chooses `3`.

### Example B: Password Check

```javascript
let password;

do {
    password = prompt("Enter the password:");
} while (password !== "12345");

console.log("Access granted.");
```

The user must be asked for the password at least once.

### Example C: Validating Input

```javascript
let age;

do {
    age = Number(prompt("Enter your age (1 - 100):"));
} while (age < 1 || age > 100);

console.log("Your age is " + age);
```

### Example D: Calculating a Total

A student wants to add the numbers from 1 to 5.

```javascript
let i = 1;
let total = 0;

do {
    total = total + i;
    i++;
} while (i <= 5);

console.log("Total:", total);
```

**Output:**

```text
Total: 15
```

### Example E: Adding Numbers Until the User Enters 0

```javascript
let number;
let sum = 0;

do {
    number = Number(prompt("Enter a number (0 to stop):"));
    sum = sum + number;
} while (number !== 0);

console.log("Sum:", sum);
```

## 18. Additional Examples

### 18.1 `do...while` with an Array

```javascript
let subjects = ["JavaScript", "Database", "Networking"];
let i = 0;

do {
    console.log(subjects[i]);
    i++;
} while (i < subjects.length);
```

**Output:**

```text
JavaScript
Database
Networking
```

> **Warning:** If the array is empty, `subjects[0]` is `undefined`, but the loop still runs once. For arrays that may be empty, a `while` or `for` loop is safer.

### 18.2 `do...while` with an `if` Condition: Pass or Fail

```javascript
let marks = [35, 72, 48, 90, 55];
let i = 0;

do {
    if (marks[i] >= 50) {
        console.log(marks[i] + " - Pass");
    } else {
        console.log(marks[i] + " - Fail");
    }
    i++;
} while (i < marks.length);
```

**Output:**

```text
35 - Fail
72 - Pass
48 - Fail
90 - Pass
55 - Pass
```

### 18.3 Rolling a Dice Until We Get 6

```javascript
let dice;
let attempts = 0;

do {
    dice = Math.floor(Math.random() * 6) + 1;
    attempts++;
    console.log("Attempt " + attempts + ": " + dice);
} while (dice !== 6);

console.log("You got a 6 after " + attempts + " attempts.");
```

The dice must be rolled at least once, and we do not know how many rolls are needed.

## 19. Student Practice Exercises

1. Write a `do...while` loop that prints numbers from 1 to 10.
2. Write a `do...while` loop that prints numbers from 10 down to 1.
3. Write a `do...while` loop that prints `"Welcome to JavaScript"` five times.
4. Write a program that asks the user to enter a number between 1 and 10 and keeps asking until the number is valid.
5. Write a `do...while` loop that calculates the total of numbers from 1 to 50.
6. Create an array of five numbers and use a `do...while` loop to display each number.
7. Write a program that displays a menu with three options and repeats until the user chooses to exit.
8. Predict the output without running the code:

```javascript
let x = 20;

do {
    console.log("x is " + x);
    x++;
} while (x < 10);
```

---

# Comparing the Three Basic Loops

## 20. Summary Table

| Feature | `for` | `while` | `do...while` |
|---|---|---|---|
| Condition checked | Before each iteration | Before each iteration | After each iteration |
| Minimum executions | 0 | 0 | 1 |
| Best used when | Number of repetitions is known | Number of repetitions is unknown | Code must run at least once |
| Initialization | In the loop header | Before the loop | Before the loop |
| Update | In the loop header | Inside the loop body | Inside the loop body |
| Typical use | Counting, arrays | Waiting for a condition | Menus, input validation |

### Syntax Review

```javascript
// for loop
for (let i = 1; i <= 5; i++) {
    console.log(i);
}

// while loop
let j = 1;
while (j <= 5) {
    console.log(j);
    j++;
}

// do...while loop
let k = 1;
do {
    console.log(k);
    k++;
} while (k <= 5);
```

## 21. Which Loop Should I Use?

Ask yourself these questions:

1. **Do I know exactly how many times to repeat?** → Use `for`.
2. **Do I repeat until something happens, and it might not need to run at all?** → Use `while`.
3. **Must the code run at least once before checking the condition?** → Use `do...while`.

## 22. Summary

- **`while` loop:** checks the condition first, then runs the code. It may run 0 times.
- **`do...while` loop:** runs the code first, then checks the condition. It always runs at least once.
- Always **initialize** the variable before the loop and **update** it inside the loop.
- A missing or incorrect update causes an **infinite loop**.
- Remember the semicolon after `while (condition)` in a `do...while` loop.
- In an index-based array loop, use `i < array.length`, not `i <= array.length`.

## 23. Mixed Review Exercises

1. Write the same program (print numbers from 1 to 10) using `for`, `while`, and `do...while`.
2. Explain in your own words why `do...while` is better than `while` for displaying a menu.
3. Write a program that asks for a password using the loop of your choice, and explain why you chose it.
4. Write a program that counts how many numbers in an array are greater than 50, using a `while` loop.
5. Find the mistakes in the following code:

```javascript
let i = 1;

do {
    console.log(i);
} while (i <= 5)
```

**Next lesson:** The `break` and `continue` statements, and the `for...of`, `for...in`, and `forEach()` iteration techniques.
