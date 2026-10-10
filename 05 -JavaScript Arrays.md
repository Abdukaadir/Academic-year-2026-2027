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

## 8. Arrays versus other collection choices

An array is appropriate when order and position are meaningful, and when repeated items are expected. An array is not a special “list of only one type”: JavaScript permits mixed values, but a predictable structure is usually easier to maintain. If you need to describe one item through named fields, an object is a better fit; see [JavaScript Objects — Detailed Guide](JavaScript%20Objects%20%E2%80%94%20Detailed%20Guide.md).

**Exercise:** Decide whether each should be an array, an object, or an array of objects: a playlist, one user's profile, and a list of library books where each book has a title and author. Explain each choice.

