#### Logging Utilities (`loggingUtils.js`)

- **log**: Logs a message to the console and to a file.

```javascript {.line-numbers}
export const logger = {
  log: (message) => console.log(`[LOG]: ${message}`),
  warn: (message) => console.warn(`[WARN]: ${message}`),
  error: (message) => console.error(`[ERROR]: ${message}`),
  info: (message) => console.info(`[INFO]: ${message}`),
};
```

- **warn**: Logs a warning message to the console and to a file.

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

- **File Logging Utility**: Logs an error message to the console and to a file. This utility will be useful for maintaining logs for debugging and monitoring purposes in a Node.js environment.

```javascript {.line-numbers}
import fs from 'fs';
import path from 'path';

// Ensure the log directory exists
const logDirectory = path.resolve(__dirname, '../logs');
if (!fs.existsSync(logDirectory)) {
  fs.mkdirSync(logDirectory, { recursive: true });
}

// Log file path
const logFilePath = path.join(logDirectory, 'application.log');

// Helper function to write logs to file
const writeToFile = (message) => {
  fs.appendFile(logFilePath, `${message}\n`, (err) => {
    if (err) {
      console.error('Failed to write to log file:', err);
    }
  });
};

export const logger = {
  log: (message) => {
    const formattedMessage = `[LOG]: ${message}`;
    console.log(formattedMessage);
    writeToFile(formattedMessage);
  },
  warn: (message) => {
    const formattedMessage = `[WARN]: ${message}`;
    console.warn(formattedMessage);
    writeToFile(formattedMessage);
  },
  error: (message) => {
    const formattedMessage = `[ERROR]: ${message}`;
    console.error(formattedMessage);
    writeToFile(formattedMessage);
  },
  info: (message) => {
    const formattedMessage = `[INFO]: ${message}`;
    console.info(formattedMessage);
    writeToFile(formattedMessage);
  },
};
```

- **info**: Logs an informational message to the console and to a file.

```javascript {.line-numbers}
export const logElapsedTime = (startTime, label = '') => {
  const elapsedMilliseconds = endTimer(startTime);
  console.log(`${label} - Elapsed time: ${elapsedMilliseconds.toFixed(3)} ms`);
};
```

- **TryiCatchWrapper**:

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
