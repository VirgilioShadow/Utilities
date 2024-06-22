#### Statistical Utilities (`statisticalUtils.js`)

- **mean**: Calculates the mean (average) of an array of numbers.

```javascript {.line-numbers}
export const mean = (numbers) => {
  const total = numbers.reduce((acc, num) => acc + num, 0);
  return total / numbers.length;
};
```

- **median**: Calculates the median of an array of numbers.

```javascript {.line-numbers}
export const median = (numbers) => {
  const sorted = [...numbers].sort((a, b) => a - b);
  const middle = Math.floor(sorted.length / 2);

  if (sorted.length % 2 === 0) {
    return (sorted[middle - 1] + sorted[middle]) / 2;
  } else {
    return sorted[middle];
  }
};
```

- **mode**: Calculates the mode(s) of an array of numbers.

```javascript {.line-numbers}
export const mode = (numbers) => {
  const frequency = {};
  numbers.forEach((num) => {
    frequency[num] = (frequency[num] || 0) + 1;
  });

  let maxFrequency = 0;
  let modes = [];

  for (const num in frequency) {
    if (frequency[num] > maxFrequency) {
      modes = [Number(num)];
      maxFrequency = frequency[num];
    } else if (frequency[num] === maxFrequency) {
      modes.push(Number(num));
    }
  }

  return modes.length === numbers.length ? [] : modes;
};
```

- **variance**: Calculates the variance of an array of numbers.

```javascript {.line-numbers}
export const variance = (numbers) => {
  const avg = mean(numbers);
  const squareDiffs = numbers.map((num) => Math.pow(num - avg, 2));
  return mean(squareDiffs);
};
```

- **standardDeviation**: Calculates the standard deviation of an array of numbers.

```javascript {.line-numbers}
export const standardDeviation = (numbers) => {
  return Math.sqrt(variance(numbers));
};
```

#### Statistical Test Utilities (`statisticalTestsUtils.js`)

- **leastSquaresRegression**: Calculates the least squares regression line for a set of data points.

```javascript {.line-numbers}
export const leastSquaresRegression = (x, y) => {
  const n = x.length;
  const xMean = mean(x);
  const yMean = mean(y);

  let numerator = 0;
  let denominator = 0;

  for (let i = 0; i < n; i++) {
    numerator += (x[i] - xMean) * (y[i] - yMean);
    denominator += Math.pow(x[i] - xMean, 2);
  }

  const slope = numerator / denominator;
  const intercept = yMean - slope * xMean;

  return { slope, intercept };
};
```

- **zTest**: Performs a Z-test given a sample mean, population mean, population standard deviation, and sample size.

```javascript {.line-numbers}
export const zTest = (
  sampleMean,
  populationMean,
  populationStdDev,
  sampleSize
) => {
  const z =
    (sampleMean - populationMean) / (populationStdDev / Math.sqrt(sampleSize));
  return z;
};
```

- **tTestOneSample**: Performs a one-sample T-test given a sample and a population mean.

```javascript {.line-numbers}
export const tTestOneSample = (sample, populationMean) => {
  const sampleMean = mean(sample);
  const sampleStdDev = standardDeviation(sample);
  const sampleSize = sample.length;

  const t =
    (sampleMean - populationMean) / (sampleStdDev / Math.sqrt(sampleSize));
  return t;
};
```

- **chiSquareTest**: Performs a Chi-Square test given observed and expected frequencies.

```javascript {.line-numbers}
export const chiSquareTest = (observed, expected) => {
  let chiSquare = 0;
  for (let i = 0; i < observed.length; i++) {
    chiSquare += Math.pow(observed[i] - expected[i], 2) / expected[i];
  }
  return chiSquare;
};
```
