#### Environment Utilities (`envUtils.js`)

- **getEnvVariable**: Retrieves the value of an environment variable.

```javascript {.line-numbers}
export const getEnvVariable = (key) => {
  return process.env[key];
};
```
