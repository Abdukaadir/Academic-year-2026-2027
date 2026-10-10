# JavaScript Arrays: Detailed Guide

An array is a value that keeps a sequence of items together. Use one when the data is naturally a list: meals in a menu, scores in a game, stops on a route, or products in a basket. Items are kept in order and can be reached by their numeric position.

## 1. Creating arrays

### Array literal — the usual choice

Square brackets create an array. Put items inside, separated by commas. An empty pair creates an empty array that can be filled later.

```js
const weekdays = ["Monday", "Tuesday", "Wednesday"];
const emptyQueue = [];
const mixed = ["Ada", 31, true]; // valid, although one kind of data is often easier to manage
```

This is the clearest form for most programs because you can see the initial items directly.

### `new Array(...)` — constructor form

The `Array` constructor has behavior that can surprise beginners:

```js
const names = new Array("Ada", "Lin"); // ["Ada", "Lin"]
const spaces = new Array(3);            // three empty slots; length is 3
```

One numeric argument means “make an array with this length,” not “put this number in the array.” For a one-number array, use `[3]` or `Array.of(3)`. Prefer literals for ordinary lists.

### `Array.of(...)` — make items from arguments

`Array.of` treats each argument as an item, including a single number:

```js
const oneNumber = Array.of(3); // [3]
const several = Array.of(3, 6, 9); // [3, 6, 9]
```

Unlike `new Array(3)`, `Array.of(3)` contains one item whose value is `3`.

### `Array.from(...)` — make an array from iterable or array-like data

Use `Array.from` to create a new array from a string, a `Set`, or a value with a length and indexed entries. It can also transform each item while creating the array.

```js
const letters = Array.from("cat"); // ["c", "a", "t"]
const doubled = Array.from([2, 4, 6], number => number * 2);
// [4, 8, 12]
```

### Spread syntax — copy or combine

The spread operator (`...`) expands an iterable's items into a new array literal.

```js
const morning = ["tea", "toast"];
const lunch = ["rice", "beans"];
const meals = [...morning, ...lunch]; // new combined array
const copy = [...morning];            // shallow copy
```

These creation approaches are not interchangeable in every case: use a literal for a known list, `Array.of` when arguments should become items, `Array.from` to convert/transform another iterable, and spread to combine or copy lists.

**Exercise:** Create `[5]` using a literal, `Array.of`, and the constructor in a way that results in one item with value `5`. Also create a three-item array using `Array.from` and a mapping callback. Explain why `new Array(5)` is different.

## 2. Indexes, length, reading, and updating

Array positions are called indexes and begin at zero. For a list of length `n`, the final index is `n - 1`. `length` counts elements/slots; it is not an index.

```js
const busStops = ["Market", "Library", "Hospital"];

console.log(busStops[0]); // "Market"
console.log(busStops[2]); // "Hospital"
console.log(busStops.length); // 3
console.log(busStops[3]); // undefined: no item at index 3

busStops[1] = "Museum"; // replace an existing item
busStops[3] = "Terminal"; // assigning beyond the end creates a gap if needed
```

Avoid creating gaps by assigning far beyond the current length; such sparse arrays are harder to reason about. To add items, use array methods. Arrays can contain different value types, but consistent item shapes make code easier to understand.

**Real-life comparison:** A route's first stop is position zero because the index is an offset from the beginning: move zero places to get the first stop, one place to get the second.

**Exercise:** Given `const temperatures = [18, 21, 24, 19]`, print the first and last values using `length`, update the second value to `22`, and write the result of `temperatures[4]`.

## 3. Add and remove items at the ends

These four methods alter the original array:

| Method | Action | Return value |
| --- | --- | --- |
| `push(item)` | Add one or more items at the end | New length |
| `pop()` | Remove the last item | Removed item, or `undefined` if empty |
| `unshift(item)` | Add one or more items at the beginning | New length |
| `shift()` | Remove the first item | Removed item, or `undefined` if empty |

```js
const orders = ["Order A", "Order B"];
const count = orders.push("Order C"); // orders now has 3 items; count is 3
const served = orders.shift();         // served is "Order A"
orders.unshift("Urgent order");       // insert at the front
const cancelled = orders.pop();        // remove the final order
```

Think of `push`/`pop` as placing or taking the newest plate at the top of a stack. `shift`/`unshift` act on the front of a waiting line. Removing/adding at the front may require the remaining positions to be reindexed, so end operations are generally preferable for frequent queue-like additions.

**Exercise:** Start with `let pantry = ["flour", "sugar"]`. Add `"salt"` at the end, add `"oil"` at the beginning, remove one item from each end, and print both removed values and the remaining pantry.

