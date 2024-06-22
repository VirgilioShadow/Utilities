## Object Utilities (`objectUtils.js`)

- **deepClone**: Creates a deep clone of an object.

```javascript {.line-numbers}
export const deepClone = (obj) => {
  return JSON.parse(JSON.stringify(obj));
};
```

- **mergeObjects**: Merges two objects into one.

```javascript {.line-numbers}
export const mergeObjects = (target, source) => {
  return { ...target, ...source };
};
```
