Here’s a **comprehensive guide** to the **Sliding Window** technique in **JavaScript**, including:

✅ **How to spot when to use it**  
✅ **Fixed-size & Variable-size Sliding Window examples**  
✅ **How to determine if Sliding Window is the right choice**  
✅ **Leetcode problems for practice**  

---

# **🚀 Sliding Window Technique in JavaScript**

The **Sliding Window** technique is an **optimization method** used to efficiently solve problems involving **subarrays or substrings**. Instead of repeatedly recalculating values from scratch, we "slide" a **window** over the input, reusing previous computations.

## **🔹 When to Use Sliding Window?**
You should consider using **Sliding Window** when:
1. **The problem involves contiguous elements** (subarrays or substrings).
2. **You need to find an optimal subarray** (max/min/longest/shortest).
3. **Brute force approaches involve nested loops** (O(N²) or worse).
4. **The problem requires dynamically expanding/shrinking a window** to meet a condition.

## **🔹 How to Figure Out If Sliding Window Is the Right Choice**
To determine if **Sliding Window** is suitable:
- If the problem asks for:
  - **Max/Min sum or length of a contiguous subarray** → Consider **Sliding Window**.
  - **Finding a substring or subarray with a specific property** → Try **Sliding Window**.
- If your **brute-force approach involves nested loops**, try **optimizing** with **Sliding Window**.

---

## **🔹 Types of Sliding Window**
### **1️⃣ Fixed-size Sliding Window**
- The window size is predefined.
- We slide it one step at a time while keeping track of the desired value.

### **📌 Example 1: Maximum Sum of `K` Consecutive Elements**
**Problem Statement**:  
Find the maximum sum of any contiguous subarray of size `K`.

**🔴 Brute Force Approach**:  
Use nested loops (**O(N * K)**).

**🟢 Optimized Sliding Window Approach (O(N))**:
```javascript
function maxSubarraySum(arr, k) {
    let maxSum = -Infinity;
    let windowSum = 0;

    // Compute the sum of the first 'k' elements
    for (let i = 0; i < k; i++) {
        windowSum += arr[i];
    }

    maxSum = windowSum;

    // Slide the window over the array
    for (let i = k; i < arr.length; i++) {
        windowSum = windowSum - arr[i - k] + arr[i];  // Slide window
        maxSum = Math.max(maxSum, windowSum);
    }

    return maxSum;
}

// Example
console.log(maxSubarraySum([2, 1, 5, 1, 3, 2], 3)); // Output: 9 (5+1+3)
```
**Time Complexity**: **O(N)** ✅  
**Space Complexity**: **O(1)** ✅  

---

### **2️⃣ Variable-size Sliding Window**
- The window expands until the condition is met.
- Then, it shrinks to find the optimal subarray.

### **📌 Example 2: Smallest Subarray with Sum ≥ `S`**
**Problem Statement**:  
Find the length of the smallest contiguous subarray whose sum is **≥ `S`**.

**🟢 Sliding Window Approach (O(N))**:
```javascript
function minSubarrayLength(arr, S) {
    let left = 0;
    let minLength = Infinity;
    let windowSum = 0;

    for (let right = 0; right < arr.length; right++) {
        windowSum += arr[right];

        while (windowSum >= S) {
            minLength = Math.min(minLength, right - left + 1);
            windowSum -= arr[left];  // Shrink window from left
            left++;
        }
    }

    return minLength === Infinity ? 0 : minLength;
}

// Example
console.log(minSubarrayLength([2, 3, 1, 2, 4, 3], 7)); // Output: 2 ([4,3] or [3,4])
```
**Time Complexity**: **O(N)** ✅  
**Space Complexity**: **O(1)** ✅  

---
Here’s a **comprehensive list** of **20+ Sliding Window problems** from **Leetcode**, categorized by difficulty level. Solving these will help you master **both Fixed-size and Variable-size Sliding Window** techniques. 🚀  

---

## **🔹 Leetcode Sliding Window Problems**
  
