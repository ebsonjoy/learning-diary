# JavaScript Type Coercion - Examples with Output and Explanation

---

### 1. `console.log('a' + 9)`  
✅ **Output:** `'a9'`  
🧠 **Why:**  
The `+` operator is used for string concatenation when one operand is a string.  
Here, `'a'` is a string, so `9` is converted to `'9'`, and the result is `'a9'`.

---

### 2. `console.log('3' + 9)`  
✅ **Output:** `'39'`  
🧠 **Why:**  
Again, `'3'` is a string, and `+` joins it with `9` (converted to `'9'`), so the result is `'39'`.

---

### 3. `console.log('a' - 1)`  
✅ **Output:** `NaN`  
🧠 **Why:**  
The `-` operator expects numbers.  
Since `'a'` is not a number, JavaScript cannot convert it and returns `NaN` (Not a Number).

---

### 4. `console.log(1 + '2')`  
✅ **Output:** `'12'`  
🧠 **Why:**  
Number `1` is added to string `'2'` using `+`, so both are treated as strings.  
Result: `'12'`.

---

### 5. `console.log(1 - '2')`  
✅ **Output:** `-1`  
🧠 **Why:**  
`'2'` is a string, but `-` forces it to be converted to number `2`.  
So, `1 - 2 = -1`.

---

### 6. `console.log(1 + true)`  
✅ **Output:** `2`  
🧠 **Why:**  
`true` is converted to `1`, so `1 + 1 = 2`.

---

### 7. `console.log('5' - true)`  
✅ **Output:** `4`  
🧠 **Why:**  
`'5'` becomes `5`, and `true` becomes `1`.  
So, `5 - 1 = 4`.

---

### 8. `console.log('5' + true)`  
✅ **Output:** `'5true'`  
🧠 **Why:**  
`'5'` is a string, and `true` becomes `'true'`.  
So, string concatenation gives `'5true'`.

---

### 9. `console.log(undefined + 1)`  
✅ **Output:** `NaN`  
🧠 **Why:**  
`undefined` cannot be converted to a number (it becomes `NaN`),  
and `NaN + 1` is still `NaN`.

---

### 10. `console.log(null + 1)`  
✅ **Output:** `1`  
🧠 **Why:**  
`null` is treated as `0` in numeric operations.  
So, `0 + 1 = 1`.

---

### 11. `console.log(false + 10)`  
✅ **Output:** `10`  
🧠 **Why:**  
`false` is converted to `0`, so `0 + 10 = 10`.

---

### 12. `console.log(true + '1')`  
✅ **Output:** `'true1'`  
🧠 **Why:**  
`true` becomes `'true'` when added to a string,  
so `'true' + '1'` = `'true1'`.

---

### 13. `console.log('10' - '4')`  
✅ **Output:** `6`  
🧠 **Why:**  
Both strings are converted to numbers,  
so `10 - 4 = 6`.

---

### 14. `console.log('10' + '4')`  
✅ **Output:** `'104'`  
🧠 **Why:**  
Both operands are strings, and `+` does string joining,  
so `'10' + '4'` = `'104'`.

---

### 15. `console.log('5' * '2')`  
✅ **Output:** `10`  
🧠 **Why:**  
`*` forces both `'5'` and `'2'` to be numbers.  
So, `5 * 2 = 10`.

---

### 16. `console.log('6' / '2')`  
✅ **Output:** `3`  
🧠 **Why:**  
The `/` operator forces both operands to be numbers.  
So `'6'` → 6 and `'2'` → 2, and `6 / 2 = 3`.

---

### 17. `console.log('6' % '4')`  
✅ **Output:** `2`  
🧠 **Why:**  
`'6'` and `'4'` are both converted to numbers.  
`6 % 4 = 2` (remainder when 6 is divided by 4).

---

### 18. `console.log('10' * null)`  
✅ **Output:** `0`  
🧠 **Why:**  
`null` becomes `0`, and `'10'` becomes `10`.  
So, `10 * 0 = 0`.

