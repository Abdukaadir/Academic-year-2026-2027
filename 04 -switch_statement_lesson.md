# Lesson: The `switch` Statement in JavaScript

## Objective

By the end of this lesson, students should be able to:

- Understand the purpose of the `switch` statement.
- Explain the difference between `if...else` and `switch`.
- Create a `switch` statement using `case`, `break`, and `default`.
- Use `switch` when one value has several possible choices.
- Apply `switch` to practical programming problems.
- Identify situations where `if...else` is more appropriate than `switch`.

---

# 1. Comparing `if...else` and `switch`

Both `if...else` and `switch` allow a program to make decisions. However, they are commonly used for different types of problems.

An `if...else` statement is useful when we need to evaluate conditions or ranges.

For example:

```javascript
let age = 20;

if (age >= 18) {
    console.log("You are an adult.");
} else {
    console.log("You are a minor.");
}
```

Here, the program is checking a condition: whether `age` is greater than or equal to `18`.

A `switch` statement is more suitable when one value needs to be compared with several specific options.

For example, a university system may receive a student's faculty code and display the corresponding faculty name.

```javascript
let faculty = "CIS";

switch (faculty) {
    case "CIS":
        console.log("Computer and Information Science");
        break;

    case "ENG":
        console.log("Engineering");
        break;

    case "BM":
        console.log("Business and Management");
        break;

    default:
        console.log("Faculty not found.");
}
```

### When to Use `if...else`

Use `if...else` when you need to check things such as:

```javascript
score >= 50
age < 18
price > 100
marks >= 80
```

It is especially useful for ranges, comparisons, and more complex logical conditions.

### When to Use `switch`

Use `switch` when one value has several known possibilities.

Examples include:

- Days of the week
- Months
- Menu choices
- Faculty codes
- User roles
- Traffic-light colors
- Calculator operators
- Payment methods

---

# 2. What Is a `switch` Statement?

A `switch` statement checks the value of an expression and compares it with a number of possible values called `case` values.

When a matching case is found, its code is executed.

### Syntax

```javascript
switch (expression) {
    case value1:
        // code to execute
        break;

    case value2:
        // code to execute
        break;

    default:
        // code when no case matches
}
```

The main parts are:

- `switch` — starts the decision structure.
- `expression` — the value being checked.
- `case` — defines a possible value.
- `break` — stops the `switch` after a matching case.
- `default` — runs when no case matches.

---

# 3. The `case` Statement

A `case` represents one possible value that the `switch` statement can match.

### Example

Suppose a program needs to display information about a student's academic level.

```javascript
let level = "Second Year";

switch (level) {
    case "First Year":
        console.log("You are in your first year.");
        break;

    case "Second Year":
        console.log("You are in your second year.");
        break;

    case "Third Year":
        console.log("You are in your third year.");
        break;

    case "Fourth Year":
        console.log("You are in your fourth year.");
        break;

    default:
        console.log("Invalid academic level.");
}
```

### Output

```text
You are in your second year.
```

The program compares `level` with each `case` until it finds a match.

---

# 4. The `break` Statement

The `break` statement is important when working with `switch`.

After a matching case has executed, `break` tells JavaScript to leave the `switch` statement.

### Example

```javascript
let number = 2;

switch (number) {
    case 1:
        console.log("One");
        break;

    case 2:
        console.log("Two");
        break;

    case 3:
        console.log("Three");
        break;

    default:
        console.log("Unknown number.");
}
```

### Output

```text
Two
```

When `number` is `2`, JavaScript executes `case 2`. The `break` then stops the `switch`.

### What Happens Without `break`?

If `break` is omitted, JavaScript can continue executing the statements in the following cases. This is called **fall-through**.

For beginners, it is generally best to include `break` after each case unless fall-through is intentionally required.

---

# 5. The `default` Case

The `default` case provides a result when none of the available cases match.

It works similarly to the final `else` in an `if...else if...else` statement.

### Example

```javascript
let paymentMethod = "Crypto";

switch (paymentMethod) {
    case "Cash":
        console.log("Payment will be made with cash.");
        break;

    case "Card":
        console.log("Payment will be made with a card.");
        break;

    case "Mobile Money":
        console.log("Payment will be made using mobile money.");
        break;

    default:
        console.log("Payment method not supported.");
}
```

### Output

```text
Payment method not supported.
```

Since `Crypto` does not match any case, the `default` block is executed.

---

# 6. Example: Days of the Week

A program can use `switch` to convert a number into the corresponding day.

```javascript
let day = 5;

switch (day) {
    case 1:
        console.log("Monday");
        break;

    case 2:
        console.log("Tuesday");
        break;

    case 3:
        console.log("Wednesday");
        break;

    case 4:
        console.log("Thursday");
        break;

    case 5:
        console.log("Friday");
        break;

    case 6:
        console.log("Saturday");
        break;

    case 7:
        console.log("Sunday");
        break;

    default:
        console.log("Invalid day number.");
}
```

### Output

```text
Friday
```

---

# 7. Example: University Menu

A university management system may provide different options to a user.

```javascript
let choice = 3;

switch (choice) {
    case 1:
        console.log("View student profile");
        break;

    case 2:
        console.log("View courses");
        break;

    case 3:
        console.log("View examination results");
        break;

    case 4:
        console.log("View attendance");
        break;

    case 5:
        console.log("Logout");
        break;

    default:
        console.log("Invalid menu option.");
}
```

