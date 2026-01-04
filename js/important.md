# JavaScript Array Methods - Interview Comparison Guide

## 1. **Mutating vs Non-Mutating Methods**

### Mutating Methods (Modify Original Array)
- `push()`, `pop()`, `shift()`, `unshift()`, `splice()`, `sort()`, `reverse()`, `fill()`, `copyWithin()`

### Non-Mutating Methods (Return New Array/Value)
- `slice()`, `map()`, `filter()`, `reduce()`, `concat()`, `join()`, `includes()`, `indexOf()`, `find()`, `some()`, `every()`

---

## 2. **Adding/Removing Elements**

| Method | Returns | Mutates | Use Case |
|--------|---------|---------|----------|
| `push()` | New length | ✅ | Add to end |
| `pop()` | Removed element | ✅ | Remove from end |
| `unshift()` | New length | ✅ | Add to start |
| `shift()` | Removed element | ✅ | Remove from start |
| `splice(start, deleteCount, ...items)` | Removed elements array | ✅ | Add/remove/replace anywhere |
| `slice(start, end)` | New array | ❌ | Get portion without modifying |
| `concat(...arrays)` | New array | ❌ | Merge arrays |

**Interview Tip:** Know the return values - `push()` returns length, not the element. `splice()` returns removed elements, not the remaining array.

---

## 3. **Iteration Methods (Callbacks)**

| Method | Returns | Mutates | Key Feature |
|--------|---------|---------|-------------|
| `map()` | New array (transformed) | ❌ | Transform each element |
| `filter()` | New array (subset) | ❌ | Keep elements matching condition |
| `reduce()` | Single value | ❌ | Accumulate to single value |
| `forEach()` | undefined | ❌ | Execute for side effects only |
| `find()` | First matching element | ❌ | Get first match |
| `findIndex()` | Index of first match | ❌ | Get index of first match |
| `some()` | Boolean | ❌ | Check if ANY match condition |
| `every()` | Boolean | ❌ | Check if ALL match condition |

**Interview Example:**
```javascript
const nums = [1, 2, 3, 4];

map(x => x * 2)        // [2, 4, 6, 8]
filter(x => x > 2)     // [3, 4]
reduce((acc, x) => acc + x, 0)  // 10
find(x => x > 3)       // 4
some(x => x > 3)       // true
every(x => x > 0)      // true
```

---

## 4. **Search Methods**

| Method | Returns | Case Sensitive | Key Difference |
|--------|---------|----------------|-----------------|
| `indexOf(element)` | Index or -1 | Yes (with ===) | Uses strict equality |
| `lastIndexOf(element)` | Last index or -1 | Yes (with ===) | Searches from end |
| `includes(element)` | Boolean | Yes | Can't find NaN (except includes can) |
| `find(callback)` | Element or undefined | N/A | Uses custom logic |
| `findIndex(callback)` | Index or -1 | N/A | Uses custom logic |

**Interview Tip:** `includes()` can find `NaN`, but `indexOf()` cannot because `NaN !== NaN`.

---

## 5. **Ordering Methods**

| Method | Mutates | Returns | Key Point |
|--------|---------|---------|-----------|
| `sort(compareFn)` | ✅ | Sorted array | Mutates original! Converts to strings by default |
| `reverse()` | ✅ | Reversed array | Mutates original |

**Interview Critical Knowledge:**
```javascript
// Default sort converts to strings
[10, 5, 40].sort()  // [10, 40, 5] ❌ Wrong!

// Use comparator
[10, 5, 40].sort((a, b) => a - b)  // [5, 10, 40] ✅

// For objects
objects.sort((a, b) => a.age - b.age)
```

---

## 6. **String Conversion**

| Method | Returns | Key Feature |
|--------|---------|-------------|
| `join(separator)` | String | Converts array to string, default separator is comma |
| `toString()` | String | Same as join() with comma separator |

```javascript
['a', 'b', 'c'].join('-')  // "a-b-c"
['a', 'b', 'c'].join()     // "a,b,c"
```

---

## 7. **Utility Methods**

| Method | Mutates | Returns | Use Case |
|--------|---------|---------|----------|
| `flat(depth)` | ❌ | New flattened array | Flatten nested arrays |
| `flatMap(callback)` | ❌ | Flattened & mapped array | Map then flatten |
| `fill(value, start, end)` | ✅ | Modified array | Fill with constant value |
| `copyWithin(target, start, end)` | ✅ | Modified array | Copy part to another location |

```javascript
[1, [2, 3], [4, [5]]].flat()      // [1, 2, 3, 4, [5]]
[1, [2, 3], [4, [5]]].flat(2)     // [1, 2, 3, 4, 5]

[1, 2, 3].flatMap(x => [x, x*2])  // [1, 2, 2, 4, 3, 6]
```

---

## 8. **Common Interview Questions & Answers**

### Q: What's the difference between `map()` and `forEach()`?
**A:** `map()` returns a new array, `forEach()` returns undefined and is for side effects only.

### Q: How do you deep copy an array?
**A:** `JSON.parse(JSON.stringify(arr))` or `structuredClone(arr)` (newer, handles more types)

### Q: Difference between `filter()` and `find()`?
**A:** `filter()` returns ALL matching elements, `find()` returns FIRST match only.

### Q: What does `reduce()` return if array is empty?
**A:** If no initialValue provided, it throws error. With initialValue, it returns that value.

### Q: Can you chain array methods? Give example.
**A:** Yes! `arr.filter(x => x > 5).map(x => x * 2).reduce((a, b) => a + b)`

### Q: What's faster - `some()` or `filter().length > 0`?
**A:** `some()` is faster because it stops at first match; `filter()` checks entire array.

### Q: Does `splice()` affect performance?
**A:** Yes, slower than `filter()` for large arrays because it shifts all remaining elements.

---

## 9. **Quick Reference Table**

| Method | Mutates | Returns | Time Complexity |
|--------|---------|---------|-----------------|
| push() | ✅ | Length | O(1) |
| pop() | ✅ | Element | O(1) |
| shift() | ✅ | Element | O(n) |
| unshift() | ✅ | Length | O(n) |
| splice() | ✅ | Array | O(n) |
| slice() | ❌ | Array | O(n) |
| map() | ❌ | Array | O(n) |
| filter() | ❌ | Array | O(n) |
| find() | ❌ | Element | O(n) |
| includes() | ❌ | Boolean | O(n) |
| sort() | ✅ | Array | O(n log n) |
| reduce() | ❌ | Value | O(n) |

---

## 10. **Performance Tips for Interviews**

1. **Use `some()` instead of `filter().length > 0`** - Early termination
2. **Use `includes()` instead of `indexOf() !== -1`** - More readable
3. **Avoid `splice()` in loops** - Use `filter()` instead for new array
4. **Know your comparator in `sort()`** - Common mistakes with numbers
5. **Understand method chaining** - It creates temporary arrays, impacts performance
6. **For large operations, consider libraries like Lodash** - More optimized

---

## 11. **Real Interview Scenario**

**Question:** "Remove duplicates from an array"

**Approach 1 - Using Set:**
```javascript
const unique = [...new Set(arr)];
```

**Approach 2 - Using filter + indexOf:**
```javascript
const unique = arr.filter((el, i) => arr.indexOf(el) === i);
```

**Approach 3 - Using reduce:**
```javascript
const unique = arr.reduce((acc, el) => 
  acc.includes(el) ? acc : [...acc, el], []);
```

**Interview Tip:** Show you know multiple approaches, discuss tradeoffs (performance, readability, edge cases).