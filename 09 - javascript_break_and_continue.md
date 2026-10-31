# JavaScript Loops — `break` and `continue`

## 1. Learning Objectives

By the end of this lesson, students should be able to:

- Define the `break` statement in JavaScript.
- Define the `continue` statement in JavaScript.
- Explain the difference between `break` and `continue`.
- Use `break` to stop a loop early.
- Use `continue` to skip the rest of the current iteration.
- Avoid common mistakes when using these statements.

## 2. Introduction

Sometimes a loop should not always run until its normal condition becomes false.

There are situations where we want to:

- stop the loop immediately, or
- skip the rest of the current loop iteration and move to the next one.

JavaScript gives us two special statements for this:

- `break`
- `continue`

These are very useful when working with loops such as `for`, `while`, and `do...while`.

## 3. The `break` Statement

The `break` statement is used to exit a loop immediately.

When JavaScript reaches `break`, it stops the loop and jumps to the next code after the loop.

### Syntax

```javascript
while (condition) {
    // code
    if (someCondition) {
        break;
    }
    // more code
}
```

### Example A: Stop a Loop Early

```javascript
let i = 1;

while (i <= 10) {
    console.log(i);

    if (i === 5) {
        break;
    }

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

In this example, the loop stops when `i` becomes `5`. Even though the loop condition is still `true`, the `break` statement ends the loop.

### Example B: Search in an Array

```javascript
let marks = [65, 80, 72, 90, 48, 77];
let target = 90;

for (let i = 0; i < marks.length; i++) {
    if (marks[i] === target) {
        console.log("Found 90 at index " + i);
        break;
    }
}
```

**Output:**

```text
Found 90 at index 3
```

Here, as soon as the target value is found, the loop stops.

## 4. How `break` Works

The `break` statement:

1. Stops the current loop immediately.
2. Ignores any remaining code in that loop iteration.
3. Moves control to the code after the loop.

This is useful when a condition is met and we no longer need to keep looping.

## 5. The `continue` Statement

The `continue` statement skips the rest of the current loop iteration and moves to the next one.

Unlike `break`, it does not stop the loop completely. It only skips the remaining code in that iteration.

### Syntax

```javascript
for (let i = 0; i < 10; i++) {
    if (condition) {
        continue;
    }

    // code to run for allowed values
}
```

### Example A: Skip Odd Numbers

```javascript
for (let i = 1; i <= 10; i++) {
    if (i % 2 !== 0) {
        continue;
    }

    console.log(i);
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

The loop continues running, but odd numbers are skipped.

### Example B: Ignore Invalid Marks

```javascript
let marks = [50, 75, -10, 88, 100, 120];

for (let i = 0; i < marks.length; i++) {
    if (marks[i] < 0 || marks[i] > 100) {
        continue;
    }

    console.log("Valid mark: " + marks[i]);
}
```

**Output:**

```text
Valid mark: 50
Valid mark: 75
Valid mark: 88
Valid mark: 100
```

The invalid marks are ignored without stopping the entire loop.

## 6. How `continue` Works

The `continue` statement:

1. Stops the current iteration.
2. Skips the remaining code in the loop body.
3. Moves to the next iteration.

This is useful when we want to ignore some values or conditions while continuing the rest of the loop.

## 7. Comparing `break` and `continue`

| Statement | Effect | Loop continues? |
|---|---|---|
| `break` | Exits the loop completely | No |
| `continue` | Skips the rest of the current iteration | Yes |

### Quick Example

```javascript
for (let i = 1; i <= 5; i++) {
    if (i === 3) {
        break;
    }
    console.log(i);
}
```

**Output:**

```text
1
2
```

```javascript
for (let i = 1; i <= 5; i++) {
    if (i === 3) {
        continue;
    }
    console.log(i);
}
```

**Output:**

```text
1
2
4
5
```

The difference is very important:

- `break` stops the loop.
- `continue` just skips one value.

## 8. Real-Life Examples

### Example A: Stopping at the Correct Password

```javascript
let password = "12345";
let guess = "";

while (guess !== password) {
    guess = prompt("Enter your password:");

    if (guess === password) {
        console.log("Access granted.");
        break;
    }

    console.log("Incorrect password. Try again.");
}
```

The loop stops as soon as the student enters the correct password.

### Example B: Skipping Invalid Input

```javascript
let numbers = [10, 20, -5, 30, 40, 120];

for (let i = 0; i < numbers.length; i++) {
    if (numbers[i] < 0 || numbers[i] > 100) {
        continue;
    }

    console.log("Number accepted: " + numbers[i]);
}
```

This program skips values that are outside the allowed range and keeps processing the valid ones.

### Example C: Counting Only Positive Numbers

```javascript
let values = [5, -2, 8, 0, 12, -7, 15];
let total = 0;

for (let i = 0; i < values.length; i++) {
    if (values[i] <= 0) {
        continue;
    }

    total += values[i];
}

console.log("Total of positive numbers: " + total);
```

**Output:**

```text
Total of positive numbers: 40
```

The loop ignores negative numbers and zero, then continues the calculation.

## 9. Common Mistakes

### Mistake 1: Forgetting to Update the Counter

```javascript
let i = 1;

while (i <= 5) {
    if (i === 3) {
        continue;
    }

    console.log(i);
    // i++ is missing!
}
```

This creates an infinite loop because `i` never changes.

### Mistake 2: Using `break` Instead of `continue`

```javascript
for (let i = 1; i <= 10; i++) {
    if (i % 2 === 0) {
        break;
    }

    console.log(i);
}
```

This stops the loop too early and prints only:

```text
1
```

`break` ends everything. `continue` only skips the current value.

### Mistake 3: Using `break` Outside a Loop

```javascript
if (true) {
    break;
}
```

This is invalid because `break` must be used inside a loop or a `switch` statement.

## 10. Student Practice Exercises

1. Write a `for` loop that prints numbers from 1 to 10, but stops when the number reaches 7.
2. Write a `while` loop that prints even numbers from 1 to 20 and skips the odd numbers using `continue`.
3. Create an array of marks and use `continue` to skip marks below 50.
4. Write a loop that stops when it finds the first negative number in an array.
5. Use `break` in a `do...while` loop to stop after five iterations.
6. Write a program that prints all numbers from 1 to 15 except 6, 9, and 12.
7. Explain the difference between these two code snippets:

```javascript
if (x === 3) {
    break;
}
```

and

```javascript
if (x === 3) {
    continue;
}
```

8. Find and correct the mistake in the following code:

```javascript
let i = 0;

while (i < 5) {
    if (i === 2) {
        continue;
    }
    console.log(i);
    i++;
}
```

## 11. Summary

- `break` exits a loop immediately.
- `continue` skips the rest of the current iteration and moves to the next one.
- `break` stops the loop completely.
- `continue` does not stop the loop; it only skips part of it.
- Always make sure the loop variable changes when using `continue` so the loop does not become infinite.

## 12. Quick Review

```javascript
for (let i = 1; i <= 10; i++) {
    if (i === 4) {
        break;
    }

    if (i % 2 === 0) {
        continue;
    }

    console.log(i);
}
```

**Output:**

```text
1
3
```

### Why?

- `1` is printed.
- `2` is skipped with `continue`.
- `3` is printed.
- `4` triggers `break`, so the loop stops.

## 13. Final Note

The `break` and `continue` statements are simple but very powerful. They help you control the flow of a loop and write more efficient programs.

Use `break` when you want to stop the loop early.
Use `continue` when you want to skip part of the loop and keep going.

---

This lesson covers the two essential control statements for loops: `break` and `continue`.
