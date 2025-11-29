# JavaScript Revision Notes

## Chapter 1. Getting Started with JavaScript

## ECMAScript Version History

| Version     | Release Date |
| ----------- | ------------ |
| 1           | 1997-06-01   |
| 2           | 1998-06-01   |
| 3           | 1998-12-01   |
| E4X         | 2004-06-01   |
| 5           | 2009-12-01   |
| 5.1         | 2011-06-01   |
| 6 (ES2015)  | 2015-06-01   |
| 7 (ES2016)  | 2016-06-14   |
| 8 (ES2017)  | 2017-06-27   |
| 9 (ES2018)  | 2018-06-27   |
| 10 (ES2019) | 2019-06-27   |
| 11 (ES2020) | 2020-06-27   |
| 12 (ES2021) | 2021-06-22   |
| 13 (ES2022) | 2022-06-22   |
| 14 (ES2023) | 2023-06-27   |
| 15 (ES2024) | 2024-06-27   |

# 1.1 Using `console.log()`

### Purpose

Outputs messages to the browser or Node.js console. Used mainly for debugging.

### Basic Usage

```js
console.log("Hello, World!");
```

Returns `undefined` because it has no return value.

### Logging Variables

```js
var foo = "bar";
console.log(foo);
```

### Logging Multiple Values

```js
var a = "first";
var b = "second";
console.log("a:", a, "b:", b);
```

### Placeholders

```js
var greet = "Hello";
var who = "World";
console.log("%s, %s!", greet, who);
```

### Logging Objects

```js
console.log({
  Email: "",
  Groups: {},
  Id: 33,
  IsHiddenInUI: false,
  IsSiteAdmin: false,
  LoginName: "i:0#.w|virtualdomain\\user2",
  PrincipalType: 1,
  Title: "user2",
});
```

### Logging DOM Elements

```js
console.log(document.body);
```

# 1.2 Using the DOM API

### DOM Concept

DOM is an object representation of HTML or XML documents. JavaScript manipulates it via the DOM API.

### Selecting and Editing Elements

HTML:

```html
<p id="paragraph"></p>
```

JavaScript:

```js
document.getElementById("paragraph").textContent = "Hello, World";
```

### Creating Elements Dynamically

```js
var element = document.createElement("p");
element.textContent = "Hello, World";
document.body.appendChild(element);
```

### Timing Requirements

Manipulate DOM only after elements exist. Options:

- Place `<script>` at end of `<body>`.
- Use `window.onload`.
- Wrap code in `setTimeout(..., 0)` to requeue it.

# 1.3 Using `window.alert()`

### Purpose

Displays a modal popup with a message. Blocks user interaction until dismissed.

### Syntax

```js
alert("hello, world");
```

### Notes

- Blocks execution in most browsers.
- Considered poor UX for production.
- Blocked inside iframes in Chrome unless `sandbox="allow-modal"`.

# 1.4 Using `window.prompt()`

### Purpose

Asks user for input via a modal dialog.

### Syntax

```js
prompt(text, defaultValue);
```

### Example

```js
var age = prompt("How old are you?");
console.log(age);
```

### Return Values

- User pressed OK: returns a string.
- User pressed Cancel: returns `null` (Safari returns empty string).

### Notes

- Modal, blocks page interaction.
- Blocked in iframes without `allow-modal`.

# 1.5 Using `window.confirm()`

### Purpose

Displays a modal dialog with OK and Cancel for user confirmation.

### Syntax

```js
var result = window.confirm("Are you sure?");
```

### Typical Use

```js
if (window.confirm("Delete this?")) {
  deleteItem(itemId);
}
```

### Notes

- Returns boolean.
- Same iframe restrictions as `alert` and `prompt`.
- Use sparingly; modal dialogs are intrusive.

# 1.6 DOM API with Graphical Text (Canvas, SVG, Images)

## Using `<canvas>`

### Steps

1. Create a canvas.
2. Set size.
3. Get drawing context.
4. Draw text.
5. Append to page.

### Example

```js
var canvas = document.createElement("canvas");
canvas.width = 500;
canvas.height = 250;

var ctx = canvas.getContext("2d");
ctx.font = "30px Cursive";
ctx.fillText("Hello world!", 50, 50);

document.body.appendChild(canvas);
```

## Using SVG

### Example

