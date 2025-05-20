## Problem 1:

**Description:**
Create a function that takes a `string` and an optional `boolean`.

- If the boolean is `true` or not provided, return the string in **uppercase**.
- If the boolean is `false`, return the string in **lowercase**.

**Solution:**

```ts
function formatString(input: string, toUpper?: boolean): string {
  if (toUpper === false) {
    return input.toLowerCase();
  } else {
    return input.toUpperCase();
  }
}

console.log(formatString("Hello")); // Output: "HELLO"
console.log(formatString("Hello", true)); // Output: "HELLO"
console.log(formatString("Hello", false)); // Output: "hello"
```
