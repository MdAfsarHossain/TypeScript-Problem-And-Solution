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

## Problem 2:

**Description:**
Create a function that filters an array of objects by the `rating` property, returning only items with a rating of **4 or more**.

**Solution:**

```ts
function filterByRating(
  items: { title: string; rating: number }[]
): { title: string; rating: number }[] {
  const newArray = items?.filter((item) => item.rating >= 4.0);
  return newArray;
}

const books = [
  { title: "Book A", rating: 4.5 },
  { title: "Book B", rating: 3.2 },
  { title: "Book C", rating: 5.0 },
];

console.log(filterByRating(books));
// Output: [ { title: "Book A", rating: 4.5 }, { title: "Book C", rating: 5.0 } ]
```

---

## Problem 3:

**Description:**
Create a generic function that concatenates multiple arrays of the **same type** using rest parameters.

**Solution:**

```ts
function concatenateArrays<T>(...arrays: T[][]): T[] {
  let newArray: T[] = [];

  for (const i of arrays) {
    newArray.push(...i);
  }

  return newArray;
}

console.log(concatenateArrays(["a", "b"], ["c"])); // Output: ["a", "b", "c"]
console.log(concatenateArrays([1, 2], [3, 4], [5])); // Output: [1, 2, 3, 4, 5]
```

---

## Problem 4:

**Description:**

- Create a `Vehicle` class with private `make` and `year` properties and a `getInfo()` method.
- Create a `Car` class extending `Vehicle`, adding a private `model` property and a `getModel()` method.

**Solution:**

```ts
class Vehicle {
  private make: string;
  private year: number;

  constructor(make: string, year: number) {
    this.make = make;
    this.year = year;
  }

  getInfo() {
    return `Make: ${this.make}, Year: ${this.year}`;
  }
}

class Car extends Vehicle {
  private model: string;

  constructor(make: string, year: number, model: string) {
    super(make, year);
    this.model = model;
  }

  getModel() {
    return `Model: ${this.model}`;
  }
}

const myCar = new Car("Toyota", 2020, "Corolla");
// myCar.getInfo(); // Output: "Make: Toyota, Year: 2020"
// myCar.getModel(); // Output: "Model: Corolla"

console.log(myCar.getInfo());
console.log(myCar.getModel());
```

---

## Problem 5:

**Description:**
Write a function that takes a `string | number` and returns:

- The **length** if it's a string
- The **number multiplied by 2** if it's a number

**Solution:**

```ts
function processValue(value: string | number): number {
  if (typeof value === "string") {
    return value.length;
  } else {
    return value * 2;
  }
}

console.log(processValue("hello")); // Output: 5
console.log(processValue(10)); // Output: 20
```

---

## Problem 6:

**Description:**
Define an interface `Product` and create a function to find the product with the **highest price** in an array. If the array is empty, return `null`.

**Solution:**

```ts
interface Product {
  name: string;
  price: number;
}

function getMostExpensiveProduct(products: Product[]): Product | null {
  if (products.length === 0) {
    return null;
  }

  let mostExpensiveProduct = products[0];
  for (const product of products) {
    if (product.price > mostExpensiveProduct.price) {
      mostExpensiveProduct = product;
    }
  }
  return mostExpensiveProduct;
}

const products = [
  { name: "Pen", price: 10 },
  { name: "Notebook", price: 25 },
  { name: "Bag", price: 50 },
];

//   getMostExpensiveProduct(products);
console.log(getMostExpensiveProduct(products));
console.log(getMostExpensiveProduct([]));
// Output: { name: "Bag", price: 50 }
```

---

## Problem 7:

**Description:**

- Define an `enum Day` for the days of the week.
- Create a function that returns `"Weekday"` or `"Weekend"` based on the input day.

**Solution:**

```ts
enum Day {
  Monday,
  Tuesday,
  Wednesday,
  Thursday,
  Friday,
  Saturday,
  Sunday,
}

function getDayType(day: Day): string {
  switch (day) {
    case Day.Saturday:
    case Day.Sunday:
      return "Weekend";
    default:
      return "Weekday";
  }
}

//   getDayType(Day.Monday); // Output: "Weekday"
//   getDayType(Day.Sunday); // Output: "Weekend"
console.log(getDayType(Day.Monday)); // Output: "Weekday"
console.log(getDayType(Day.Sunday)); // Output: "Weekend"
console.log(getDayType(Day.Monday)); // Output: "Weekday"
console.log(getDayType(Day.Tuesday)); // Output: "Weekday"
console.log(getDayType(Day.Saturday)); // Output: "Weekend"
console.log(getDayType(Day.Sunday)); // Output: "Weekend"
```

---

## Problem 8:

**Description:**
Create an async function that:

- Returns the square of a number after 1 second
- Rejects if the number is negative

**Solution:**