```js
var svg = document.createElementNS("http://www.w3.org/2000/svg", "svg");
svg.width = 500;
svg.height = 50;

var text = document.createElementNS("http://www.w3.org/2000/svg", "text");
text.setAttribute("x", "0");
text.setAttribute("y", "50");
text.style.fontFamily = "Times New Roman";
text.style.fontSize = "50";
text.textContent = "Hello world!";

svg.appendChild(text);
document.body.appendChild(svg);
```

## Using an Image File

```js
var img = new Image();
img.src = "https://i.ytimg.com/vi/zecueq-mo4M/maxresdefault.jpg";
document.body.appendChild(img);
```

# Chapter 2. JavaScript Variables

## Overview

A variable stores a value that can be referenced and manipulated later.

- **variable_name**: identifier for the variable
- **=**: assignment operator
- **value**: assigned data. If no value is assigned, the variable is `undefined`

JavaScript variables can store any data type because JS uses dynamic typing.

## 2.1 Defining a Variable

### Example

```js
var myVariable = "This is a variable!";
```

This creates a variable using `var` and assigns a string.
A string is text data enclosed in quotes.

## 2.2 Using a Variable

### Reassigning Values

```js
var number1 = 5;
number1 = 3;
```

### Viewing the Value

```js
console.log(number1); // 3
alert(number1); // 3
```

### Basic Arithmetic

```js
number1 = number1 + 5; // 8
number1 = number1 - 6; // 2

var number2 = number1 * 10; // 20
var number3 = number2 / number1; // 10
```

### String Concatenation

```js
var myString = "I am a " + "string!";
// "I am a string!"
```

## 2.3 Types of Variables

### Important Correction

JavaScript does not have separate `integer`, `float`, `double`, or `long` types.
There is **one** number type: **Number** (64-bit floating point).
The examples below are still valid JS, but the comments in the original text were factually wrong.

### Valid Examples

```js
var myInteger = 12;
var myLong = 9310141419482;
var myFloat = 5.5;
var myDouble = 9310141419482.22;
```

All of these are the same type internally: **Number**.

### Other Primitive Types

```js
var myBoolean = true;
var myBoolean2 = false;

var myNotANumber = NaN;
var NaN_Example = 0 / 0; // NaN

var notDefined; // undefined (no value assigned)

var myNull = null; // intentional absence of value
```

### Undefined example

```js
alert(aRandomVariable); // undefined
```

## 2.4 Arrays and Objects

## Arrays

An array stores ordered values accessed by index.

```js
var myArray = []; // empty array

var favoriteFruits = ["apple", "orange", "strawberry"];
var carsInParkingLot = ["Toyota", "Ferrari", "Lexus"];
var employees = ["Billy", "Bob", "Joe"];
var primeNumbers = [2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31];
var randomVariables = [2, "any type works", undefined, null, true, 2.51];
```

### Accessing Elements

```js
myArray = ["zero", "one", "two"];
alert(myArray[0]); // "zero"

myArray = ["John Doe", "Billy"];
var elementNumber = 1;
alert(myArray[elementNumber]); // "Billy"
```

## Objects

Objects store key-value pairs, offering meaningful property names instead of numeric indexes.

```js
var myObject = {};

var john = {
  firstname: "John",
  lastname: "Doe",
  fullname: "John Doe",
};

var billy = {
  firstname: "Billy",
  lastname: undefined,
  fullname: "Billy",
};
```

### Accessing Object Properties

```js
alert(john.fullname); // "John Doe"
alert(billy.firstname); // "Billy"
```

### Why objects are better than arrays here

Instead of:

```js
["John Doe", "Billy"][0];
```

You get readable access:

```js
john.fullname;
billy.fullname;
```

## Chapter 3. Built-in Constants

# 3.1 null

### What null Represents

- `null` is a primitive value meaning **intentional absence of any object value**.
- It is **not** the same as `undefined`, although they are loosely equal.

### Comparisons

```js
null == undefined; // true  (loose equality)
null === undefined; // false (strict equality)
```

### typeof Quirk

```js
typeof null; // "object" (this is a long-standing bug in JS)
```

### Proper Check

```js
var a = null;
a === null; // true
```

# 3.2 Testing for NaN with isNaN()

### window.isNaN()

`isNaN()` attempts to convert the input to a number first, then checks if the result is `NaN`.
This implicit conversion causes unintuitive results.

