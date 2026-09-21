# Lesson 2: JavaScript Basics

## 2.1 Getting Your Environment Ready

**Goal:** Set up a simple, no-install way to start writing and running JavaScript.

You don't need any special software to start experimenting with JavaScript — every modern browser ships with a built-in console that runs code instantly.

**Quick setup — the browser console:**

1. Open any browser (Chrome, Edge, Firefox — whichever you have).
2. Right-click anywhere on a page and choose **Inspect**, or press `Ctrl+Shift+I`.
3. Switch to the **Console** tab. Anything you type there runs immediately.

**Try it yourself:** Open the console and type:

```js
console.log("JavaScript is now running in my browser!");
```

Press Enter and watch the message appear.

## 2.2 Writing Your First Script

**Goal:** Understand the two places JavaScript code can live, and run a script both ways.

JavaScript can sit directly inside an HTML page, or live in its own `.js` file that the page loads separately. Real projects almost always use the second approach, since it keeps markup and logic apart.

**Option A — JavaScript inside HTML**

Create `index.html`:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My First Script</title>
</head>
<body>
  <h1>Practicing JavaScript</h1>
  <script>
    console.log("This message came from inline JavaScript.");
  </script>
</body>
</html>
```

**Option B — JavaScript in its own file**

Create `app.js`:

```js
console.log("This message came from an external file called app.js.");
```

Then link it from `index.html`:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My First Script</title>
</head>
<body>
  <h1>Practicing JavaScript</h1>
  <script src="app.js"></script>
</body>
</html>
```

**Try it yourself:** Build both versions above, open `index.html` in a browser, and check the console for the output.

## 2.3 Variables and Data Types

**Goal:** Learn how to store data in variables, and understand `var`, `let`, and `const` — including how each one behaves inside a block of code.

### What's a Variable?

A variable is just a labeled box for holding a value — a price, a name, a true/false flag, anything. In JavaScript you create one with `var`, `let`, or `const`.

### var vs. let vs. const

| Keyword | Can reassign? | Scope | Recommended? |
|---|---|---|---|
| `var` | Yes | Function-scoped (ignores blocks like `if` or `for`) | Avoid in new code |
| `let` | Yes | Block-scoped | Use for values that will change |
| `const` | No | Block-scoped | Use by default, for values that won't change |

**Real-life example — an online store's product info:**

```js
let stockCount = 42;                   // this will change as items sell
const productName = "Wireless Mouse";  // this shouldn't change
var warehouse = "Warehouse B";         // old-style declaration

console.log(productName);  // Output: Wireless Mouse
console.log(stockCount);   // Output: 42
console.log(warehouse);    // Output: Warehouse B
```

### Block Scope in Action

This is the real difference between `var` and `let`/`const`: a **block** is anything wrapped in `{ }` — an `if` statement, a `for` loop, and so on. `let` and `const` only exist inside the block where they're declared; `var` leaks straight out of it.

**Example 1 — a ticket count checked inside an `if` block:**

```js
if (true) {
  var totalTicketsVar = 100;
  let totalTicketsLet = 100;
  const totalTicketsConst = 100;
}

console.log(totalTicketsVar);   // Output: 100 — var ignores the block boundary
console.log(totalTicketsLet);   // ReferenceError — let stays trapped inside the block
console.log(totalTicketsConst); // ReferenceError — const stays trapped inside the block
```

**Example 2 — a classic loop pitfall with `var`:**

Imagine printing a boarding-pass number for each passenger after a short delay:

```js
for (var i = 1; i <= 3; i++) {
  setTimeout(() => console.log("Boarding pass (var):", i), 100);
}
// Output:
// Boarding pass (var): 4
// Boarding pass (var): 4
// Boarding pass (var): 4
// var shares ONE variable across the entire loop, so by the time the
// delayed messages run, i has already finished counting up to 4.

for (let j = 1; j <= 3; j++) {
  setTimeout(() => console.log("Boarding pass (let):", j), 100);
}
// Output:
// Boarding pass (let): 1
// Boarding pass (let): 2
// Boarding pass (let): 3
// let creates a FRESH variable for every single loop iteration.
```

This loop behavior is one of the main real-world reasons modern JavaScript favors `let` and `const` over `var`.

**Example 3 — a fitting-room light switch (const protects against accidental changes):**

```js
const maxOccupancy = 1; // a fitting room only allows one person at a time

function tryToChangeOccupancy() {
  maxOccupancy = 2; // TypeError: Assignment to constant variable.
}
```

`const` doesn't just organize code — it actively stops a value from being overwritten by mistake somewhere else in a large program.

### Data Types

JavaScript values come in a few basic types. Here they are shown through a customer-profile example:

- **String** — text, wrapped in quotes:

```js
let customerName = "Amara Chen";
```

- **Number** — numeric values:

```js
let loyaltyPoints = 1280;
```