```ts
async function squareAsync(n: number): Promise<number> {
  return new Promise((resolve, reject) => {
    if (n < 0) {
      reject("Error: Negative number not allowed");
    } else {
      setTimeout(() => {
        resolve(n * n);
      }, 1000);
    }
  });
}
squareAsync(4).then(console.log); // Output after 1s: 16
squareAsync(-3).catch(console.error); // Output: Error: Negative number not allowed
```

---

## Problem: 9

**Description:**
Create a function that takes an array of objects with name (string) and age (number) properties and returns a new array containing only the names of the people who are 18 or older.

**Solution:**

```ts
function getAdultNames(people: { name: string; age: number }[]): string[] {
  const adults = people.filter((person) => person.age >= 18);
  return adults.map((adult) => adult.name);
}

const people = [
  { name: "Alice", age: 17 },
  { name: "Bob", age: 20 },
  { name: "Charlie", age: 18 },
  { name: "David", age: 16 },
];

console.log(getAdultNames(people)); // Output: ["Bob", "Charlie"]
```

---

## Problem: 10

**Description:**
Create a function that takes an array of numbers and returns a new array where each number is doubled, but only if the original number is even.

**Solution:**

```ts
function doubleEvens(numbers: number[]): number[] {
return numbers.map(number => {
if (number % 2 === 0) {
return number \* 2;
} else {
return number;
}
});
}

const numbers = [1, 2, 3, 4, 5, 6];
console.log(doubleEvens(numbers)); // Output: [1, 4, 3, 8, 5, 12]
```

---

## Problem: 11

**Description:** Create a function that takes an array of strings and returns a new array containing the length of each string in the original array.

**Solution:**

```ts
function stringLengths(strings: string[]): number[] {
  return strings.map((str) => str.length);
}

const words = ["apple", "banana", "kiwi"];
console.log(stringLengths(words)); // Output: [5, 6, 4]
```

---

---

## Problem: 12

**Description:** Create a function that takes an array of numbers and returns the sum of all the numbers in the array.

**Solution:**

```ts
function sumArray(numbers: number[]): number {
  return numbers.reduce((sum, number) => sum + number, 0);
}

const numbers = [1, 2, 3, 4, 5];
console.log(sumArray(numbers)); // Output: 15
```

---

## Problem: 13

**Description:** Create a function that takes an array of objects with name (string) and city (string) properties, and returns a new object where the keys are the cities and the values are arrays of names of people living in that city.

**Solution:**

```ts
function groupPeopleByCity(people: { name: string; city: string }[]): {
  [city: string]: string[];
} {
  const cityMap: { [city: string]: string[] } = {};

  for (const person of people) {
    if (cityMap[person.city]) {
      cityMap[person.city].push(person.name);
    } else {
      cityMap[person.city] = [person.name];
    }
  }

  return cityMap;
}

const people = [
  { name: "Alice", city: "New York" },
  { name: "Bob", city: "New York" },
  { name: "Charlie", city: "London" },
  { name: "David", city: "Paris" },
  { name: "Eve", city: "London" },
];

console.log(groupPeopleByCity(people));
// Output: { "New York": ["Alice", "Bob"], "London": ["Charlie", "Eve"], "Paris": ["David"] }
```

---

## Problem: 14

**Description:** Create a function that takes two arrays of numbers and returns a new array containing only the numbers that are present in both arrays.

**Solution:**

```ts
function findCommonElements(arr1: number[], arr2: number[]): number[] {
  return arr1.filter((number) => arr2.includes(number));
}

const array1 = [1, 2, 3, 4, 5];
const array2 = [3, 5, 6, 7, 8];
console.log(findCommonElements(array1, array2)); // Output: [3, 5]
```

---

## Problem: 15

**Description:** Create a function that takes a string and returns the string with all vowels removed.

**Solution:**

```ts
function removeVowels(str: string): string {
  return str.replace(/[aeiouAEIOU]/g, "");
}

const myString = "Hello World";
console.log(removeVowels(myString)); // Output: Hll Wrld
```

---

## Problem 16:

**Description:**
Create a function that takes an array of numbers and returns the average of those numbers. If the array is empty, return 0.

**Solution:**

```typescript
function average(numbers: number[]): number {
  if (numbers.length === 0) {
    return 0;
  }
  const sum = numbers.reduce((acc, num) => acc + num, 0);
  return sum / numbers.length;
}

const numbers = [1, 2, 3, 4, 5];
console.log(average(numbers)); // Output: 3
console.log(average([])); // Output: 0
```

---

## Problem 17:

**Description:** Create a function that takes a string and returns the reversed version of that string.

**Solution:**

```ts
function reverseString(str: string): string {
  return str.split("").reverse().join("");
}

const myString = "hello";
console.log(reverseString(myString)); // Output: "olleh"
```

---

## Problem 18:

**Description:** Create a function that takes an array of strings and returns a new array with only the strings that have a length greater than or equal to 5.

**Solution:**

```ts
function filterLongStrings(strings: string[]): string[] {
  return strings.filter((str) => str.length >= 5);
}

const words = ["apple", "banana", "kiwi", "grape"];
console.log(filterLongStrings(words)); // Output: ["apple", "banana", "grape"]
```
