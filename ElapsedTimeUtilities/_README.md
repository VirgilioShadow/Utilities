#### Elapsed Time Utilities (`elapsedTimeUtils.js`)

- **startTimer**: Starts a high-resolution timer.

```javascript {.line-numbers}
export const startTimer = () => {
  return process.hrtime();
};
```

- **endTimer**: Ends the timer and calculates the elapsed time in milliseconds.

```javascript {.line-numbers}
export const endTimer = (startTime) => {
  const endTime = process.hrtime(startTime);
  const elapsedSeconds = endTime[0];
  const elapsedNanoseconds = endTime[1];
  const elapsedMilliseconds = elapsedSeconds * 1000 + elapsedNanoseconds / 1e6;
  return elapsedMilliseconds;
};
```

- **logElapsedTime**: Logs the elapsed time with an optional label.

```javascript {.line-numbers}
export const logElapsedTime = (startTime, label = '') => {
  const elapsedMilliseconds = endTimer(startTime);
  console.log(`${label} - Elapsed time: ${elapsedMilliseconds.toFixed(3)} ms`);
};
```