### Examples

```js
isNaN(NaN); // true
isNaN(1); // false
isNaN(-2e-4); // false
isNaN(Infinity); // false

isNaN(true); // false (becomes 1)
isNaN(false); // false (becomes 0)
isNaN(null); // false (becomes 0)
isNaN(""); // false (becomes 0)
isNaN("45.3"); // false
isNaN("10$"); // true
isNaN("hello"); // true
isNaN(undefined); // true
isNaN(); // true (implicitly undefined)
isNaN({}); // true
isNaN(function () {}); // true
isNaN([1, 2]); // true (becomes "1,2")
```

### Arrays Specifically

`Number([])` → `0`
`Number([34])` → `34`
`Number([1,2])` → `NaN`

So:

```js
isNaN([]); // false
isNaN([34]); // false
isNaN([1, 2]); // true
```

## ES6+ Number.isNaN()

### Purpose

Fixes the flaws of `isNaN()` by **not converting** the value before checking.

### Rules

- Only `Number.isNaN(NaN)` returns `true`.
- Anything that is not a number returns `false`.

### Examples

```js
Number.isNaN(NaN); // true

Number.isNaN(1); // false
Number.isNaN("hello"); // false
Number.isNaN(undefined); // false
Number.isNaN([1, 2]); // false
Number.isNaN("10$"); // false
```

# 3.3 NaN

### Meaning

**NaN** stands for “Not a Number”.
Returned when a numeric operation cannot produce a valid number.

### Properties

```js
typeof NaN; // "number"
NaN === NaN; // false
NaN == NaN; // false
```

### Global Binding

```js
window.hasOwnProperty("NaN"); // true
```

### Never compare NaN using == or ===

Use:

```js
Number.isNaN(value);
```

# 3.4 undefined and null

### undefined

Represents the **absence of an assigned value**. It means "no value was provided".

### null

Represents the **intentional** absence of value.

### typeof

```js
typeof undefined; // "undefined"
typeof null; // "object" (quirk)
```

## When undefined appears

### 1. Declared but not assigned

```js
let foo;
foo; // undefined
```

### 2. Accessing non-existing object properties

```js
let obj = { a: "a" };
obj.b; // undefined
```

### 3. Function with no return

```js
function test() {}
test(); // undefined
```

### 4. Missing arguments

```js
function f(x) {
  return x;
}
f(); // undefined
```

### Global undefined

```js
window.undefined; // undefined
window.hasOwnProperty("undefined"); // true
```

### Pre-ES5 quirk

`undefined` used to be writable. Now it is read-only.

# 3.5 Infinity and -Infinity

### Meaning

Represents mathematical positive or negative infinity.

```js
1 / 0; // Infinity
1 / -0; // -Infinity
```

### Properties

```js
Infinity === Number.POSITIVE_INFINITY; // true
-Infinity === Number.NEGATIVE_INFINITY; // true
```

### Examples

```js
Infinity > 1e308; // true
23 / Infinity; // 0

var a = 0,
  b = -0;
a === b; // true
1 / a === 1 / b; // false (Infinity vs -Infinity)
```

# 3.6 Number Constants

### Useful Number Constants

```js
Number.MAX_VALUE; // 1.7976931348623157e+308
Number.MIN_VALUE; // 5e-324

Number.MAX_SAFE_INTEGER; // 9007199254740991
Number.MIN_SAFE_INTEGER; // -9007199254740991

Number.EPSILON; // 2.220446049250313e-16

Number.POSITIVE_INFINITY; // Infinity
Number.NEGATIVE_INFINITY; // -Infinity
Number.NaN; // NaN
```

### Notes

- Operations outside the safe integer range may produce inaccurate results.
- `Number.EPSILON` is useful for floating-point comparison.

# 3.7 Operations that Return NaN

### NaN occurs when math operations use invalid numeric operands.

Examples:

```js
"b" * 3; // NaN
"cde" - "e"; // NaN
[1, 2, 3] * 2; // NaN
```

### Exception: Single-element arrays

```js
[2] * [3]; // 6 (both converted to numbers)
```

### Remember

`+` with strings concatenates:

```js
"a" + "b"; // "ab"
```

### Zero divided by zero

```js
0 / 0; // NaN
```

# 3.8 Math Functions that Return NaN

### Non-numeric Input

```js
Math.floor("a"); // NaN
```

