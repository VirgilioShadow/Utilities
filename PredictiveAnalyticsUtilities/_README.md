#### Predictive Analytics Utilities (`predictiveAnalyticsUtils.js`)

- **simpleLinearRegression**: Calculates the simple linear regression line for a set of data points.

```javascript {.line-numbers}
export const simpleLinearRegression = (x, y) => {
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

export const predictLinear = (x, { slope, intercept }) => {
  return x * slope + intercept;
};
```

- **predictLinear**: Predicts a value based on a simple linear regression model.
- **sigmoid function**:

```javascript
const sigmoid = (z) => {
  return 1 / (1 + Math.exp(-z));
};
```

- **Logistic Regression**:

```javascript
const sigmoid = (z) => {
export const logisticRegression = (x, y, learningRate = 0.01, epochs = 1000) => {
  const n = x.length;
  let weights = Array(x[0].length).fill(0);
  let bias = 0;

  for (let i = 0; i < epochs; i++) {
    let modelOutput = [];
    for (let j = 0; j < n; j++) {
      const linearModel = x[j].reduce((sum, val, index) => sum + val * weights[index], 0) + bias;
      modelOutput.push(sigmoid(linearModel));
    }

    const gradientW = Array(weights.length).fill(0);
    let gradientB = 0;

    for (let j = 0; j < n; j++) {
      const error = modelOutput[j] - y[j];
      for (let k = 0; k < weights.length; k++) {
        gradientW[k] += error * x[j][k];
      }
      gradientB += error;
    }

    for (let k = 0; k < weights.length; k++) {
      weights[k] -= learningRate * (gradientW[k] / n);
    }
    bias -= learningRate * (gradientB / n);
  }

  return { weights, bias };
};

export const predictLogistic = (x, { weights, bias }) => {
  const linearModel = x.reduce((sum, val, index) => sum + val * weights[index], 0) + bias;
  return sigmoid(linearModel);
};

```

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

- **logisticRegression**: Performs logistic regression on a dataset.

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

**movingAverageForecast**: Uses a simple moving average for forecasting future values.

```javascript {.line-numbers}export const movingAverageForecast = (data, windowSize) => {
  const movingAverages = rollingAverage(data, windowSize);
  return movingAverages[movingAverages.length - 1];
};

```
