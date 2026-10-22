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

# JavaScript Nested `if` Statements and Logical Operators

## 1. Student Pass or Fail

A student must score at least 50 to pass. If they pass, check whether they scored 80 or more to award a distinction.

### Example A: Using a Nested `if`

```javascript
let mark = 85;

if (mark >= 50) {
    console.log("Student passed");

    if (mark >= 80) {
        console.log("Distinction awarded");
    }
} else {
    console.log("Student failed");
}
```

**Output:**

```text
Student passed
Distinction awarded
```

**How it works:**

1. The outer `if` checks whether `mark >= 50`.
2. Because the mark is 85, the outer condition is true.
3. The inner `if` checks whether `mark >= 80`.
4. Both conditions are true, so both messages are displayed.

### Example B: Using Logical Operators

```javascript
let mark = 85;

if (mark >= 50) {
    console.log("Student passed");
}

if (mark >= 50 && mark >= 80) {
    console.log("Distinction awarded");
}

if (mark < 50) {
    console.log("Student failed");
}
```

**Output:**

```text
Student passed
Distinction awarded
```

The `&&` operator means **AND**. Both conditions must be true for the combined condition to be true.

**Note:** `mark >= 50 && mark >= 80` can be simplified to `mark >= 80`, because a mark of 80 or more is already at least 50.

## 2. Login System

A user must enter the correct username and password.

### Example A: Using a Nested `if`

```javascript
let username = "admin";
let password = "1234";

if (username === "admin") {
    if (password === "1234") {
        console.log("Login successful");
    } else {
        console.log("Incorrect password");
    }
} else {
    console.log("Incorrect username");
}
```

**Output:**

```text
Login successful
```

### Example B: Using `&&`

```javascript
let username = "admin";
let password = "1234";

if (username === "admin" && password === "1234") {
    console.log("Login successful");
} else {
    console.log("Incorrect username or password");
}
```

**Output:**

```text
Login successful
```

Both conditions must be true for the login to succeed. The nested version can give a specific error message; the combined version gives one general error message.

## 3. University Admission

A student must score at least 60 on the entrance exam and at least 50 in English.

### Example A: Using a Nested `if`

```javascript
let entranceMark = 75;
let englishMark = 65;

if (entranceMark >= 60) {
    console.log("Entrance mark accepted");

    if (englishMark >= 50) {
        console.log("Admission requirements satisfied");
    } else {
        console.log("English mark is too low");
    }
} else {
    console.log("Entrance mark is too low");
}
```

**Output:**

```text
Entrance mark accepted
Admission requirements satisfied
```

### Example B: Using `&&`

```javascript
let entranceMark = 75;
let englishMark = 65;

if (entranceMark >= 60 && englishMark >= 50) {
    console.log("Admission requirements satisfied");
} else {
    console.log("Admission requirements not satisfied");
}
```

**Output:**

```text
Admission requirements satisfied
```

The combined condition checks both requirements. The `else` branch does not identify which requirement was not met.

## 4. User Input and Course Registration

The program checks the user's age. If the user is at least 18, it asks whether they have the required certificate.

### Example A: Using a Nested `if`

```javascript
let age = Number(prompt("Enter your age"));

if (age >= 18) {
    let certificate = prompt(
        "Do you have the required certificate? (yes/no)"
    );

    if (certificate === "yes") {
        console.log("You can register");
    } else {
        console.log("You need the required certificate");
    }
} else {
    console.log("You must be at least 18");
}
```

This asks about the certificate only if the user's age is at least 18.

### Example B: Using `&&`

If both pieces of information are already available, combine the conditions:

```javascript
let age = 20;
let certificate = "yes";

if (age >= 18 && certificate === "yes") {
    console.log("You can register");
} else {
    console.log("You cannot register");
}
```

**Output:**

```text
You can register
```

Use the nested version when you need to ask for the certificate only after checking the age.

## 5. Nested `if` vs. Logical Operators

| Situation | Suitable approach |
|---|---|
| Check whether multiple conditions are all true | `&&` |
| Check whether at least one condition is true | `||` |
| Check one condition, then make another decision inside it | Nested `if` |
| Give different messages for different failure reasons | Nested `if` or `if...else if` |
| Check several requirements that are already available | A combined condition using `&&` |


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

## Student Practice Exercises (Nested If with Logical Operators)

**Instructions:** Write and test each program in JavaScript. Do not use arrays or loops. For each exercise, try to solve it first with a nested `if` where appropriate, then decide whether a logical operator can make the condition simpler.


1. **Library membership:** A student can borrow a book if they have a valid student ID and their membership is active. Use `&&` to check both conditions.
2. **Discount eligibility:** A customer receives a discount if they are a university student or are at least 60 years old. Use `||` to check the two alternatives.
3. **Driving eligibility:** Ask the user to enter their age with `prompt()`. If they are at least 18, ask whether they have a driving license. Display an appropriate message using a nested `if`.
4. **Password check:** Create a variable named `password`. If it matches the correct password, display `Password accepted`. Otherwise, display `Incorrect password`. Then update the program to check the username and password together using `&&`.
5. **Scholarship eligibility:** A student must have a mark of at least 85 and good attendance of at least 90 percent. Use `&&` to decide whether the student qualifies.
6. **Sports club entry:** A person can enter the sports club if they are a registered member. If they are not a member, check whether they have a valid guest pass. Use a nested `if` to display `Entry allowed` or `Entry denied`.

### Challenge Questions

7. **Predict the output:** Before running the code, write down what it will display. Then test your answer.

    ```javascript
    let mark = 75;

    if (mark >= 50) {
        console.log("Passed");
        if (mark >= 80) {
            console.log("Distinction");
        }
    } else {
        console.log("Failed");
    }
    ```

8. **Compare the conditions:** Explain the difference between these two conditions and give one example where you would use each.

    ```javascript
    age >= 18 && hasCertificate === "yes"
    ```

    ```javascript
    age >= 18 || hasCertificate === "yes"
    ```

9. **Improve the message:** Rewrite the admission example so that it tells the student whether the entrance mark is too low, the English mark is too low, or both requirements are satisfied.

## Summary

- A **nested `if`** places one decision inside another.
- The logical AND operator (`&&`) is true only when both conditions are true.
- The logical OR operator (`||`) is true when at least one condition is true.
- Use nested `if` statements when a later decision depends on an earlier one or when you need different messages for different outcomes.
- Use logical operators to combine conditions when a single combined decision is sufficient.


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