### Invalid Domain Input

Square root of a negative number:

```js
Math.sqrt(-1); // NaN
```

# Chapter 4. Comments

# 4.1 Using Comments

Comments allow you to annotate code, explain logic, disable execution, or leave reminders. JavaScript supports two native comment styles.

## Single-line Comments (`//`)

Everything after `//` on the same line is ignored by the JavaScript engine.

```js
function elementAt(event) {
  // Gets the element at the event's coordinates
  return document.elementFromPoint(event.clientX, event.clientY);
}

// TODO: write more cool stuff!
```

## Multi-line Comments (`/* ... */`)

Everything between `/*` and `*/` is ignored, even across multiple lines.

```js
/*
Gets the element from Event coordinates.
Usage:
var clickedEl = someEl.addEventListener("click", elementAt, false);
*/
function elementAt(event) {
  return document.elementFromPoint(event.clientX, event.clientY);
}

/* TODO: write more useful comments! */
```

Use multi-line comments for blocks of explanation, documentation, or temporarily disabling multiple lines.

# 4.2 HTML Comments in JavaScript (Bad Practice)

Historically, HTML comments were sometimes used in JavaScript for compatibility with ancient browsers. Modern JavaScript should **never** rely on this.

## HTML-style Opening Comment (`<!--`)

If used at the beginning of a JavaScript line, the JS engine treats it as a comment starter.
The closing `-->` is ignored by JavaScript.

```js
<!-- A single-line comment
<!-- --> Same effect as //
```

This behavior exists for backward compatibility and should not be used today.

## Legacy Example: Hiding JS from Non-JS Browsers

Old browsers that didn’t understand `<script>` tags would display JavaScript as text. Developers hid the JS using HTML comment markers:

```html
<script type="text/javascript">
  <!--
  // JavaScript code here
  // -->
</script>
```

This is obsolete and should never appear in modern code.

## Using `-->` at Line Start in JavaScript

If a line begins with `-->`, JavaScript ignores everything after it:

```js
--> unreachable JS code
```

Again, this is outdated behavior.

# HTML–JavaScript Hybrid Exploit (For Understanding Only)

Because HTML comments and JS comments behave differently, developers once used them to create files that could be interpreted as HTML or JavaScript depending on context.

Example:

```js
<!--
self.postMessage('reached JS "file"');
/*
-->
<!DOCTYPE html>
<script>
  var w1 = new Worker('#1');
  w1.onmessage = function(e) {
    console.log(e.data); // 'reached JS "file"'
  };
</script>
<!--
*/
-->
```

### What happens:

- When parsed as **HTML**, everything between `<!--` and `-->` is treated as an HTML comment and ignored.
- When parsed as **JavaScript**, only lines beginning with `<!--` or `-->` are ignored.
  JavaScript continues reading subsequent lines until it hits standard JS comment syntax (`/* ... */`).

This is purely historical, not something you should ever write.

# Chapter 5. Console

The browser (and Node) debugging console exposes a `console` object with many utility methods for logging, timing, grouping, inspecting, and debugging runtime behavior. Behavior and available methods vary by environment and browser, so use feature checks when needed.

## Common `console` methods

Typical methods you will see (not exhaustive and may differ by runtime):

```
assert, clear, count, debug, dir, dirxml, error, group, groupCollapsed,
groupEnd, info, log, table, time, timeEnd, timeStamp, trace, warn
```

Note: Chrome exposes additional internals like `console.memory`. Never rely on non-standard features in production.

## Opening the Console (quick shortcuts)

- **Chrome**

  - Windows / Linux: `Ctrl + Shift + J` or `F12` then Console tab
  - macOS: `Cmd + Option + J`

- **Firefox**

  - Windows / Linux: `Ctrl + Shift + K` or `F12` then Console tab
  - macOS: `Cmd + Option + K`

- **Edge / IE**

  - `F12` then Console tab

- **Safari**

  - Enable Develop menu in Preferences, then `Develop → Show Error Console` or `⌘ + Option + C`

- **Opera**

  - `Ctrl + Shift + I` then Console tab

## Compatibility & defensive patterns

In old IE versions (and some limited environments) `console` may be undefined unless dev tools are open. Prevent fatal errors with a guard or shim:

```js
// Guard before using:
if (typeof window.console !== "undefined") {
  console.log("Hello World");
}

// Lightweight shim (silences all logs)
if (!window.console) {
  console = { log() {} };
}
```

