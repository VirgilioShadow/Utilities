#### Validation Utilities (`validationUtils.js`)

- **validateEmail**: Validates an email address format.

```javascript {.line-numbers}
export const validateEmail = (email) => {
  const re = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  return re.test(String(email).toLowerCase());
};
```

- **validateURL**: Validates a URL format.

```javascript {.line-numbers}
export const validateURL = (url) => {
  const re = /^(https?|chrome):\/\/[^\s$.?#].[^\s]*$/;
  return re.test(String(url).toLowerCase());
};
```
