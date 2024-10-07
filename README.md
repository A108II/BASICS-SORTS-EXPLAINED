# Basic Sorts Documentation

This document explains three fundamental sorting algorithms: **Bubble Sort**, **Selection Sort**, and **Insertion Sort**. Each algorithm has different approaches and use cases but aims to reorder an array in ascending order. Below is a detailed explanation of the code for each sorting method.

---

### Bubble Sort

```javascript
function bubbleSort(array) {
    for(let i = array.length - 1; i > 0; i--) {         // Outer loop: Iterate backwards from the end of the array.
        for(let j = 0; j < i; j++) {                    // Inner loop: Traverse the array up to the current unsorted portion.
            if(array[j] > array[j+1]) {                 // Compare adjacent elements and swap if they are in the wrong order.
                let temp = array[j];                    // Swap logic using a temporary variable.
                array[j] = array[j + 1];
                array[j + 1] = temp;
            }
        }
    }
    return array;                                       // Return the sorted array.
}
```

#### Explanation:
1. **Outer Loop** (`for(let i = array.length - 1; i > 0; i--)`):
   - This loop runs from the end of the array to the beginning.
   - With each iteration, the highest unsorted element "bubbles up" to its correct position at the end of the array. After each complete pass, the last element is guaranteed to be sorted, so the unsorted portion reduces.
   
2. **Inner Loop** (`for(let j = 0; j < i; j++)`):
   - It compares each adjacent element (`array[j]` and `array[j+1]`) in the array.
   - If the current element is greater than the next one, they are swapped to ensure smaller values move forward, and larger values move toward the end.

3. **Swapping Elements**:
   - A temporary variable (`temp`) is used to store `array[j]` before swapping the elements.
   - This ensures that values are correctly rearranged without losing any data during the swap.

4. **Return**:
   - Once the entire array is sorted, it is returned.

#### Time Complexity:
- **Worst-case**: O(n²) — When the array is in reverse order.
- **Best-case**: O(n) — When the array is already sorted.
  
---

### Selection Sort

```javascript
function selectionSort(array) {
    let min;                                            // Variable to store the index of the minimum value.
    for(let i = 0; i < array.length - 1; i++) {         // Outer loop: Move through the unsorted portion.
        min = i;                                        // Assume the first unsorted element is the minimum.
        for(let j = i + 1; j < array.length; j++) {     // Inner loop: Find the smallest element in the unsorted portion.
            if(array[j] < array[min]) min = j;          // Update the minimum index if a smaller value is found.
        }
        if(i !== min) {                                 // Swap the found minimum element with the first unsorted element.
            let temp = array[i];
            array[i] = array[min];
            array[min] = temp;
        }
    }
    return array;                                       // Return the sorted array.
}
```

#### Explanation:
1. **Outer Loop** (`for(let i = 0; i < array.length - 1; i++)`):
   - Iterates over the unsorted portion of the array.
   - At each iteration, it assumes the current element (`array[i]`) is the smallest in the unsorted portion.

2. **Inner Loop** (`for(let j = i + 1; j < array.length; j++)`):
   - Compares each subsequent element to find the smallest value in the unsorted portion.
   - If a smaller element is found, `min` is updated to the index of that element.

3. **Swapping**:
   - If the smallest element (`array[min]`) is not already at the position `i`, the current element (`array[i]`) is swapped with the minimum element.
   - This ensures that the smallest unsorted element is placed at the beginning of the unsorted portion.

4. **Return**:
   - Once the entire array is sorted, it is returned.

#### Time Complexity:
- **Worst-case**: O(n²) — Regardless of initial arrangement.
- **Best-case**: O(n²) — Even if the array is already sorted.

---

### Insertion Sort

```javascript
function insertionSort(array) {
    for(let i = 1; i < array.length; i++) {             // Outer loop: Iterate through each element, starting from the second.
        let temp = array[i];                            // Store the current element.
        for(var j = i - 1; array[j] > temp && j > -1; j--) {  // Inner loop: Shift elements greater than the current element to the right.
            array[j + 1] = array[j];                    // Shift larger elements one position to the right.
        }
        array[j+1] = temp;                              // Insert the current element in its correct position.
    }
    return array;                                       // Return the sorted array.
}
```

#### Explanation:
1. **Outer Loop** (`for(let i = 1; i < array.length; i++)`):
   - Starts from the second element in the array and considers it part of the unsorted portion.
   - This loop traverses each element, inserting them into their correct position in the sorted portion.

2. **Inner Loop** (`for(var j = i - 1; array[j] > temp && j > -1; j--)`):
   - It shifts elements of the sorted portion (`array[0...i-1]`) to the right, as long as they are greater than the current element (`temp`).
   - The inner loop continues to move elements to make space for the current element.

3. **Inserting Elements**:
   - Once the right position is found, the current element (`temp`) is inserted into the array at `array[j+1]`, ensuring the sorted portion remains correctly ordered.

4. **Return**:
   - Once the entire array is sorted, it is returned.

#### Time Complexity:
- **Worst-case**: O(n²) — When elements are in reverse order.
- **Best-case**: O(n) — When the array is already sorted, as no shifts are required.

