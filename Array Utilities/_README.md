#### Array Utilities (`arrayUtils.js`)

- **removeDuplicates**: Removes duplicate elements from an array.

```javascript {.line-numbers}
export const removeDuplicates = (array) => [...new Set(array)];
```

- **shuffleArray**: Shuffles the elements of an array randomly.

```javascript {.line-numbers}
export const shuffleArray = (array) => {
  let currentIndex = array.length,
    temporaryValue,
    randomIndex;

  while (0 !== currentIndex) {
    randomIndex = Math.floor(Math.random() * currentIndex);
    currentIndex -= 1;

    temporaryValue = array[currentIndex];
    array[currentIndex] = array[randomIndex];
    array[randomIndex] = temporaryValue;
  }

  return array;
};
```
