# 🚀 Two Heaps Technique
## 🔹 **Introduction**
The **Two Heaps technique** is a powerful algorithmic approach used to efficiently solve problems involving:
- **Median finding**
- **Balancing two parts of a dataset**
- **Maintaining order or constraints** dynamically  
- **Efficient retrieval of min/max values**

✅ This technique utilizes:
- **Min Heap** → To store the larger half of the data.  
- **Max Heap** → To store the smaller half of the data.  

By **balancing the heaps**, you can quickly access the **median** or perform operations on two halves efficiently.

---

## 🔹 **When to Use Two Heaps?**
You should consider using **Two Heaps** when:
1. **You need to efficiently find the median** in a stream of numbers.
2. **You want to balance two sets** of values (e.g., smaller and larger halves).
3. **You need to efficiently perform insertion and removal** while keeping track of min/max values.
4. **You need dynamic ordering** or finding a running median.

---

## 🔹 **How to Approach Two Heaps Problems?**
1️⃣ **Initialize two heaps:**  
   - **Min Heap** → For the larger half of the numbers (heap root is the smallest of the larger half).  
   - **Max Heap** → For the smaller half of the numbers (heap root is the largest of the smaller half).  

2️⃣ **Insertion Logic:**  
   - Insert a new number into the **Max Heap** by default.  
   - If the number is larger than the **Min Heap’s root**, push it into the **Min Heap**.  
   - Ensure the two heaps are balanced (size difference ≤ 1).

3️⃣ **Median Calculation:**  
   - If the heaps are balanced, the median is the average of both roots.  
   - If one heap is larger, the median is the root of the larger heap.

---

## 🔹 **How to Identify Questions Solvable Using Two Heaps?**
✅ Look for the following **clues** in problem statements:
- **Finding the median** in a data stream.  
- **Maintaining the Kth largest/smallest element** efficiently.  
- **Splitting data** into two balanced groups.  
- **Continuous insertion/removal** operations with efficient median retrieval.

---

## 🔹 **Variations of Two Heaps Technique**
### 🔥 **1️⃣ Median of a Stream**
- **Use Case:** Finding the **median of a dynamically changing data stream**.
- **Logic:** Balance the **Min Heap** and **Max Heap**.
- **Complexity:** O(log N) for insertion and O(1) for median retrieval.

---

### 🚀 **2️⃣ Kth Largest or Smallest Element**
- **Use Case:** Find the **Kth largest/smallest** element in an array.
- **Logic:**  
   - Use a **Min Heap** to track the largest `K` elements.  
   - Use a **Max Heap** to track the smallest `K` elements.
- **Complexity:** O(log K) for insertion and retrieval.

---

### ⚡ **3️⃣ Balancing Workloads**
- **Use Case:** Splitting data into two balanced groups for **load balancing**.
- **Logic:**  
   - **Min Heap** → Tracks the heavier workload.  
   - **Max Heap** → Tracks the lighter workload.
- **Complexity:** O(log N) for balancing operations.

---

## 🔹 **Examples with Code**

### ✅ **Example 1: Running Median of a Data Stream**
📌 **Problem:**  
Find the **median** after each insertion into a stream of integers.

```javascript
class MedianFinder {
    constructor() {
        this.maxHeap = new MaxPriorityQueue();  // Lower half
        this.minHeap = new MinPriorityQueue();  // Upper half
    }

    addNum(num) {
        this.maxHeap.enqueue(num);
        
        // Balancing
        if (!this.minHeap.isEmpty() && this.maxHeap.front().element > this.minHeap.front().element) {
            this.minHeap.enqueue(this.maxHeap.dequeue().element);
        }

        // Balance heap sizes
        if (this.maxHeap.size() > this.minHeap.size() + 1) {
            this.minHeap.enqueue(this.maxHeap.dequeue().element);
        } else if (this.minHeap.size() > this.maxHeap.size()) {
            this.maxHeap.enqueue(this.minHeap.dequeue().element);
        }
    }

    findMedian() {
        if (this.maxHeap.size() === this.minHeap.size()) {
            return (this.maxHeap.front().element + this.minHeap.front().element) / 2;
        }
        return this.maxHeap.front().element;
    }
}

// Usage
const medianFinder = new MedianFinder();
medianFinder.addNum(1);
medianFinder.addNum(2);
console.log(medianFinder.findMedian());  // Output: 1.5
medianFinder.addNum(3);
console.log(medianFinder.findMedian());  // Output: 2
```
✅ **Time Complexity:** O(log N) for insertion, O(1) for median retrieval.

---

### ✅ **Example 2: Kth Largest Element in a Stream**
📌 **Problem:**  
Find the **Kth largest** element in a stream.

```javascript
class KthLargest {
    constructor(k, nums) {
        this.k = k;
        this.minHeap = new MinPriorityQueue();

        nums.forEach(num => this.add(num));
    }

    add(val) {
        this.minHeap.enqueue(val);

        if (this.minHeap.size() > this.k) {
            this.minHeap.dequeue();
        }

        return this.minHeap.front().element;
    }
}

// Example Usage
const kthLargest = new KthLargest(3, [4, 5, 8, 2]);
console.log(kthLargest.add(3));  // Output: 4
console.log(kthLargest.add(5));  // Output: 5
console.log(kthLargest.add(10)); // Output: 5
console.log(kthLargest.add(9));  // Output: 8
```
✅ **Time Complexity:** O(log K) for insertion.

---

## 🔹 **Leetcode Problems for Practice**

### 🔥 **Easy Problems**
| **Problem** | **Link** | **Difficulty** |
|-------------|---------|----------------|
| **703. Kth Largest Element in a Stream** | [🔗 Leetcode](https://leetcode.com/problems/kth-largest-element-in-a-stream/) | Easy |
| **1046. Last Stone Weight** | [🔗 Leetcode](https://leetcode.com/problems/last-stone-weight/) | Easy |

---

### ⚡ **Medium Problems**
| **Problem** | **Link** | **Difficulty** |
|-------------|---------|----------------|
| **295. Find Median from Data Stream** | [🔗 Leetcode](https://leetcode.com/problems/find-median-from-data-stream/) | Medium |
| **378. Kth Smallest Element in a Sorted Matrix** | [🔗 Leetcode](https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/) | Medium |
| **373. Find K Pairs with Smallest Sums** | [🔗 Leetcode](https://leetcode.com/problems/find-k-pairs-with-smallest-sums/) | Medium |

---

### 🚀 **Hard Problems**
| **Problem** | **Link** | **Difficulty** |
|-------------|---------|----------------|
| **480. Sliding Window Median** | [🔗 Leetcode](https://leetcode.com/problems/sliding-window-median/) | Hard |
| **502. IPO** | [🔗 Leetcode](https://leetcode.com/problems/ipo/) | Hard |
| **218. The Skyline Problem** | [🔗 Leetcode](https://leetcode.com/problems/the-skyline-problem/) | Hard |

---

## 🔹 **Key Takeaways**
✅ **Two Heaps technique** is used to solve median, balancing, and min/max retrieval problems efficiently.  
✅ It uses **Min and Max Heaps** to dynamically balance data streams.  
✅ **Complexity:** O(log N) for insertion and O(1) for median retrieval.  