### **🔥 Easy Problems**
| **Problem** | **Problem Link** | **Sliding Window Type** |
|-------------|-----------------|--------------------|
| **643. Maximum Average Subarray I** | [🔗 Link](https://leetcode.com/problems/maximum-average-subarray-i/) | **Fixed** |
| **485. Max Consecutive Ones** | [🔗 Link](https://leetcode.com/problems/max-consecutive-ones/) | **Fixed** |
| **1004. Max Consecutive Ones III** | [🔗 Link](https://leetcode.com/problems/max-consecutive-ones-iii/) | **Variable** |
| **1456. Maximum Number of Vowels in a Substring of Given Length** | [🔗 Link](https://leetcode.com/problems/maximum-number-of-vowels-in-a-substring-of-given-length/) | **Fixed** |
| **1838. Frequency of the Most Frequent Element** | [🔗 Link](https://leetcode.com/problems/frequency-of-the-most-frequent-element/) | **Variable** |

---

### **⚡ Medium Problems**
| **Problem** | **Problem Link** | **Sliding Window Type** |
|-------------|-----------------|--------------------|
| **3. Longest Substring Without Repeating Characters** | [🔗 Link](https://leetcode.com/problems/longest-substring-without-repeating-characters/) | **Variable** |
| **209. Minimum Size Subarray Sum** | [🔗 Link](https://leetcode.com/problems/minimum-size-subarray-sum/) | **Variable** |
| **424. Longest Repeating Character Replacement** | [🔗 Link](https://leetcode.com/problems/longest-repeating-character-replacement/) | **Variable** |
| **567. Permutation in String** | [🔗 Link](https://leetcode.com/problems/permutation-in-string/) | **Fixed** |
| **930. Binary Subarrays With Sum** | [🔗 Link](https://leetcode.com/problems/binary-subarrays-with-sum/) | **Variable** |
| **1208. Get Equal Substrings Within Budget** | [🔗 Link](https://leetcode.com/problems/get-equal-substrings-within-budget/) | **Variable** |
| **1493. Longest Subarray of 1's After Deleting One Element** | [🔗 Link](https://leetcode.com/problems/longest-subarray-of-1s-after-deleting-one-element/) | **Variable** |
| **2024. Maximize the Confusion of an Exam** | [🔗 Link](https://leetcode.com/problems/maximize-the-confusion-of-an-exam/) | **Variable** |
| **1695. Maximum Erasure Value** | [🔗 Link](https://leetcode.com/problems/maximum-erasure-value/) | **Variable** |
| **1658. Minimum Operations to Reduce X to Zero** | [🔗 Link](https://leetcode.com/problems/minimum-operations-to-reduce-x-to-zero/) | **Variable** |

---

### **🚀 Hard Problems**
| **Problem** | **Problem Link** | **Sliding Window Type** |
|-------------|-----------------|--------------------|
| **76. Minimum Window Substring** | [🔗 Link](https://leetcode.com/problems/minimum-window-substring/) | **Variable** |
| **239. Sliding Window Maximum** | [🔗 Link](https://leetcode.com/problems/sliding-window-maximum/) | **Fixed + Deque** |
| **295. Find Median from Data Stream** | [🔗 Link](https://leetcode.com/problems/find-median-from-data-stream/) | **Variable + Heap** |
| **1423. Maximum Points You Can Obtain from Cards** | [🔗 Link](https://leetcode.com/problems/maximum-points-you-can-obtain-from-cards/) | **Variable** |
| **992. Subarrays with K Different Integers** | [🔗 Link](https://leetcode.com/problems/subarrays-with-k-different-integers/) | **Variable** |
| **1987. Number of Unique Good Subsequences** | [🔗 Link](https://leetcode.com/problems/number-of-unique-good-subsequences/) | **Variable** |
| **2271. Maximum White Tiles Covered by a Carpet** | [🔗 Link](https://leetcode.com/problems/maximum-white-tiles-covered-by-a-carpet/) | **Variable** |
| **1343. Number of Sub-arrays of Size K and Average Greater than or Equal to Threshold** | [🔗 Link](https://leetcode.com/problems/number-of-sub-arrays-of-size-k-and-average-greater-than-or-equal-to-threshold/) | **Fixed** |

---


# **🔹 How to Approach These Problems?**

1️⃣ **Understand the problem**:  
   - Are we looking for **fixed-length subarrays**? → **Fixed-size Sliding Window**  
   - Are we dynamically **expanding/shrinking**? → **Variable-size Sliding Window**  

2️⃣ **Think about the brute-force approach**:  
   - If nested loops lead to **O(N²) complexity**, try **Sliding Window**.  

3️⃣ **Implement the optimized Sliding Window approach**:  
   - **Fixed-size**: Maintain a sum/count within a window and slide.  
   - **Variable-size**: Expand until the condition is met, then shrink.  

---


## **🔹 Summary**

1️⃣ **Fixed-size Sliding Window** → Used when a specific window size is **predefined**.  
2️⃣ **Variable-size Sliding Window** → Used when the **window expands/shrinks dynamically**.  
3️⃣ **Key to spotting Sliding Window**:
   - **Contiguous subarray/substring**.
   - **Optimal sum/length/count within a window**.
   - **Repeated calculations in brute-force approach**.  

