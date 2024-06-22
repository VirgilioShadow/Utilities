#### Number Utilities (`numberUtils.js`)

- **formatNumberWithCommas**: Formats a number with commas as thousands separators.

```javascript {.line-numbers}
export const formatNumberWithCommas = (number) => {
  return number.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',');
};
```

- **generateRandomNumber**: Generates a random number between specified min and max values.

```javascript {.line-numbers}
export const generateRandomNumber = (min, max) => {
  return Math.floor(Math.random() * (max - min + 1)) + min;
};
```
