#### Smoothing Utilities (`smoothingUtils.js`)

- **rollingAverage**: Calculates the rolling average (simple moving average) of a data series.

```javascript {.line-numbers}
export const rollingAverage = (data, windowSize) => {
  const result = [];
  for (let i = 0; i <= data.length - windowSize; i++) {
    const window = data.slice(i, i + windowSize);
    const avg = window.reduce((sum, value) => sum + value, 0) / windowSize;
    result.push(avg);
  }
  return result;
};
```

- **exponentialMovingAverage**: Calculates the exponential moving average of a data series.

```javascript {.line-numbers}
export const exponentialMovingAverage = (data, smoothingFactor) => {
  const result = [];
  let previousEma = data[0];

  result.push(previousEma);

  for (let i = 1; i < data.length; i++) {
    const currentEma = (data[i] - previousEma) * smoothingFactor + previousEma;
    result.push(currentEma);
    previousEma = currentEma;
  }

  return result;
};
```

- **weightedMovingAverage**: Calculates the weighted moving average of a data series.

```javascript {.line-numbers}
export const weightedMovingAverage = (data, weights) => {
  const windowSize = weights.length;
  const result = [];

  for (let i = 0; i <= data.length - windowSize; i++) {
    const window = data.slice(i, i + windowSize);
    const weightedSum = window.reduce(
      (sum, value, index) => sum + value * weights[index],
      0
    );
    const weightSum = weights.reduce((sum, value) => sum + value, 0);
    result.push(weightedSum / weightSum);
  }

  return result;
};
```
