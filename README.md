# Utility Functions

This folder contains a collection of reusable utility functions. Below is a list of the contents of each file.

#### Date and Time Utilities (`dateUtils.js`)

- **getCurrentTimestamp**: Returns the current timestamp in ISO format.
- **formatDate**: Formats a date according to the given format options.
- **daysBetweenDates**: Calculates the number of days between two dates.

#### String Utilities (`stringUtils.js`)

- **capitalizeFirstLetter**: Capitalizes the first letter of a string.
- **generateRandomString**: Generates a random string of specified length.

## Array Utilities (`arrayUtils.js`)

- **removeDuplicates**: Removes duplicate elements from an array.
- **shuffleArray**: Shuffles the elements of an array randomly.

## Object Utilities (`objectUtils.js`)

- **deepClone**: Creates a deep clone of an object.
- **mergeObjects**: Merges two objects into one.

#### Number Utilities (`numberUtils.js`)

- **formatNumberWithCommas**: Formats a number with commas as thousands separators.
- **generateRandomNumber**: Generates a random number between specified min and max values.

#### Validation Utilities (`validationUtils.js`)

- **validateEmail**: Validates an email address format.
- **validateURL**: Validates a URL format.

#### HTTP Utilities (`httpUtils.js`)

- **fetchWithTimeout**: Fetches data from a URL with a specified timeout.

#### Environment Utilities (`envUtils.js`)

- **getEnvVariable**: Retrieves the value of an environment variable.

#### Sorting Algorithms (`sortingAlgorithms.js`)

- **bubbleSort**: Sorts an array using the bubble sort algorithm.
- **mergeSort**: Sorts an array using the merge sort algorithm.
- **quickSort**: Sorts an array using the quick sort algorithm.
- **insertionSort**: Sorts an array using the insertion sort algorithm.
- **selectionSort**: Sorts an array using the selection sort algorithm.
- **radixSort**: Sorts an array using the radix sort algorithm.
- **heapSort**: Sorts an array using the heap sort algorithm.

#### Timestamp Utilities (`timestampUtils.js`)

- **getCurrentTimestamp**: Returns the current timestamp in ISO format.
- **formatTimestamp**: Formats a timestamp according to the given format options.
- **convertTimestampToTimezone**: Converts a timestamp to a specified timezone.
- **differenceBetweenTimestamps**: Calculates the difference between two timestamps in specified units.
- **addToTimestamp**: Adds a specified amount of time to a timestamp.
- **timestampToReadableDate**: Converts a timestamp to a readable date format.
- **readableDateToTimestamp**: Converts a readable date string to a timestamp.
- **toUnixTimestampSeconds**: Converts a timestamp to Unix timestamp in seconds.
- **toUnixTimestampMilliseconds**: Converts a timestamp to Unix timestamp in milliseconds.
- **fromUnixTimestampSecondsToISO**: Converts a Unix timestamp in seconds to an ISO string.
- **fromUnixTimestampMillisecondsToISO**: Converts a Unix timestamp in milliseconds to an ISO string.
- **toHumanReadableDate**: Converts a timestamp to a human-readable date format.
- **toHumanReadableTime**: Converts a timestamp to a human-readable time format.
- **toHumanReadableDateTime**: Converts a timestamp to a human-readable date and time format.
- **localToUTC**: Converts a local timestamp to UTC.
- **utcToLocal**: Converts a UTC timestamp to local time.
- **utcToTimezone**: Converts a UTC timestamp to a specified timezone.

#### Elapsed Time Utilities (`elapsedTimeUtils.js`)

- **startTimer**: Starts a high-resolution timer.
- **endTimer**: Ends the timer and calculates the elapsed time in milliseconds.
- **logElapsedTime**: Logs the elapsed time with an optional label.

#### Data Manipulation Utilities (`dataUtils.js`)

- **debounce**: Creates a debounced function that delays invoking the provided function.
- **throttle**: Creates a throttled function that only invokes the provided function at most once per every specified milliseconds.
- **deepMerge**: Deeply merges two objects.

#### Logging Utilities (`loggingUtils.js`)

- **log**: Logs a message to the console and to a file.
- **warn**: Logs a warning message to the console and to a file.
- **error**: Logs an error message to the console and to a file.
- **info**: Logs an informational message to the console and to a file.

#### Error Handling Utilities (`errorUtils.js`)

- **tryCatch**: Wraps a function in a try-catch block to handle errors.

#### File Handling Utilities (`fileUtils.js`)

- **readFile**: Reads a file and returns its contents.
- **writeFile**: Writes data to a file.

#### Statistical Utilities (`statisticalUtils.js`)

- **mean**: Calculates the mean (average) of an array of numbers.
- **median**: Calculates the median of an array of numbers.
- **mode**: Calculates the mode(s) of an array of numbers.
- **variance**: Calculates the variance of an array of numbers.
- **standardDeviation**: Calculates the standard deviation of an array of numbers.

#### Statistical Test Utilities (`statisticalTestsUtils.js`)

- **leastSquaresRegression**: Calculates the least squares regression line for a set of data points.
- **zTest**: Performs a Z-test given a sample mean, population mean, population standard deviation, and sample size.
- **tTestOneSample**: Performs a one-sample T-test given a sample and a population mean.
- **chiSquareTest**: Performs a Chi-Square test given observed and expected frequencies.

#### Smoothing Utilities (`smoothingUtils.js`)

- **rollingAverage**: Calculates the rolling average (simple moving average) of a data series.
- **exponentialMovingAverage**: Calculates the exponential moving average of a data series.
- **weightedMovingAverage**: Calculates the weighted moving average of a data series.

#### Financial Utilities (`financialUtils.js`)

- **percentageChange**: Calculates the percentage change between two values.
- **compoundAnnualGrowthRate**: Calculates the compound annual growth rate (CAGR) between two values over a number of periods.
- **simpleInterest**: Calculates the simple interest given principal, rate, and time.
- **compoundInterest**: Calculates the compound interest given principal, rate, times compounded per period, and time.
- **futureValue**: Calculates the future value of an investment given principal, rate, times compounded per period, and time.

#### Predictive Analytics Utilities (`predictiveAnalyticsUtils.js`)

- **simpleLinearRegression**: Calculates the simple linear regression line for a set of data points.
- **predictLinear**: Predicts a value based on a simple linear regression model.
- **logisticRegression**: Performs logistic regression on a dataset.
- **predictLogistic**: Predicts a value based on a logistic regression model.
- **movingAverageForecast**: Uses a simple moving average for forecasting future values.

#### Number Formatting Utilities (`numberFormattingUtils.js`)

- **formatNumberWithCommas**: Formats a number with commas as thousands separators.
- **formatToFixed**: Formats a number to a fixed number of decimal places.
- **numberToPercentage**: Converts a number to a percentage format.
- **formatCurrency**: Formats a number
