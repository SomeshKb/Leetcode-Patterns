# 🚀 Cycle Sort Implementation and Explanation

## 🔄 Cycle Sort Algorithm

```javascript
function cycleSort(arr) {
    let i = 0;
    while (i < arr.length) {
        let correctIndex = arr[i]; // Find correct position for the element
        if (arr[i] !== arr[correctIndex]) {
            swap(arr, arr[i], arr[correctIndex]); // Swap
            console.log(arr);
        } else {
            i++; // Move to the next element
        }
    }
    return arr;
}

function swap(arr,i,j){
    let temp = arr[i];
    arr[i] = arr[j];
    arr[j] = temp;
}

```

## 📖 Explanation

Cycle Sort is an **in-place, non-comparison-based sorting algorithm**. It minimizes the number of swaps, making it **optimal when memory writes are costly**. The main idea is to place each element at its **correct position** in the array by cycling elements.

### 🛠️ Steps:
1️⃣ Start from the first element and determine its correct position.
2️⃣ If the element is not in its correct position, swap it with the correct index.
3️⃣ Repeat the process for all elements.
4️⃣ If an element is already in its correct position, move to the next index.

### 🔍 Code Walkthrough:
✅ The algorithm initializes an index variable `i`.
✅ The loop runs while `i` is less than the length of the array.
✅ It finds the `correctIndex` where the element should be placed.
✅ If the element is not at the correct index, it swaps it.
✅ The process continues until all elements are in their correct positions.

### ⏳ Time Complexity
- **⚡ Best Case:** O(n) (already sorted array)
- **🐢 Worst Case:** O(n²) (when every element is misplaced)
- **📦 Space Complexity:** O(1) (in-place sorting algorithm)

---

## 🔍 Identifying When to Use Cycle Sort

### 🔑 Key Characteristics of Cycle Sort Problems
- 🔢 **Array elements range from 1 to N or 0 to N-1**  
  - The problem often involves **placing elements in their correct index**.
- 🕵️ **Finding missing or duplicate numbers**  
  - Problems that require detecting **missing numbers, duplicates, or misplaced elements**.
- 💾 **In-place sorting without extra space**  
  - The problem restricts the use of extra space (O(1) space complexity).
- 🔄 **Numbers are supposed to be unique but may have violations**  
  - If a number appears twice or some numbers are missing.
- ❌ **The problem doesn’t require a stable sorting order**  
  - Cycle Sort is not a stable sort.

---

## 🔥 Common Problem Patterns & LeetCode Links

| 📝 **Pattern** | 🔗 **Example Problems** |
|------------------------------------|---------------------|
| ❓ **Find Missing Number(s)** | [Missing Number (LeetCode 268)](https://leetcode.com/problems/missing-number/) |
| 🔍 **Find Duplicates in an Array** | [Find the Duplicate Number (LeetCode 287)](https://leetcode.com/problems/find-the-duplicate-number/) |
| 🏆 **Find All Duplicates in an Array** | [Find All Duplicates (LeetCode 442)](https://leetcode.com/problems/find-all-duplicates-in-an-array/) |
| ⚠️ **Find All Missing Numbers** | [Find Disappeared Numbers (LeetCode 448)](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/) |
| 🔄 **Detect Mismatched Numbers** | [Set Mismatch (LeetCode 645)](https://leetcode.com/problems/set-mismatch/) |
| 📊 **Sorting Numbers in a Range 1 to N** | [First Missing Positive (LeetCode 41)](https://leetcode.com/problems/first-missing-positive/) |

---

## 🧐 How to Recognize If Cycle Sort Works?
Ask these **questions** to decide if **Cycle Sort** can be used:
✅ **Does the array contain numbers ranging from 1 to N (or 0 to N-1)?**  
✅ **Are elements meant to be in their correct positions (index-based placement)?**  
✅ **Does the problem involve finding missing/duplicate numbers?**  
✅ **Is the problem requiring an in-place solution with O(1) extra space?**  

If most of these conditions hold, **Cycle Sort is a likely candidate**. 🚀

