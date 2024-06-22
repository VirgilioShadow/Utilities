#### Error Handling Utilities (`errorUtils.js`)

- **tryCatch**: Wraps a function in a try-catch block to handle errors.

```javascript {.line-numbers}
export const tryCatch = (fn, onError) => {
  try {
    return fn();
  } catch (error) {
    if (onError) {
      onError(error);
    } else {
      console.error(error);
    }
  }
};
```