## 4. Insert, remove, replace, and copy sections

`splice(start, deleteCount, ...items)` changes an array in place. It can remove items, insert items, or do both. Its return value is a new array containing the removed items.

```js
const schedule = ["math", "break", "science", "art"];
const removed = schedule.splice(1, 1, "lunch");
// schedule: ["math", "lunch", "science", "art"]
// removed: ["break"]
```

`slice(start, end)` returns a shallow copy of a section and does not change the original. The `end` position is excluded.

```js
const firstTwo = schedule.slice(0, 2);
const copyOfSchedule = schedule.slice();
```

Use `splice` when the source list itself should change; use `slice` when you want a selection or copy. To copy an array one level deep, `[...schedule]` is another option. Nested objects inside a shallow copy are still shared references.

**Exercise:** With `const scores = [10, 20, 30, 40, 50]`, use `slice` to get `[20, 30]` without changing `scores`. Then use `splice` to replace `30` with `35` and inspect both the changed array and the removed-items result.

## 5. Find, test, transform, and filter

Arrays provide methods that express common list tasks without manually managing an index:

```js
const prices = [12, 25, 8, 30];

prices.includes(25);                    // true: does it contain this value?
prices.indexOf(8);                     // 2: first matching index, or -1
prices.find(price => price > 20);       // 25: first matching item
prices.findIndex(price => price > 20);  // 1: its index
prices.some(price => price < 10);       // true: does at least one match?
prices.every(price => price > 0);      // true: do all match?
const discounted = prices.map(p => p * 0.9); // new transformed array
const large = prices.filter(p => p >= 20);   // new matching array
```

`map` keeps one output for every input, while `filter` keeps only inputs that pass a condition. `find` returns one matching value; `filter` returns all matches. These methods do not replace the original array.

`reduce` combines a list into one accumulated result, such as a total:

```js
const total = prices.reduce((sum, price) => sum + price, 0); // 75
```

The `0` is the starting value for the accumulator. Providing it makes the behavior clear, including for an empty list.

**Exercise:** Given an array of daily step counts, use `filter` to get days over 8,000 steps, `map` to convert the counts to thousands, `some` to check whether any day exceeded 10,000, and `reduce` to calculate the total.

## 6. Iterating over arrays

Use `for...of` when you need each value, `forEach` for an action on each value, and an indexed `for` loop when the position matters or you need precise control.

```js
const names = ["Nia", "Omar", "Pia"];

for (const name of names) {
  console.log(name);
}

names.forEach((name, index) => console.log(index, name));

for (let index = 0; index < names.length; index++) {
  console.log(names[index]);
}
```

Avoid changing the array's length while looping unless that behavior is intentional. For a new transformed list, `map` is often clearer than building one manually.

**Exercise:** Print each item in `const chores = ["wash", "cook", "study"]` with a one-based number (1, 2, 3). Do it once with an indexed loop and once with `forEach`.

## 7. Nested arrays

A nested array is an array whose items include other arrays. Use it when each entry is itself a sequence, such as a weekly timetable, a cinema seating chart, or a grid of map cells.

```js
const seats = [
  ["A1", "A2", "A3"],
  ["B1", "B2", "B3"],
  ["C1", "C2", "C3"]
];

console.log(seats[1]);    // second row: ["B1", "B2", "B3"]
console.log(seats[1][2]); // row 2, seat 3: "B3"
seats[0][1] = "Reserved";
```

Read nested indexes from the outside inward: `seats[row][column]`. The first index selects the inner array; the second selects an item within it. For the timetable example, `week[day][period]` can select one lesson.

Nested arrays need not be rectangular, but a grid is easier to use if every row has the same number of columns. To visit every cell:

```js
for (const row of seats) {
  for (const seat of row) {
    console.log(seat);
  }
}
```

**Exercise:** Create a 3-by-3 array representing a tic-tac-toe board. Read the center cell, change a corner cell to `"X"`, and use nested loops to print all cells.

## 8. Arrays versus other collection choices

An array is appropriate when order and position are meaningful, and when repeated items are expected. An array is not a special “list of only one type”: JavaScript permits mixed values, but a predictable structure is usually easier to maintain. If you need to describe one item through named fields, an object is a better fit; see [JavaScript Objects — Detailed Guide](JavaScript%20Objects%20%E2%80%94%20Detailed%20Guide.md).

**Exercise:** Decide whether each should be an array, an object, or an array of objects: a playlist, one user's profile, and a list of library books where each book has a title and author. Explain each choice.