---

### 19. `console.log('5' - undefined)`  
✅ **Output:** `NaN`  
🧠 **Why:**  
`'5'` becomes `5`, but `undefined` becomes `NaN`.  
So, `5 - NaN = NaN`.

---

### 20. `console.log(true + false)`  
✅ **Output:** `1`  
🧠 **Why:**  
`true` → 1, `false` → 0. So `1 + 0 = 1`.

---

### 21. `console.log('2' * '3')`  
✅ **Output:** `6`  
🧠 **Why:**  
Both strings are converted to numbers.  
`2 * 3 = 6`.

---

### 22. `console.log('2' * 'a')`  
✅ **Output:** `NaN`  
🧠 **Why:**  
`'2'` → 2, but `'a'` is not a number → `NaN`.  
So, `2 * NaN = NaN`.

---

### 23. `console.log(0 + '0')`  
✅ **Output:** `'00'`  
🧠 **Why:**  
`0` is a number, `'0'` is a string.  
`+` turns both into strings → `'0' + '0' = '00'`.

---

### 24. `console.log('' + 0)`  
✅ **Output:** `'0'`  
🧠 **Why:**  
Empty string + number → string.  
`'' + 0 = '0'`.

---

### 25. `console.log(0 - '')`  
✅ **Output:** `0`  
🧠 **Why:**  
`''` is converted to `0`, so `0 - 0 = 0`.

---

### 26. `console.log('10' - true)`  
✅ **Output:** `9`  
🧠 **Why:**  
`'10'` → 10, `true` → 1, so `10 - 1 = 9`.

---

### 27. `console.log('10' + true)`  
✅ **Output:** `'10true'`  
🧠 **Why:**  
String `'10'` + `'true'` → `'10true'`.

---

### 28. `console.log(null + true)`  
✅ **Output:** `1`  
🧠 **Why:**  
`null` → 0, `true` → 1, so `0 + 1 = 1`.

---

### 29. `console.log([] + {})`  
✅ **Output:** `'[object Object]'`  
🧠 **Why:**  
Empty array (`[]`) becomes `''`  
Empty object (`{}`) becomes `'[object Object]'`  
So: `'' + '[object Object]' = '[object Object]'`

---

### 30. `console.log({} + [])`  
✅ **Output:** `0` (or `'[object Object]'` depending on context)  
🧠 **Why:**  
In some contexts, `{}` is treated as a block, and `+[]` is evaluated.  
`+[]` = 0, so result = `0`.  
But if `{}` is treated as an object: `'[object Object]' + '' = '[object Object]'`

---

---

### 31. `console.log(3 + '5' + 0)`  
✅ **Output:** `'350'`  
🧠 **Why:**  
- `3 + '5'` → `'35'` (number + string = string)
- `'35' + 0` → `'350'` (string + number = string)

So, the entire expression results in `'350'`.

---

### 32. `console.log('a' + '4' + '8')`  
✅ **Output:** `'a48'`  
🧠 **Why:**  
All operands are strings.  
- `'a' + '4'` → `'a4'`  
- `'a4' + '8'` → `'a48'`

So the result is `'a48'`.

---

### 33. `console.log(3 + 5 + '0')`  
✅ **Output:** `'80'`  
🧠 **Why:**  
- `3 + 5` → `8` (number + number = number)
- `8 + '0'` → `'80'` (number + string = string)

So the result is `'80'`.

---

### 34. `console.log('a' + 4 + 8)`  
✅ **Output:** `'a48'`  
🧠 **Why:**  
- `'a' + 4` → `'a4'` (string + number = string)
- `'a4' + 8` → `'a48'`

So the final result is `'a48'`.

---

### 35. `console.log(4 + 8 + 'a')`  
✅ **Output:** `'12a'`  
🧠 **Why:**  
- `4 + 8` → `12`  
- `12 + 'a'` → `'12a'` (number + string = string)

So the result is `'12a'`.

---

