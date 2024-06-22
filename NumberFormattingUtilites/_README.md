#### Number Formatting Utilities (`numberFormattingUtils.js`)

- **formatNumberWithCommas**: Formats a number with commas as thousands separators.

```javascript {.line-numbers}
export const formatNumberWithCommas = (number) => {
  return number.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',');
};
```

- **formatToFixed**: Formats a number to a fixed number of decimal places.

```javascript {.line-numbers}
export const formatToFixed = (number, decimalPlaces) => {
  return number.toFixed(decimalPlaces);
};
```

- **numberToPercentage**: Converts a number to a percentage format.

```javascript
export const numberToPercentage = (number, decimalPlaces = 2) => {
  return (number * 100).toFixed(decimalPlaces) + '%';
};
```

- **formatCurrency**: Formats a number

```javascript {.line-numbers}
export const formatCurrency = (number, locale = 'en-US', currency = 'USD') => {
  return new Intl.NumberFormat(locale, { style: 'currency', currency }).format(
    number
  );
};
```
