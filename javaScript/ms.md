# JavaScript Built-in Methods Cheat Sheet

## 🔹 Legend
- `(value)` = required
- `(start?)` = optional
- `(...items)` = variable number of arguments

---

## 🔸 String Methods

| Method | Description | Arguments |
|--------|-------------|-----------|
| `slice(start, end?)` | Returns part of the string | `(start: number, end?: number)` |
| `substring(start, end?)` | Similar to slice, but no negative values | `(start: number, end?: number)` |
| `substr(start, length?)` | Deprecated. Extracts substring | `(start: number, length?: number)` |
| `charAt(index)` | Returns character at index | `(index: number)` |
| `indexOf(searchValue, start?)` | First index of match | `(searchValue: string, start?: number)` |
| `lastIndexOf(searchValue, start?)` | Last index of match | `(searchValue: string, start?: number)` |
| `includes(searchValue, start?)` | Checks if string contains value | `(searchValue: string, start?: number)` |
| `startsWith(searchValue, start?)` | Checks if string starts with value | `(searchValue: string, start?: number)` |
| `endsWith(searchValue, length?)` | Checks if ends with value | `(searchValue: string, length?: number)` |
| `replace(searchValue, newValue)` | Replaces first occurrence | `(searchValue: string\|RegExp, newValue: string)` |
| `replaceAll(searchValue, newValue)` | Replaces all occurrences | `(searchValue: string\|RegExp, newValue: string)` |
| `split(separator, limit?)` | Splits string into array | `(separator: string\|RegExp, limit?: number)` |
| `toUpperCase()` | Converts to uppercase | `()` |
| `toLowerCase()` | Converts to lowercase | `()` |
| `trim()` | Removes whitespace | `()` |
| `repeat(count)` | Repeats string | `(count: number)` |
| `padStart(targetLength, padString?)` | Pads from start | `(targetLength: number, padString?: string)` |
| `padEnd(targetLength, padString?)` | Pads from end | `(targetLength: number, padString?: string)` |

---

## 🔸 Array Methods

| Method | Description | Arguments |
|--------|-------------|-----------|
| `push(...items)` | Adds elements to end | `(...items: any[])` |
| `pop()` | Removes last item | `()` |
| `shift()` | Removes first item | `()` |
| `unshift(...items)` | Adds elements to beginning | `(...items: any[])` |
| `slice(start?, end?)` | Returns portion of array | `(start?: number, end?: number)` |
| `splice(start, deleteCount?, ...items)` | Removes/adds elements | `(start: number, deleteCount?: number, ...items: any[])` |
| `concat(...arrays)` | Combines arrays | `(...arrays: any[])` |
| `join(separator?)` | Joins elements into string | `(separator?: string)` |
| `includes(value, fromIndex?)` | Checks if array contains value | `(value: any, fromIndex?: number)` |
| `indexOf(value, fromIndex?)` | First index of value | `(value: any, fromIndex?: number)` |
| `lastIndexOf(value, fromIndex?)` | Last index of value | `(value: any, fromIndex?: number)` |
| `find(callback)` | Finds first matching item | `(callback: (item, index, array) => boolean)` |
| `findIndex(callback)` | Finds index of first match | `(callback: (item, index, array) => boolean)` |
| `filter(callback)` | Filters array | `(callback: (item, index, array) => boolean)` |
| `map(callback)` | Transforms array | `(callback: (item, index, array) => any)` |
| `reduce(callback, initialValue?)` | Reduces to single value | `(callback: (acc, item, index, array) => any, initialValue?: any)` |
| `every(callback)` | Returns true if all match condition | `(callback: (item, index, array) => boolean)` |
| `some(callback)` | Returns true if any match condition | `(callback: (item, index, array) => boolean)` |
| `reverse()` | Reverses array | `()` |
| `sort(compareFn?)` | Sorts array | `(compareFn?: (a, b) => number)` |
| `flat(depth?)` | Flattens nested array | `(depth?: number)` |
| `flatMap(callback)` | Map + flatten one level | `(callback: (item, index, array) => any[])` |

---

## 🔸 Object Methods

| Method | Description | Arguments |
|--------|-------------|-----------|
| `Object.keys(obj)` | Returns array of keys | `(obj: object)` |
| `Object.values(obj)` | Returns array of values | `(obj: object)` |
| `Object.entries(obj)` | Returns key-value pairs | `(obj: object)` |
| `Object.assign(target, ...sources)` | Copies properties | `(target: object, ...sources: object[])` |
| `Object.hasOwn(obj, prop)` | Checks if property exists | `(obj: object, prop: string)` |
| `delete obj.prop` | Deletes a property | `(prop: string)` |
| `'prop' in obj` | Checks if property exists | `(prop: string, obj: object)` |

---

## 🔸 Math Methods

| Method | Description | Arguments |
|--------|-------------|-----------|
| `Math.round(x)` | Rounds to nearest integer | `(x: number)` |
| `Math.ceil(x)` | Rounds up | `(x: number)` |
| `Math.floor(x)` | Rounds down | `(x: number)` |
| `Math.abs(x)` | Absolute value | `(x: number)` |
| `Math.sqrt(x)` | Square root | `(x: number)` |
| `Math.pow(x, y)` | Power (x^y) | `(x: number, y: number)` |
| `Math.max(...values)` | Largest of values | `(...values: number[])` |
| `Math.min(...values)` | Smallest of values | `(...values: number[])` |
| `Math.random()` | Random number between 0–1 | `()` |

---

## 🔸 JSON Methods

| Method | Description | Arguments |
|--------|-------------|-----------|
| `JSON.stringify(value, replacer?, space?)` | Converts object to JSON string | `(value: any, replacer?: function \| array, space?: number \| string)` |
| `JSON.parse(text, reviver?)` | Converts JSON string to object | `(text: string, reviver?: function)` |

---

## 🔸 Number Methods

| Method | Description | Arguments |
|--------|-------------|-----------|
| `Number.toFixed(digits)` | Fixed decimal places | `(digits: number)` |
| `Number.toString(radix?)` | Converts to string | `(radix?: number)` |
| `parseInt(string, radix?)` | Converts string to int | `(string: string, radix?: number)` |
| `parseFloat(string)` | Converts string to float | `(string: string)` |
| `isNaN(value)` | Checks if value is NaN | `(value: any)` |
| `isFinite(value)` | Checks if finite number | `(value: any)` |

---

## 🔸 Date Methods

| Method | Description | Arguments |
|--------|-------------|-----------|
| `new Date(value?)` | Creates a Date object | `(value?: string \| number)` |
| `getFullYear()` | Gets year | `()` |
| `getMonth()` | Gets month | `()` |
| `getDate()` | Gets date | `()` |
| `getDay()` | Gets day of week | `()` |
| `getHours()` | Gets hour | `()` |
| `getMinutes()` | Gets minutes | `()` |
| `setFullYear(year)` | Sets year | `(year: number)` |
| `toISOString()` | Returns ISO string | `()` |
| `toLocaleDateString(locale?, options?)` | Local string | `(locale?: string, options?: object)` |

---


