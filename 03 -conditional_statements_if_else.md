# Lesson: Conditional Statements (`if-else`)

## Objective

By the end of this lesson, students should be able to:

- Understand how conditional statements work in JavaScript.
- Use `if` to execute code when a condition is true.
- Use `if...else` to choose between two possible outcomes.
- Use `else if` to check multiple conditions.
- Use the ternary operator for simple two-way decisions.
- Apply conditional statements to simple programming problems.

---

# 1. The `if` Statement

An `if` statement allows a program to check a condition before executing a particular block of code.

If the condition evaluates to `true`, the code inside the `if` block runs. If the condition is `false`, the block is skipped.

### Syntax

```javascript
if (condition) {
    // code to execute when the condition is true
}
```

### Example

Suppose a cinema allows people who are 18 or older to watch a particular movie.

```javascript
let age = 21;

if (age >= 18) {
    console.log("You can watch the movie.");
}
```

### Output

```text
You can watch the movie.
```

If `age` were `15`, the message would not be displayed because the condition would be false.

---

# 2. The `if...else` Statement

An `if...else` statement is used when a program needs to choose between two different actions.

If the condition is true, the first block runs. Otherwise, the `else` block runs.

### Syntax

```javascript
if (condition) {
    // code that runs when the condition is true
} else {
    // code that runs when the condition is false
}
```

### Example

A program can check whether a person has enough money to buy lunch.

```javascript
let money = 25;

if (money >= 20) {
    console.log("You can buy lunch.");
} else {
    console.log("You do not have enough money.");
}
```

The program checks the value of `money` and selects one of the two possible messages.

### Exercise

Write an `if...else` statement that checks a student's score.

- If the score is `50` or higher, display `"You passed!"`.
- Otherwise, display `"You failed."`

---

# 3. The `else if` Statement

Sometimes a program needs to evaluate more than two possible conditions.

The `else if` statement allows us to test additional conditions when the previous condition is false.

JavaScript checks the conditions from top to bottom. When it finds a condition that is true, its code block is executed and the remaining conditions are skipped.

### Syntax

```javascript
if (condition1) {
    // code for condition1
} else if (condition2) {
    // code for condition2
} else {
    // code when none of the conditions are true
}
```

### Example

A program can classify temperature into different categories.

```javascript
let temperature = 22;

if (temperature < 0) {
    console.log("Very cold");
} else if (temperature < 15) {
    console.log("Cold");
} else if (temperature <= 25) {
    console.log("Warm");
} else {
    console.log("Hot");
}
```

### Output

```text
Warm
```

The program evaluates each condition in order until it finds one that is true.

### Exercise

Write an `else if` statement that displays:

- `"Very cold"` if the temperature is below `0`.
- `"Cold"` if the temperature is between `0` and `14`.
- `"Warm"` if the temperature is between `15` and `25`.
- `"Hot"` if the temperature is above `25`.

---

# 4. The Ternary Operator

The ternary operator is a shorter way of writing a simple `if...else` statement.

It uses three parts:

1. A condition.
2. The value to use when the condition is true.
3. The value to use when the condition is false.

### Syntax

```javascript
condition ? valueIfTrue : valueIfFalse;
```

### Example

```javascript
let age = 20;

let result = age >= 18 ? "Adult" : "Minor";

console.log(result);
```

### Output

```text
Adult
```

The same decision can be written using `if...else`:

```javascript
let age = 20;
let result;

if (age >= 18) {
    result = "Adult";
} else {
    result = "Minor";
}

console.log(result);
```

The ternary operator is most useful when the decision is simple and has only two possible results.

### Exercise

Use the ternary operator to display `"Pass"` if the variable `grade` is `60` or higher, and `"Fail"` otherwise.

---

# 5. Using Conditional Statements in Programs

Conditional statements become more useful when they are combined with variables and operators.

For example, a school program can use a student's marks to determine their grade.

```javascript
let marks = 78;

if (marks >= 90) {
    console.log("Grade A");
} else if (marks >= 80) {
    console.log("Grade B");
} else if (marks >= 70) {
    console.log("Grade C");
} else if (marks >= 60) {
    console.log("Grade D");
} else {
    console.log("Grade F");
}
```

### Output

```text
Grade C
```

The program compares the student's marks with each condition and displays the appropriate grade.

---

# 6. Practice Exercises

Complete the following exercises using JavaScript.

## Exercise 1: Simple Calculator

Write a program that accepts two numbers and an operation.

The program should be able to:

- Add the two numbers.
- Subtract the two numbers.
- Multiply the two numbers.
- Divide the two numbers.

Use conditional statements to determine which operation should be performed.

### Example

```text
First number: 20
Second number: 5
Operation: *
Result: 100
```

---

## Exercise 2: Student Grade

Write a program that accepts a student's marks and displays the corresponding grade.

Use the following grading system:

```text
90 - 100  → Grade A
80 - 89   → Grade B
70 - 79   → Grade C
60 - 69   → Grade D
Below 60  → Grade F
```

### Example

```text
Enter marks: 85
Grade: B
```

---

## Exercise 3: Odd or Even

Create a program that accepts a number and determines whether the number is odd or even.

Use the modulus operator `%`.

### Example

```text
Enter number: 24
24 is an even number.
```

Another example:

```text
Enter number: 17
17 is an odd number.
```

---

## Exercise 4: Age Category

Write a program that accepts a person's age and identifies their age category.

Use the following categories:

```text
0 - 12    → Child
13 - 19   → Teenager
20 - 59   → Adult
60+       → Senior
```

### Example

```text
Enter age: 16
Category: Teenager
```

---

## Exercise 5: Number Checker

Write a program that accepts a number and determines whether it is:

- Positive
- Negative
- Zero

### Example

```text
Enter number: -8
The number is negative.
```

Another example:

```text
Enter number: 0
The number is zero.
```

---

# Conclusion

Conditional statements allow programs to make decisions based on different conditions.

The main concepts covered in this lesson are:

```text
if
if...else
else if
ternary operator
```

The `if` statement is useful when code should run only when a particular condition is true.

The `if...else` statement provides two possible paths, while `else if` allows a program to evaluate several conditions.

The ternary operator provides a shorter syntax for simple decisions with two possible outcomes.

By practicing these concepts through calculators, grading systems, number checks, temperature categories, and age classifications, students can develop a stronger understanding of how conditional logic controls the behavior of JavaScript programs.
