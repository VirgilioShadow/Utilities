#### Financial Utilities (`financialUtils.js`)

- **percentageChange**: Calculates the percentage change between two values.

```javascript {.line-numbers}
export const percentageChange = (initialValue, finalValue) => {
  return ((finalValue - initialValue) / initialValue) * 100;
};
```

- **compoundAnnualGrowthRate**: Calculates the compound annual growth rate (CAGR) between two values over a number of periods.

```javascript {.line-numbers}
export const compoundAnnualGrowthRate = (initialValue, finalValue, periods) => {
  return ((finalValue / initialValue) ** (1 / periods) - 1) * 100;
};
```

- **simpleInterest**: Calculates the simple interest given principal, rate, and time.

```javascript {.line-numbers}
export const simpleInterest = (principal, rate, time) => {
  return (principal * rate * time) / 100;
};
```

- **compoundInterest**: Calculates the compound interest given principal, rate, times compounded per period, and time.

```javascript {.line-numbers}
export const compoundInterest = (principal, rate, timesCompounded, time) => {
  return (
    principal * (1 + rate / timesCompounded) ** (timesCompounded * time) -
    principal
  );
};
```

- **futureValue**: Calculates the future value of an investment given principal, rate, times compounded per period, and time.

```javascript {.line-numbers}
export const futureValue = (principal, rate, timesCompounded, time) => {
  return principal * (1 + rate / timesCompounded) ** (timesCompounded * time);
};
```
