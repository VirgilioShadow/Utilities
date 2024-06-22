#### Sorting Algorithms (`sortingAlgorithms.js`)

- **bubbleSort**: Sorts an array using the bubble sort algorithm.

```javascript {.line-numbers}
export const bubbleSort = (array) => {
  let len = array.length;
  for (let i = 0; i < len; i++) {
    for (let j = 0; j < len - 1 - i; j++) {
      if (array[j] > array[j + 1]) {
        [array[j], array[j + 1]] = [array[j + 1], array[j]]; // Swap
      }
    }
  }
  return array;
};
```

- **mergeSort**: Sorts an array using the merge sort algorithm.

```javascript {.line-numbers}
export const mergeSort = (array) => {
  if (array.length <= 1) return array;

  const middle = Math.floor(array.length / 2);
  const left = array.slice(0, middle);
  const right = array.slice(middle);

  return merge(mergeSort(left), mergeSort(right));
};

const merge = (left, right) => {
  let result = [];
  let leftIndex = 0;
  let rightIndex = 0;

  while (leftIndex < left.length && rightIndex < right.length) {
    if (left[leftIndex] < right[rightIndex]) {
      result.push(left[leftIndex]);
      leftIndex++;
    } else {
      result.push(right[rightIndex]);
      rightIndex++;
    }
  }

  return result.concat(left.slice(leftIndex)).concat(right.slice(rightIndex));
};
```

- **quickSort**: Sorts an array using the quick sort algorithm.

```javascript {.line-numbers}
export const quickSort = (array) => {
  if (array.length <= 1) return array;

  const pivot = array[array.length - 1];
  const left = [];
  const right = [];

  for (const el of array.slice(0, array.length - 1)) {
    el < pivot ? left.push(el) : right.push(el);
  }

  return [...quickSort(left), pivot, ...quickSort(right)];
};
```

- **insertionSort**: Sorts an array using the insertion sort algorithm.

```javascript {.line-numbers}
export const insertionSort = (array) => {
  for (let i = 1; i < array.length; i++) {
    let key = array[i];
    let j = i - 1;
    while (j >= 0 && array[j] > key) {
      array[j + 1] = array[j];
      j--;
    }
    array[j + 1] = key;
  }
  return array;
};
```

- **selectionSort**: Sorts an array using the selection sort algorithm.

```javascript {.line-numbers}
export const selectionSort = (array) => {
  for (let i = 0; i < array.length; i++) {
    let minIndex = i;
    for (let j = i + 1; j < array.length; j++) {
      if (array[j] < array[minIndex]) {
        minIndex = j;
      }
    }
    if (minIndex !== i) {
      [array[i], array[minIndex]] = [array[minIndex], array[i]]; // Swap
    }
  }
  return array;
};
```

- **radixSort**: Sorts an array using the radix sort algorithm.

```javascript {.line-numbers}
export const radixSort = (array) => {
  const getMax = (arr) => {
    let max = arr[0];
    for (let i = 1; i < arr.length; i++) {
      if (arr[i] > max) max = arr[i];
    }
    return max;
  };

  const countingSort = (arr, exp) => {
    const output = new Array(arr.length).fill(0);
    const count = new Array(10).fill(0);

    for (let i = 0; i < arr.length; i++) {
      const index = Math.floor(arr[i] / exp) % 10;
      count[index]++;
    }

    for (let i = 1; i < 10; i++) {
      count[i] += count[i - 1];
    }

    for (let i = arr.length - 1; i >= 0; i--) {
      const index = Math.floor(arr[i] / exp) % 10;
      output[count[index] - 1] = arr[i];
      count[index]--;
    }

    for (let i = 0; i < arr.length; i++) {
      arr[i] = output[i];
    }
  };

  const max = getMax(array);

  for (let exp = 1; Math.floor(max / exp) > 0; exp *= 10) {
    countingSort(array, exp);
  }

  return array;
};
```

- **heapSort**: Sorts an array using the heap sort algorithm.

```javascript {.line-numbers}
export const heapSort = (array) => {
  let n = array.length;

  // Build a max heap
  for (let i = Math.floor(n / 2) - 1; i >= 0; i--) {
    heapify(array, n, i);
  }

  // Extract elements from heap one by one
  for (let i = n - 1; i >= 0; i--) {
    // Move current root to end
    [array[0], array[i]] = [array[i], array[0]];

    // Call max heapify on the reduced heap
    heapify(array, i, 0);
  }

  return array;
};

const heapify = (array, n, i) => {
  let largest = i;
  const left = 2 * i + 1;
  const right = 2 * i + 2;

  // If left child is larger than root
  if (left < n && array[left] > array[largest]) {
    largest = left;
  }

  // If right child is larger than largest so far
  if (right < n && array[right] > array[largest]) {
    largest = right;
  }

  // If largest is not root
  if (largest !== i) {
    [array[i], array[largest]] = [array[largest], array[i]];

    // Recursively heapify the affected sub-tree
    heapify(array, n, largest);
  }
};
```
