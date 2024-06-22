#### String Utilities (`StringUtilities.js`)

- **capitalizeFirstLetter**: Capitalizes the first letter of a string.

```javascript {.line-numbers}
export const capitalizeFirstLetter = (string) =>
  string.charAt(0).toUpperCase() + string.slice(1);
```

- **generateRandomString**: Generates a random string of specified length.

```javascript {.line-numbers}
export const generateRandomString = (length) => {
  const characters =
    'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789';
  let result = '';
  for (let i = 0; i < length; i++) {
    result += characters.charAt(Math.floor(Math.random() * characters.length));
  }
  return result;
};
```
