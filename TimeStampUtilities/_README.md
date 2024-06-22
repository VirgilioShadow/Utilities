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

#### Timestamp Utilities (`timestampUtils.js`)

- **getCurrentTimestamp**: Returns the current timestamp in ISO format.

```javascript {.line-numbers}
export const getCurrentTimestamp = () => new Date().toISOString();
```

- **formatTimestamp**: Formats a timestamp according to the given format options.

```javascript {.line-numbers}
export const formatTimestamp = (timestamp, options) => {
  const date = new Date(timestamp);
  return date.toLocaleDateString(undefined, options);
};
```

- **convertTimestampToTimezone**: Converts a timestamp to a specified timezone.

```javascript {.line-numbers}
export const convertTimestampToTimezone = (timestamp, timeZone) => {
  const date = new Date(timestamp);
  return date.toLocaleString('en-US', { timeZone });
};
```

- **differenceBetweenTimestamps**: Calculates the difference between two timestamps in specified units.

```javascript {.line-numbers}
export const differenceBetweenTimestamps = (
  timestamp1,
  timestamp2,
  unit = 'milliseconds'
) => {
  const diff = Math.abs(new Date(timestamp1) - new Date(timestamp2));
  switch (unit) {
    case 'seconds':
      return Math.floor(diff / 1000);
    case 'minutes':
      return Math.floor(diff / (1000 * 60));
    case 'hours':
      return Math.floor(diff / (1000 * 60 * 60));
    case 'days':
      return Math.floor(diff / (1000 * 60 * 60 * 24));
    default:
      return diff;
  }
};
```

- **addToTimestamp**: Adds a specified amount of time to a timestamp.

```javascript {.line-numbers}
export const addToTimestamp = (timestamp, value, unit) => {
  const date = new Date(timestamp);
  switch (unit) {
    case 'seconds':
      date.setSeconds(date.getSeconds() + value);
      break;
    case 'minutes':
      date.setMinutes(date.getMinutes() + value);
      break;
    case 'hours':
      date.setHours(date.getHours() + value);
      break;
    case 'days':
      date.setDate(date.getDate() + value);
      break;
    default:
      throw new Error(
        'Invalid unit. Use "seconds", "minutes", "hours", or ..."days".'
      );
  }
  return date.toISOString();
};
```

- **timestampToReadableDate**: Converts a timestamp to a readable date format.

```javascript {.line-numbers}
export const timestampToReadableDate = (
  timestamp,
  locale = 'en-US',
  options = {}
) => {
  const date = new Date(timestamp);
  return date.toLocaleDateString(locale, options);
};
```

- **readableDateToTimestamp**: Converts a readable date string to a timestamp.

```javascript {.line-numbers}
export const readableDateToTimestamp = (dateString) => {
  return new Date(dateString).toISOString();
};
```

- **toUnixTimestampSeconds**: Converts a timestamp to Unix timestamp in seconds.

```javascript {.line-numbers}
export const toUnixTimestampSeconds = (timestamp) => {
  return Math.floor(new Date(timestamp).getTime() / 1000);
};
```

- **toUnixTimestampMilliseconds**: Converts a timestamp to Unix timestamp in milliseconds.

```javascript {.line-numbers}
export const toUnixTimestampMilliseconds = (timestamp) => {
  return new Date(timestamp).getTime();
};
```

- **fromUnixTimestampSecondsToISO**: Converts a Unix timestamp in seconds to an ISO string.

```javascript {.line-numbers}
export const fromUnixTimestampSecondsToISO = (unixTimestamp) => {
  return new Date(unixTimestamp * 1000).toISOString();
};
```

- **fromUnixTimestampMillisecondsToISO**: Converts a Unix timestamp in milliseconds to an ISO string.

```javascript {.line-numbers}
export const fromUnixTimestampMillisecondsToISO = (unixTimestamp) => {
  return new Date(unixTimestamp).toISOString();
};
```

- **toHumanReadableDate**: Converts a timestamp to a human-readable date format.

```javascript {.line-numbers}
export const toHumanReadableDate = (
  timestamp,
  locale = 'en-US',
  options = {}
) => {
  const date = new Date(timestamp);
  return date.toLocaleDateString(locale, options);
};
```

- **toHumanReadableTime**: Converts a timestamp to a human-readable time format.

```javascript {.line-numbers}
export const toHumanReadableTime = (
  timestamp,
  locale = 'en-US',
  options = {}
) => {
  const date = new Date(timestamp);
  return date.toLocaleTimeString(locale, options);
};
```

- **toHumanReadableDateTime**: Converts a timestamp to a human-readable date and time format.

```javascript {.line-numbers}
export const toHumanReadableDateTime = (
  timestamp,
  locale = 'en-US',
  options = {}
) => {
  const date = new Date(timestamp);
  return date.toLocaleString(locale, options);
};
```

- **localToUTC**: Converts a local timestamp to UTC.

```javascript {.line-numbers}
export const localToUTC = (localTimestamp) => {
  const date = new Date(localTimestamp);
  return date.toISOString();
};
```

- **utcToLocal**: Converts a UTC timestamp to local time.

```javascript {.line-numbers}
export const utcToLocal = (utcTimestamp) => {
  const date = new Date(utcTimestamp);
  return date.toLocaleString();
};
```

- **utcToTimezone**: Converts a UTC timestamp to a specified timezone.

```javascript {.line-numbers}
export const utcToTimezone = (utcTimestamp, timeZone) => {
  const date = new Date(utcTimestamp);
  return date.toLocaleString('en-US', { timeZone });
};
```

- **isLeapYear**: JavaScript's Date object also handles DST transitions. When you create a Date object or manipulate dates, it considers the local timezone's DST rules. However, converting between timezones can be complex because of DST differences between regions.

```javascript {.line-numbers}
const isLeapYear = (year) => {
  return (year % 4 === 0 && year % 100 !== 0) || year % 400 === 0;
};

// Usage
console.log(isLeapYear(2020)); // true
console.log(isLeapYear(2021)); // false
```

- **getDSTTransitionDates**:

```javascript {.line-numbers}
const getDSTTransitionDates = (year) => {
  const dates = [];
  for (let month = 0; month < 12; month++) {
    for (let day = 1; day <= 31; day++) {
      const date = new Date(year, month, day);
      if (date.getMonth() !== month) break; // skip invalid dates

      const offset = date.getTimezoneOffset();
      if (dates.length && offset !== dates[dates.length - 1].offset) {
        dates.push({ date, offset });
      } else if (!dates.length) {
        dates.push({ date, offset });
      }
    }
  }
  return dates;
};

// Usage
console.log(getDSTTransitionDates(2024));
```
