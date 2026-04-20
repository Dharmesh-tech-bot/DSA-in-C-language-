# 📊 Sorting Algorithms (Interview Preparation)

This document contains step-by-step algorithms for commonly asked sorting techniques.

---
## 🔥 Pro Tip

While revising:
👉 Always imagine this array:
[5, 2, 9, 1, 5, 6]

If you can mentally sort this → you know the algorithm.

---


## 🔹 1. Bubble Sort

**Algorithm:**
1. Start from the first element.
2. Compare adjacent elements.
3. If the current element is greater than the next, swap them.
4. Move to the next pair and repeat.
5. After each pass, the largest element moves to the end.
6. Repeat the process for all elements (n-1 passes).

---

**Dry Run (Array):**

Pass 1:
[5, 2, 9, 1, 5, 6] → [2, 5, 9, 1, 5, 6]  
→ [2, 5, 1, 9, 5, 6]  
→ [2, 5, 1, 5, 9, 6]  
→ [2, 5, 1, 5, 6, 9]  

Largest element (9) moved to end.

**String:**
["banana", "apple", "cherry"] → ["apple", "banana", "cherry"]

---

## 🔹 2. Selection Sort

**Algorithm:**
1. Assume the first element is the minimum.
2. Compare it with all other elements.
3. Find the smallest element in the array.
4. Swap it with the first element.
5. Move to the next position and repeat.
6. Continue until the entire array is sorted.

---

**Dry Run (Array):**
Step 1: smallest = 1 → swap with first  
[1, 2, 9, 5, 5, 6]

Step 2: next smallest = 2 → already correct  

Step 3: smallest = 5 → swap  
[1, 2, 5, 9, 5, 6]

---


## 🔹 3. Insertion Sort

**Algorithm:**
1. Consider the first element as already sorted.
2. Pick the next element (key).
3. Compare it with elements in the sorted portion.
4. Shift elements greater than the key to the right.
5. Insert the key at the correct position.
6. Repeat for all elements.

---

**Dry Run (Array):**
Start:
[5 | 2, 9, 1, 5, 6]

Insert 2:
[2, 5 | 9, 1, 5, 6]

Insert 9:
[2, 5, 9 | 1, 5, 6]

Insert 1:
[1, 2, 5, 9 | 5, 6]

---



## 🔹 4. Merge Sort

**Algorithm:**
1. Divide the array into two halves.
2. Recursively divide each half until single elements remain.
3. Merge the subarrays:
   - Compare elements from both halves.
   - Place the smaller element into a new array.
4. Continue merging until the full array is sorted.

---

**Dry Run (Array):**
Split:
[5, 2, 9] and [1, 5, 6]

Further:
[5], [2], [9] → merge → [2, 5, 9]  
[1], [5], [6] → merge → [1, 5, 6]

Final Merge:
[1, 2, 5, 5, 6, 9]

---



## 🔹 5. Quick Sort

**Algorithm:**
1. Choose a pivot element.
2. Partition the array:
   - Elements smaller than pivot → left side.
   - Elements greater than pivot → right side.
3. Place pivot in its correct position.
4. Recursively apply Quick Sort on left and right subarrays.
5. Repeat until the array is sorted.

---

**Dry Run (Array):**
Pivot = 6

Left: [5, 2, 1, 5]  
Right: [9]

Sort left → [1, 2, 5, 5]

Final:
[1, 2, 5, 5, 6, 9]

---



## 🔹 6. Heap Sort

**Algorithm:**
1. Convert the array into a max heap.
2. Swap the root (largest element) with the last element.
3. Reduce heap size by one.
4. Heapify the root to maintain heap property.
5. Repeat until the array is sorted.

---

**Dry Run Idea:**
Convert to max heap:
[9, 5, 6, 1, 2, 5]

Swap root with last:
[5, 5, 6, 1, 2, 9]

Repeat → Final sorted:
[1, 2, 5, 5, 6, 9]

---



## 🔹 7. Counting Sort

**Algorithm:**
1. Find the maximum element in the array.
2. Create a count array of size (max + 1).
3. Count occurrences of each element.
4. Convert count array to prefix sum array.
5. Place elements into output array based on positions.
6. Copy output array back to original array.

---

**Dry Run (Array):**
Count:
1→1, 2→1, 5→2, 6→1, 9→1

Reconstruct:
[1, 2, 5, 5, 6, 9]

---



## 🔹 8. Radix Sort

**Algorithm:**
1. Find the maximum number to determine the number of digits.
2. For each digit (from least significant to most significant):
   - Sort the array using Counting Sort.
3. Repeat until all digits are processed.

---

**Dry Run Idea:**
Sort by digits (units → tens)

Example:
[170, 45, 75]

Units → [170, 45, 75]  
Tens → [45, 75, 170]

---


## 🔹 9. Bucket Sort

**Algorithm:**
1. Create multiple empty buckets.
2. Distribute elements into buckets based on their value range.
3. Sort each bucket individually.
4. Concatenate all buckets to get the final sorted array.

---

**Dry Run Idea:**
Distribute:
Bucket1 → [1, 2]  
Bucket2 → [5, 5]  
Bucket3 → [6, 9]

Merge → [1, 2, 5, 5, 6, 9]

---

## 🚀 Visualization Trick (Very Important)

- Bubble → "Push largest to end"
- Selection → "Pick smallest each time"
- Insertion → "Insert in sorted part"
- Merge → "Divide & merge"
- Quick → "Pivot splits array"
- Heap → "Tree → max element first"

---

## 🚀 Tip for Interviews

Focus on:
- Quick Sort
- Merge Sort
- Insertion Sort
- Heap Sort

Also understand:
- Time Complexity
- Space Complexity
- Stability of algorithms

---


# 📊 Complexity Table

| Algorithm      | Best      | Average   | Worst     | Space  | Stable |
|----------------|-----------|-----------|-----------|--------|--------|
| Bubble Sort    | O(n)      | O(n²)     | O(n²)     | O(1)   | Yes    |
| Selection Sort | O(n²)     | O(n²)     | O(n²)     | O(1)   | No     |
| Insertion Sort | O(n)      | O(n²)     | O(n²)     | O(1)   | Yes    |
| Merge Sort     | O(n log n)| O(n log n)| O(n log n)| O(n)   | Yes    |
| Quick Sort     | O(n log n)| O(n log n)| O(n²)     | O(log n)| No    |
| Heap Sort      | O(n log n)| O(n log n)| O(n log n)| O(1)   | No     |
| Counting Sort  | O(n+k)    | O(n+k)    | O(n+k)    | O(k)   | Yes    |

---
