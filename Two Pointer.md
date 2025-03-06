## **🚀 Two Pointer Technique **

The **Two Pointer** technique is a powerful optimization method used to solve array and string problems efficiently. Instead of using nested loops (O(N²)), we use two pointers to iterate through the data in a more optimal way, reducing time complexity to **O(N)** in many cases.

---

## **🔹 When to Use Two Pointers?**
You should consider using **Two Pointers** when:
1. **The problem involves a sorted array** (common in binary search-like problems).
2. **You're searching for a pair of elements that satisfy a condition** (e.g., sum of two numbers, difference of two elements, merging arrays).
3. **You need to process a string or array from both ends**.
4. **There are two moving parts** in the problem (one fast, one slow).

---

## **🔹 Types of Two Pointer Approaches**
### **1️⃣ Opposite Direction Two Pointers**
- Used when iterating from both ends of an array.
- Common in **Palindrome Checking**, **Sorting**, **Pair Sum** problems.

### **📌 Example 1: Two Sum (Sorted Array)**
Find two numbers in a **sorted** array that add up to a target sum.

```javascript
function twoSumSorted(arr, target) {
    let left = 0, right = arr.length - 1;

    while (left < right) {
        let sum = arr[left] + arr[right];

        if (sum === target) return [left, right]; // Found the pair
        else if (sum < target) left++;  // Increase left to increase sum
        else right--;  // Decrease right to decrease sum
    }

    return []; // No pair found
}

// Example
console.log(twoSumSorted([1, 2, 3, 4, 6], 6)); // Output: [1, 3]
```
**Time Complexity**: **O(N)** ✅  

---

### **2️⃣ Same Direction Two Pointers (Fast & Slow Pointers)**
- One pointer moves **faster** than the other.
- Common in **Removing Duplicates**, **Finding Cycles in a Linked List**, **Merging Arrays**.

### **📌 Example 2: Remove Duplicates from Sorted Array**
Given a **sorted** array, remove duplicates **in-place**.

```javascript
function removeDuplicates(arr) {
    if (arr.length === 0) return 0;

    let slow = 0;

    for (let fast = 1; fast < arr.length; fast++) {
        if (arr[fast] !== arr[slow]) {
            slow++;
            arr[slow] = arr[fast]; // Move unique element forward
        }
    }

    return slow + 1; // New length
}

// Example
console.log(removeDuplicates([1, 1, 2, 2, 3, 4])); // Output: 4 (array becomes [1, 2, 3, 4])
```
**Time Complexity**: **O(N)** ✅  

---

### **3️⃣ Two Pointers in Strings**
- Used for **checking palindromes**, **comparing substrings**, **merging characters**.

### **📌 Example 3: Valid Palindrome**
Check if a given string is a palindrome (ignoring case and non-alphanumeric characters).

```javascript
function isPalindrome(s) {
    s = s.replace(/[^a-zA-Z0-9]/g, '').toLowerCase(); // Clean string
    let left = 0, right = s.length - 1;

    while (left < right) {
        if (s[left] !== s[right]) return false;
        left++;
        right--;
    }

    return true;
}

// Example
console.log(isPalindrome("A man, a plan, a canal: Panama")); // Output: true
```
**Time Complexity**: **O(N)** ✅  

---

# **🔹 Leetcode Problems for Practice**
Here are some **Leetcode problems** categorized by difficulty.

## **🔥 Easy Problems**
| **Problem** | **Problem Link** | **Two Pointer Type** |
|-------------|-----------------|--------------------|
| **125. Valid Palindrome** | [🔗 Link](https://leetcode.com/problems/valid-palindrome/) | **Opposite Direction** |
| **167. Two Sum II - Input Array is Sorted** | [🔗 Link](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/) | **Opposite Direction** |
| **26. Remove Duplicates from Sorted Array** | [🔗 Link](https://leetcode.com/problems/remove-duplicates-from-sorted-array/) | **Fast & Slow Pointers** |
| **88. Merge Sorted Array** | [🔗 Link](https://leetcode.com/problems/merge-sorted-array/) | **Two Pointer Merging** |
| **345. Reverse Vowels of a String** | [🔗 Link](https://leetcode.com/problems/reverse-vowels-of-a-string/) | **Opposite Direction** |

---

## **⚡ Medium Problems**
| **Problem** | **Problem Link** | **Two Pointer Type** |
|-------------|-----------------|--------------------|
| **11. Container With Most Water** | [🔗 Link](https://leetcode.com/problems/container-with-most-water/) | **Opposite Direction** |
| **15. 3Sum** | [🔗 Link](https://leetcode.com/problems/3sum/) | **Opposite Direction** |
| **16. 3Sum Closest** | [🔗 Link](https://leetcode.com/problems/3sum-closest/) | **Opposite Direction** |
| **18. 4Sum** | [🔗 Link](https://leetcode.com/problems/4sum/) | **Opposite Direction** |
| **209. Minimum Size Subarray Sum** | [🔗 Link](https://leetcode.com/problems/minimum-size-subarray-sum/) | **Fast & Slow Pointers** |
| **438. Find All Anagrams in a String** | [🔗 Link](https://leetcode.com/problems/find-all-anagrams-in-a-string/) | **Sliding Window + Two Pointers** |

---

## **🚀 Hard Problems**
| **Problem** | **Problem Link** | **Two Pointer Type** |
|-------------|-----------------|--------------------|
| **42. Trapping Rain Water** | [🔗 Link](https://leetcode.com/problems/trapping-rain-water/) | **Opposite Direction** |
| **76. Minimum Window Substring** | [🔗 Link](https://leetcode.com/problems/minimum-window-substring/) | **Sliding Window + Two Pointers** |
| **680. Valid Palindrome II** | [🔗 Link](https://leetcode.com/problems/valid-palindrome-ii/) | **Opposite Direction** |
| **986. Interval List Intersections** | [🔗 Link](https://leetcode.com/problems/interval-list-intersections/) | **Two Pointer Merging** |
| **1234. Replace the Substring for Balanced String** | [🔗 Link](https://leetcode.com/problems/replace-the-substring-for-balanced-string/) | **Sliding Window + Two Pointers** |

---

# **🔹 Summary**
1️⃣ **Opposite Direction Two Pointers** → Used for **pair sum, palindromes, merging sorted arrays**.  
2️⃣ **Same Direction (Fast & Slow Pointers)** → Used for **removing duplicates, linked list cycles**.  
3️⃣ **Common Patterns**:
   - **Sorted array?** → Try **Two Pointers** instead of nested loops.  
   - **Checking pairs or triplets?** → Use **Opposite Direction**.  
   - **Looking for minimal/maximal window?** → Use **Sliding Window + Two Pointers**.  

