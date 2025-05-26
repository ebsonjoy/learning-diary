# 🔸 JavaScript Data Types

JavaScript has 8 basic data types:

| Type       | Description                                      | Example               |
|------------|--------------------------------------------------|-----------------------|
| `Number`   | Any number, including floating-point and special values like `NaN` and `Infinity` | `42`, `3.14`, `NaN`    |
| `String`   | Sequence of characters                           | `'Hello'`, `"World"`  |
| `Boolean`  | Logical value: `true` or `false`                 | `true`, `false`       |
| `undefined`| Value not assigned to a variable                 | `let x;`              |
| `null`     | Represents "no value"                             | `let y = null;`       |
| `BigInt`   | Large integers beyond `Number.MAX_SAFE_INTEGER`  | `123n`, `BigInt(9007199254740991)` |
| `Symbol`   | Unique identifier                                | `Symbol('id')`        |
| `Object`   | Collection of properties                         | `{ name: "John" }`, `[1,2,3]` |

Special Objects:
- `Array` is a type of `object`
- `Function` is a type of `object`
- `Date`, `RegExp`, etc., are built-in object types

Use `typeof` to check type:
```js
typeof 123         // "number"
typeof 'abc'       // "string"
typeof true        // "boolean"
typeof undefined   // "undefined"
typeof null        // "object" (quirky JS behavior)
typeof {}          // "object"
typeof []          // "object"
typeof function(){} // "function"
```

---