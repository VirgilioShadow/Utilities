#### File Handling Utilities (`fileUtils.js`)

- **readFile**: Reads a file and returns its contents.

```javascript {.line-numbers}
import fs from 'fs';

export const readFile = (filePath, encoding = 'utf-8') => {
  return fs.promises.readFile(filePath, encoding);
};
```

- **writeFile**: Writes data to a file.

```javascript {.line-numbers}
import fs from 'fs';

export const writeFile = (filePath, data, encoding = 'utf-8') => {
  return fs.promises.writeFile(filePath, data, encoding);
};
```
