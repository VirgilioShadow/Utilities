#### Date and Time Utilities (`dateUtils.js`)

- **timeSinceMidnight**: Calculates the number of seconds, milliseconds, or microseconds since midnight of the current day.

```javascript {.line-numbers}
export const timeSinceMidnight = (unit = 'milliseconds') => {
  const now = new Date();
  const midnight = new Date(now.setHours(0, 0, 0, 0));

  const timeElapsed = now - midnight;

  switch (unit) {
    case 'seconds':
      return Math.floor(timeElapsed / 1000);
    case 'milliseconds':
      return timeElapsed;
    case 'microseconds':
      return timeElapsed * 1000;
    default:
      throw new Error(
        'Invalid unit. Use "seconds", "milliseconds", or "microseconds".'
      );
  }
};
```

- **percentageOfDayElapsed**: Uses timeSinceMidnight() to the percentage of the day elapsed.

```javascript {.line-numbers}
export const percentageOfDayElapsed = () => {
  const millisecondsInADay = 24 * 60 * 60 * 1000;
  const timeElapsed = timeSinceMidnight('milliseconds');
  return (timeElapsed / millisecondsInADay) * 100;
};
```

- **getCurrentTimestamp**: Returns the current timestamp in ISO format.

```javascript {.line-numbers}
export const getCurrentTimestamp = () => new Date().toISOString();
```

- **formatDate**: Formats a date according to the given format options.

```javascript {.line-numbers}
export const formatDate = (date, format) => {
  const options = {
    year: 'numeric',
    month: '2-digit',
    day: '2-digit',
    ...format,
  };
  return new Date(date).toLocaleDateString(undefined, options);
};
```

- **daysBetweenDates**: Calculates the number of days between two dates.

```javascript {.line-numbers}
export const daysBetweenDates = (date1, date2) => {
  const diffTime = Math.abs(new Date(date2) - new Date(date1));
  return Math.ceil(diffTime / (1000 * 60 * 60 * 24));
};
```
