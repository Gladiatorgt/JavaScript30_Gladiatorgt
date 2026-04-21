# Destructuring Concept(temp arrays)

```javascript
    const alpha = people.sort((lastOne, nextOne) => {
        const [aLast, aFirst] = lastOne.split(", ");
        const [bLast, bFirst] = nextOne.split(", ");
        return aLast > bLast ? 1 : -1;
      });
````

This snippet uses **Destructuring Assignment** and the `.split()` method to organize data for sorting.

Here is the breakdown of those specific lines:

### 1. `lastOne.split(", ")`
The `people` array contains strings in the format `"LastName, FirstName"` (e.g., `"Beck, Glenn"`).
- `.split(", ")` looks for the comma and space.
- It turns the string into a temporary array: `["Beck", "Glenn"]`.

### 2. `const [aLast, aFirst] = ...` (Destructuring)
Instead of creating an array and then accessing `arr[0]` and `arr[1]`, JavaScript allows you to "unpack" the array values into variables immediately.

```javascript
// How it works under the hood:
const [aLast, aFirst] = ["Beck", "Glenn"];

// Is the same as:
// const temp = ["Beck", "Glenn"];
// const aLast = temp[0];
// const aFirst = temp[1];
````

### Why do this inside `.sort()`?

The goal of this code is to sort the `people` array **alphabetically by last name**.

1. **Split**: It breaks the "LastName, FirstName" strings into separate variables.
2. **Compare**: It compares `aLast` (the first person's last name) against `bLast` (the next person's last name).
3. **Return**: If `aLast` is alphabetically "greater" than `bLast`, it returns `1` (moves it up); otherwise, it returns `-1`.

### Summary of the variables:

| Variable  | Value                                   |
| :-------- | :-------------------------------------- |
| `lastOne` | The full string (e.g., `"Beck, Glenn"`) |
| `aLast`   | The extracted last name (`"Beck"`)      |
| `aFirst`  | The extracted first name (`"Glenn"`)    |
