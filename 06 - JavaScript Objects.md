# JavaScript Objects: Detailed Guide

An object represents one thing through named information. It is a useful fit for a person, product, place, booking, or any record with several attributes. The lesson's central idea is that each **property** connects a key (name) with a value.

## 1. Creating objects

### Object literal — the everyday form

Curly braces create an object. Inside, write each property as `key: value`, separating properties with commas.

```js
const passenger = {
  name: "Asha",
  seat: "12A",
  checkedIn: true
};
```

An empty object is `{}`. Values can be strings, numbers, booleans, arrays, other objects, functions, or other JavaScript values.

### `new Object()` — constructor form

```js
const settings = new Object();
settings.theme = "dark";
settings.fontSize = 16;
```

This creates an ordinary object, but `{}` is shorter and clearer for most cases.

### `Object.create(prototype)` — choose a prototype

Objects can inherit behavior from another object through a prototype. `Object.create` is useful when you intentionally want to choose that prototype. A null prototype is useful for a plain key-value dictionary with no inherited object properties.

```js
const dictionary = Object.create(null);
dictionary["hello"] = "a greeting";
```

For most beginner records such as a `person` or `car`, use an object literal. `Object.create` is a more specialized tool.

**Exercise:** Create the same three-property `car` object using an object literal and using `new Object()`. Which form makes the data easier to scan? Create one `Object.create(null)` dictionary entry and read it.

## 2. Keys and property values

An object's keys identify its properties. Most property keys are strings; JavaScript also supports symbols. In object literals, simple identifier-like keys can be written without quotes. Quote a key when it contains spaces, punctuation, or would otherwise be invalid as an identifier.

```js
const user = {
  name: "Musa",
  "preferred language": "Swahili",
  7: "seven"
};
```

The numeric-looking key `7` is stored as the string key `"7"`. Property values may have different types:

```js
const course = {
  title: "JavaScript Basics", // string
  lessons: 12,                // number
  published: true,            // boolean
  tags: ["web", "code"],      // array
  instructor: { name: "Jo" } // another object
};
```

**Real-life comparison:** A delivery record is like a labeled form: `address` tells you what a particular value means, while a bare position such as “item two” does not.

**Exercise:** Create an `event` object with a title, date, online status, and an array of guests. Include a property whose key contains a space and read it back.

## 3. Reading properties: dot and bracket notation

Dot notation is compact when the property's name is known and can be written as an identifier. Bracket notation uses an expression inside square brackets; it works with unusual keys and computed names.

```js
const profile = {
  name: "Musa",
  "preferred language": "Swahili"
};

console.log(profile.name); // dot notation
console.log(profile["preferred language"]); // bracket notation

const requestedField = "name";
console.log(profile[requestedField]); // "Musa"
```

`profile.requestedField` asks for a property literally named `requestedField`. `profile[requestedField]` evaluates the variable and asks for the property named by its value.

Reading a property that does not exist normally produces `undefined`. To distinguish a missing key from a key that exists with an `undefined` value, use `Object.hasOwn(profile, "name")`.

**Exercise:** Create an object with `firstName`, `lastName`, and `email`. Read one property using dot notation and another using a variable with bracket notation. Try reading a missing property and check whether a key exists with `Object.hasOwn`.

## 4. Adding, updating, and deleting properties

Assigning to a property adds it if it is new or replaces its value if it already exists. `delete` removes a property.

```js
const bicycle = { brand: "Kifaru", gears: 7 };

bicycle.color = "blue";      // add
bicycle.gears = 8;            // update
delete bicycle.color;         // remove

console.log(bicycle); // { brand: "Kifaru", gears: 8 }
```

`const` prevents reassignment of the variable, but it does not make the object's contents immutable. This is valid:

```js
const account = { balance: 100 };
account.balance = 125; // allowed
// account = {};       // TypeError: cannot reassign a const variable
```

**Exercise:** Make a `phone` object with `brand`, `model`, and `price`. Change the price, add `color`, then delete the model. Log the object after each operation.

## 5. Methods: functions stored on objects

A property whose value is a function is commonly called a **method**. Methods put actions near the data they work with. In a method, `this` usually refers to the object used to call it.

```js
const counter = {
  value: 0,
  increase() {
    this.value += 1;
  }
};

counter.increase();
console.log(counter.value); // 1
```

Arrow functions do not get their own `this`, so method shorthand is generally the clearer choice when the method needs to access the object through `this`.

**Exercise:** Create a `bankAccount` object with a `balance` and a `deposit(amount)` method that adds the amount to the balance. Call the method twice and print the balance.