The shim stops all console output; extend it if you need methods like `dir`, `warn`, etc.

## 5.1 Measuring time `console.time()` / `console.timeEnd()`

Start/stop timers by a `label`. Multiple `timeEnd()` calls with the same label report elapsed time since the original `time()`.

```js
console.time("response in");
/* do work */
console.timeEnd("response in"); // response in: 123.456ms
```

You can call `timeEnd('label')` repeatedly to get successive elapsed times since the `time('label')` call.

Example: profiling nested loops or async response times.

## 5.2 Formatting console output

`console` supports printf-like tokens:

- `%s` → string
- `%i` or `%d` → integer
- `%f` → floating point
- `%o` → expandable DOM element
- `%O` → expandable JavaScript object
- `%c` → apply CSS to text (Chrome/Chromium-based consoles)

```js
console.log("%s has %d points", "Sam", 100);
console.log("%o", document.body);
console.log("%cHello world!", "color: blue; font-size: 16px");
```

`%c` accepts multiple occurrences; each `%c` consumes one CSS argument.

**Caveat:** styling is purely cosmetic in devtools and not portable to all consoles.

## 5.3 Groups `console.group()`, `console.groupCollapsed()`, `console.groupEnd()`

Indent and collapse related logs:

```js
console.group("Init");
console.log("step 1");
console.groupCollapsed("subgroup");
console.log("sub step");
console.groupEnd();
console.groupEnd();
```

`groupCollapsed` starts collapsed; `group` starts expanded. Use groups to keep console output readable.

## 5.4 Basic logging and variants

- `console.log(...)` — general logging, accepts multiple args
- `console.info(...)` — informational (may show an icon)
- `console.warn(...)` — warnings (often highlighted)
- `console.error(...)` — errors (often red or treated specially)

All accept objects, arrays, functions, Dates, etc. Many consoles allow expanding object trees interactively.

**Tip:** remove or guard verbose logs in production builds.

## 5.5 Stack traces `console.trace()`

Prints the current stack trace (useful to see call paths):

```js
function a() {
  b();
}
function b() {
  console.trace("trace here");
}
a();
```

You can also inspect `new Error().stack` for programmatic access.

## 5.6 Tabular output `console.table()`

Displays arrays or objects as a table, optionally restricting columns:

```js
console.table(["Hello", "world"]);
// or
console.table({ foo: "bar", bar: "baz" });
// array of objects with selected columns:
console.table(personArr, ["name", "personId"]);
```

Useful for quick inspection of homogeneous collections.

## 5.7 Counting `console.count([label])`

Keeps an internal counter per label and logs `label: X`. Useful for seeing how often code paths execute.

```js
console.count("loop");
// => loop: 1
console.count("loop");
// => loop: 2
console.count(); // uses empty string label
```

Note: the label normalization rules vary by engine (`Number('42.3')` vs `'42.3'` may produce same label in some consoles).

## 5.8 Clearing the console `console.clear()`

Clears the console output. Some environments print a small marker like "Console was cleared".

```js
console.clear();
```

## 5.9 Inspecting objects `console.dir()` and `console.dirxml()`

- `console.dir(obj)` — shows a navigable list of object properties (often better for plain JS objects).
- `console.dirxml(node)` — prints an XML/HTML-like representation for DOM nodes; otherwise prints object representation.

```js
console.dir({ foo: { bar: "data" } });
console.dirxml(document);
```

Behavior differs across browsers; try both when inspecting complex structures.

## 5.10 Assertions `console.assert()`

Logs an error message if the assertion expression is falsy. It does not throw (in browsers) so execution continues.

```js
console.assert(1 === 2, "this should never happen");
```

Additional arguments after the assertion are printed only when the assertion fails.

**Caveat:** `console.assert` is not a replacement for test-framework assertions since it usually won’t stop execution. Node.js throws an `AssertionError` only in that environment.

## Practical tips & best practices

- Avoid leaving verbose `console.log` calls in production code. Use build tools to strip them or guard with environment checks.
- Prefer `console.error()` for error conditions and `console.warn()` for recoverable issues.
- Use `console.time()`/`timeEnd()` for quick performance checks; use dedicated profilers for deeper analysis.
- Use `console.table()` for readable tabular data.
- Wrap console usage with feature checks when supporting legacy environments.
- Know that consoles are developer tools — formatting and features are implementation-specific; write code that doesn’t depend on console side-effects.