### Output

```text
View examination results
```

Each number represents a specific action available in the system.

---

# 8. Example: Calculator Using `switch`

A calculator can use `switch` to determine which mathematical operation should be performed.

```javascript
let num1 = 20;
let num2 = 5;
let operator = "*";

switch (operator) {
    case "+":
        console.log(num1 + num2);
        break;

    case "-":
        console.log(num1 - num2);
        break;

    case "*":
        console.log(num1 * num2);
        break;

    case "/":
        console.log(num1 / num2);
        break;

    default:
        console.log("Invalid operator.");
}
```

### Output

```text
100
```

The value stored in `operator` determines which calculation is performed.

---

# 9. Example: Traffic Light

A traffic-light program can use a color to determine the appropriate instruction.

```javascript
let light = "red";

switch (light) {
    case "red":
        console.log("Stop");
        break;

    case "yellow":
        console.log("Get ready");
        break;

    case "green":
        console.log("Go");
        break;

    default:
        console.log("Invalid traffic-light color.");
}
```

### Output

```text
Stop
```

---

# 10. Example: User Role

A system can use a user's role to determine what type of access or message should be displayed.

```javascript
let role = "admin";

switch (role) {
    case "admin":
        console.log("You can manage the system.");
        break;

    case "lecturer":
        console.log("You can manage your courses.");
        break;

    case "student":
        console.log("You can view your academic information.");
        break;

    default:
        console.log("Unknown user role.");
}
```

### Output

```text
You can manage the system.
```

---

# 11. Multiple Cases With the Same Result

Sometimes several values should produce the same result.

Multiple `case` statements can be placed together before the code that should be executed.

### Example

```javascript
let day = "Saturday";

switch (day) {
    case "Saturday":
    case "Sunday":
        console.log("It is the weekend.");
        break;

    case "Monday":
    case "Tuesday":
    case "Wednesday":
    case "Thursday":
    case "Friday":
        console.log("It is a working day.");
        break;

    default:
        console.log("Invalid day.");
}
```

### Output

```text
It is the weekend.
```

Here, both `Saturday` and `Sunday` lead to the same output.

---

# 12. `if...else` or `switch`?

Both structures can make decisions, but they are not always equally suitable.

| `if...else` | `switch` |
|---|---|
| Useful for conditions and comparisons | Useful for matching specific values |
| Can work with `>`, `<`, `>=`, and `<=` | Usually checks one expression against fixed cases |
| Good for ranges | Good for predefined options |
| Suitable for complex logical expressions | Suitable for menus and fixed choices |
| Can use `&&` and `||` | Keeps several exact-value choices organized |

### Example: `if...else` is more suitable

Suppose we want to determine a student's grade based on a range of marks.

```javascript
let marks = 75;

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

This is suitable for `if...else` because the program is checking ranges.

### Example: `switch` is more suitable

Suppose we want to respond to a selected menu option.

```javascript
let option = 2;

switch (option) {
    case 1:
        console.log("Add student");
        break;

    case 2:
        console.log("Update student");
        break;

    case 3:
        console.log("Delete student");
        break;

    default:
        console.log("Invalid option.");
}
```

This is suitable for `switch` because the program is matching one value against several fixed choices.

---

# 13. Practice Exercises

Complete the following exercises using JavaScript.

## Exercise 1: Simple Calculator

Create a program that accepts two numbers and an operator.

The program should support:

- `+` for addition
- `-` for subtraction
- `*` for multiplication
- `/` for division

Use a `switch` statement to select the correct operation.

### Example

```text
First number: 15
Second number: 3
Operator: /
Result: 5
```

---

## Exercise 2: Day of the Week

Write a program that accepts a number from `1` to `7` and displays the corresponding day.

Use:

```text
1 → Monday
2 → Tuesday
3 → Wednesday
4 → Thursday
5 → Friday
6 → Saturday
7 → Sunday
```

If the user enters a number outside this range, display:

```text
Invalid day.
```

---

## Exercise 3: Student Management Menu

Create a student management menu using `switch`.

The options should be:

```text
1 → View Student Profile
2 → View Courses
3 → View Results
4 → View Attendance
5 → Logout
```

Display the appropriate message based on the selected option.

If the user enters another number, display:

```text
Invalid option.
```

---

## Exercise 4: Traffic Light

Write a program that accepts a traffic-light color and displays the appropriate instruction.

Use:

```text
red    → Stop
yellow → Get ready
green  → Go
```

If another color is entered, display:

```text
Invalid color.
```

---

## Exercise 5: Month

Write a program that accepts a number from `1` to `12` and displays the corresponding month.

For example:

```text
1  → January
2  → February
3  → March
...
12 → December
```

If the number is not between `1` and `12`, display:

```text
Invalid month.
```

---

# Conclusion

The `switch` statement is a useful way to organize multiple fixed choices in a JavaScript program.

The main parts of a `switch` statement are:

```text
switch
case
break
default
```

The `case` keyword represents a possible value. The `break` statement stops the `switch` after a matching case has been executed. The `default` block handles situations where none of the cases match.

Use `if...else` when you need to evaluate ranges, comparisons, or more complex logical conditions. Use `switch` when one value needs to be compared with several specific options.

Understanding both structures helps you select the appropriate approach when building JavaScript programs.