- **Boolean** — true or false values:

```js
let isPremiumMember = true;
```

**Try it yourself:**

```js
let city = "Nairobi";
const yearJoined = 2022;
let isSubscribed = true;

console.log(city);         // Output: Nairobi
console.log(yearJoined);   // Output: 2022
console.log(isSubscribed); // Output: true
```

## 2.4 Operators

**Goal:** Learn the main categories of operators — arithmetic, comparison, logical, and string — through everyday scenarios.

An operator is a symbol or keyword that acts on values: adding up prices, comparing scores, combining conditions, or joining pieces of text together.

### 1. Arithmetic Operators — Splitting a Restaurant Bill

| Operator | Meaning |
|---|---|
| `+` | Addition |
| `-` | Subtraction |
| `*` | Multiplication |
| `/` | Division |
| `%` | Modulus (remainder) |
| `++` | Increment by one |
| `--` | Decrement by one |

```js
let billTotal = 60;
let numberOfFriends = 4;

console.log(billTotal + numberOfFriends); // Output: 64
console.log(billTotal - numberOfFriends); // Output: 56
console.log(billTotal * numberOfFriends); // Output: 240
console.log(billTotal / numberOfFriends); // Output: 15 (each person pays 15)
console.log(billTotal % numberOfFriends); // Output: 0  (splits evenly)
console.log(numberOfFriends++);           // Output: 4 (then becomes 5)
console.log(numberOfFriends--);           // Output: 5 (then becomes 4)
```

**Try it yourself:** A taxi ride costs `fare = 18` and there are `passengers = 3` sharing it. Work out the total, the difference, the product, the split cost per person, and the remainder.

```js
let fare = 18;
let passengers = 3;

console.log(fare + passengers); // Output: 21
console.log(fare - passengers); // Output: 15
console.log(fare * passengers); // Output: 54
console.log(fare / passengers); // Output: 6
console.log(fare % passengers); // Output: 0
```

### 2. Comparison Operators — Checking Exam Results

| Operator | Meaning |
|---|---|
| `==` | Equal (loose — ignores type) |
| `!=` | Not equal (loose) |
| `===` | Strictly equal (checks type too) |
| `!==` | Strictly not equal |
| `>` | Greater than |
| `<` | Less than |
| `>=` | Greater than or equal |
| `<=` | Less than or equal |

```js
let studentScore = 75;
let passMark = "75"; // stored as text this time, e.g. typed into a form

console.log(studentScore == passMark);  // Output: true  (values match, type ignored)
console.log(studentScore === passMark); // Output: false (number vs. string)
console.log(studentScore != passMark);  // Output: false
console.log(studentScore !== passMark); // Output: true
console.log(studentScore > passMark);   // Output: false
console.log(studentScore < passMark);   // Output: false
console.log(studentScore >= passMark);  // Output: true
console.log(studentScore <= passMark);  // Output: true
```

**Try it yourself:** A theme park requires riders to be at least `minimumAge = 12` for a rollercoaster. A visitor types their age into a form, so it arrives as text: `visitorAge = "12"`. Compare the two values with every comparison operator and notice where loose (`==`) and strict (`===`) comparison disagree.

### 3. Logical Operators — Deciding Who Can Borrow a Library Book

| Operator | Meaning |
|---|---|
| `&&` | AND — true only if both sides are true |
| `\|\|` | OR — true if at least one side is true |
| `!` | NOT — flips true to false and vice versa |

```js
let hasLibraryCard = true;
let hasOverdueBooks = false;

console.log(hasLibraryCard && !hasOverdueBooks); // Output: true — allowed to borrow
console.log(hasLibraryCard || hasOverdueBooks);  // Output: true — at least one is true
console.log(!hasOverdueBooks);                   // Output: true
```

**Try it yourself:** You can go hiking only if `isWeatherGood` **and** `hasWaterBottle` are both true.

```js
let isWeatherGood = true;
let hasWaterBottle = false;

console.log(isWeatherGood && hasWaterBottle); // Output: false — missing water, stay home
console.log(isWeatherGood || hasWaterBottle); // Output: true  — at least the weather's fine
console.log(!isWeatherGood);                  // Output: false
```

### 4. String Operators — Printing a Personalized Receipt

| Operator | Meaning |
|---|---|
| `+` | Joins (concatenates) strings |
| `+=` | Appends a string onto an existing variable |

```js
let firstName = "Kwame";
let lastName = "Owusu";
console.log(firstName + " " + lastName); // Output: Kwame Owusu

let receiptMessage = "Thank you for shopping, ";
receiptMessage += firstName;
receiptMessage += "!";
console.log(receiptMessage); // Output: Thank you for shopping, Kwame!
```

---

*Source: paraphrased from `Lesson 2 JavaScript Basics.pdf`, with reworked real-life examples and extra block-scope scenarios for `var`, `let`, and `const`.*