# Chapter 6. Datatypes in JavaScript

JavaScript's type system is flexible but full of quirks. This chapter summarizes the correct, practical ways to inspect and understand values.

## 6.1 `typeof`

`typeof` is the built-in operator for checking the type of a value. It works well for primitives but is inconsistent for some objects.

### Results

#### 1. Strings

```js
typeof "String"; // "string"
typeof Date(2011, 1, 1); // "string" because Date() without new returns a string
```

#### 2. Numbers

```js
typeof 42; // "number"
```

#### 3. Boolean

```js
typeof true; // "boolean"
```

#### 4. Object (overly broad)

```js
typeof {}; // "object"
typeof []; // "object"
typeof null; // "object"       // historical bug
typeof /aaa/; // "object"
typeof Error(); // "object"
```

#### 5. Function

```js
typeof function () {}; // "function"
```

#### 6. Undefined

```js
var x;
typeof x; // "undefined"
```

### Key issue

`typeof` lumps many different object categories into `"object"` and incorrectly reports `null` as `"object"`.

## 6.2 Finding an Object’s Class (`instanceof` and `constructor`)

### Using `instanceof`

Use `instanceof` to check whether an object was created by a constructor or its prototype chain.

```js
function sum(...args) {
  if (args.length === 1) {
    const [first] = args;
    if (first instanceof Array) {
      return sum(...first);
    }
  }
  return args.reduce((a, b) => a + b);
}

console.log(sum(1, 2, 3)); // 6
console.log(sum([1, 2, 3])); // 6
console.log(sum(4)); // 4
```

### Primitive caveat

Primitives are **not** instances of wrapper constructors:

```js
2 instanceof Number; // false
"abc" instanceof String; // false
true instanceof Boolean; // false
Symbol() instanceof Symbol; // false
```

### Using `.constructor`

Every value except `null` and `undefined` has a `.constructor` reference:

```js
[].constructor === Array; // true
[].constructor === Object; // false
```

This does not check inheritance, unlike `instanceof`.

### Safe example function:

```js
function isNumber(value) {
  if (value === null || value === undefined) return false;
  return value.constructor === Number;
}

isNumber(null); // false
isNumber("abc"); // false
isNumber(0); // true
isNumber(Number("10")); // true
isNumber(NaN); // true
```

## 6.3 Getting Object Type with `Object.prototype.toString.call()`

This is the **most reliable** way to get the internal `[[Class]]` of a value.
It returns strings like `"[object Array]"`.

### Examples

#### 1. String

```js
Object.prototype.toString.call("String");
// "[object String]"
```

#### 2. Number

```js
Object.prototype.toString.call(42);
// "[object Number]"
```

#### 3. Boolean

```js
Object.prototype.toString.call(true);
// "[object Boolean]"
```

#### 4. Object

```js
Object.prototype.toString.call({});
// "[object Object]"
```

#### 5. Function

```js
Object.prototype.toString.call(function () {});
// "[object Function]"
```

#### 6. Date

```js
Object.prototype.toString.call(new Date());
// "[object Date]"
```

#### 7. RegExp

```js
Object.prototype.toString.call(/foo/);
// "[object RegExp]"
```

#### 8. Array

```js
Object.prototype.toString.call([]);
// "[object Array]"
```

#### 9. Null

```js
Object.prototype.toString.call(null);
// "[object Null]"
```

#### 10. Undefined

```js
Object.prototype.toString.call(undefined);
// "[object Undefined]"
```

#### 11. Error

```js
Object.prototype.toString.call(Error());
// "[object Error]"
```

## Summary of Type-Checking Methods

| Method                           | Good for                             | Weaknesses                                         |
| -------------------------------- | ------------------------------------ | -------------------------------------------------- |
| `typeof`                         | Primitives, functions                | `null` bug, arrays/objects indistinguishable       |
| `instanceof`                     | Object instances, inheritance checks | Fails with primitives, problems across iframes     |
| `.constructor`                   | Direct constructor equality          | Cannot detect subclasses, fails for null/undefined |
| `Object.prototype.toString.call` | Precise internal class               | Verbose, not widely known by beginners             |

This is the hierarchy you should fall back on when accuracy matters.