## 6. Nested objects and arrays inside objects

An object can contain another object for grouped details, or an array for an ordered collection. This often mirrors real records: an order has a customer, an address, and a list of purchased products.

```js
const order = {
  number: "A104",
  customer: {
    name: "Neema",
    city: "Mombasa"
  },
  items: ["tea", "bread", "mangoes"]
};

console.log(order.customer.city); // "Mombasa"
console.log(order.items[1]);      // "bread"
order.customer.city = "Nakuru";  // update a nested property
```

Read the path from left to right: first `order`, then its `customer` property, then that object's `city`. If a middle property might be missing, optional chaining avoids an error:

```js
console.log(order.delivery?.instructions);
```

Optional chaining returns `undefined` if the value before `?.` is `null` or `undefined`; it does not create the missing object.

**Exercise:** Create a `restaurant` object with a `name`, a nested `address` (street and town), and an array of `openingDays`. Print the town and the second opening day. Update the town.

## 7. Copying objects, spread, and destructuring

Assigning one object variable to another does not copy the object. Both variables refer to the same object:

```js
const original = { name: "Ivy", points: 10 };
const alias = original;
alias.points = 12;
console.log(original.points); // 12
```

Use spread or `Object.assign` to make a **shallow copy**. A shallow copy creates a new outer object, but nested objects are still shared.

```js
const copy = { ...original, points: 15 };
const anotherCopy = Object.assign({}, original);
```

Destructuring extracts properties into variables:

```js
const { name, points } = original;
console.log(name, points);
```

**Exercise:** Copy a `user` object with spread and change the copy's name. Confirm the original name stays the same. Add a nested `address` object and test whether changing `copy.address.city` also changes the original's city. Explain the shallow-copy behavior.

## 8. Object utilities and iteration

`Object.keys` returns an array of an object's own enumerable property names. `Object.values` returns the matching values, and `Object.entries` returns `[key, value]` pairs.

```js
const scores = { Lina: 85, Mark: 91 };

Object.keys(scores);   // ["Lina", "Mark"]
Object.values(scores); // [85, 91]
Object.entries(scores); // [["Lina", 85], ["Mark", 91]]

for (const [name, score] of Object.entries(scores)) {
  console.log(`${name}: ${score}`);
}
```

Objects are not normally accessed by numeric position like arrays. If order and indexed access are central to the data, use an array. If each value needs a descriptive label, use an object.

**Exercise:** Create an object of three subject scores. Print each subject and score using `Object.entries`, and calculate the total of the values.

## 9. Objects compared with arrays

Both arrays and objects group values, but they answer different questions.

| Feature | Array | Object |
| --- | --- | --- |
| Main purpose | Hold an ordered sequence | Describe a thing with named properties |
| How values are addressed | Numeric index, such as `stops[0]` | Property key, such as `person.name` |
| Typical example | A route's stops | One passenger's name and seat |
| Common processing | Loop through items | Read or update a named field |
| Typical combined form | An array of records | A record containing arrays/objects |

For example, one book is naturally described with an object, while a shelf of books is a list of book objects:

```js
const book = { title: "River Path", author: "A. Noor" };
const shelf = [book, { title: "Bright Sky", author: "L. Kim" }];
```

**Exercise:** Choose a structure for (1) one student's profile, (2) the ordered quiz questions, (3) a list of students with name and grade, and (4) a weekly timetable grid. Explain why each structure fits.

## 10. Practice project: product catalogue

Represent each product as an object and the catalogue as an array. This is a common way for an application to organize data that it later displays or searches.

```js
const catalogue = [
  { name: "Water bottle", price: 8, inStock: true },
  { name: "Backpack", price: 32, inStock: false },
  { name: "Notebook", price: 4, inStock: true }
];

const available = catalogue.filter(product => product.inStock);
const names = available.map(product => product.name);
console.log(names); // ["Water bottle", "Notebook"]
```

**Exercises:**

1. Add a product with `name`, `price`, and `inStock` properties.
2. Find and print the product named `Backpack`.
3. Create a new array containing only products costing less than 10.
4. Increase the price of one product and print the updated catalogue.
5. Calculate the total price of all products with `reduce`.

## Quick recap

- An object groups values under descriptive property names.
- Use `{}` for most objects; constructors are for more specific needs.
- Dot notation reads a known property; brackets support computed or unusual keys.
- Properties can hold values, arrays, nested objects, and methods.
- Object variables hold references; spread makes a shallow copy.
- Use arrays for ordered lists and objects for named descriptions; combine them to model real data.
