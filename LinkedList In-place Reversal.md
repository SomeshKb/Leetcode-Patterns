# 🚀 **Linked List In-Place Reversal Technique**


# ✅ **🔹 When to Use In-Place Reversal?**
You should consider using **In-Place Reversal** when:
1. You need to **reverse the entire list** or part of it.
2. You want to **rotate or reorder the list** without extra memory.
3. You want to **reverse nodes in groups**.
4. The problem mentions:
   - **Reverse sub-list**
   - **Rotate the list**
   - **Reverse in k-groups**
   - **Rearrange in-place**

---

# 🔥 **🔹 Key Steps for In-Place Reversal**
1. **Initialize 3 Pointers**:
   - `prev` → Points to the previous node.
   - `current` → The node being processed.
   - `next` → Stores the next node temporarily.
2. **Reverse the Pointers**:
   - Store the next node → `next = current.next`
   - Reverse the pointer → `current.next = prev`
   - Move the pointers:
     - `prev = current`
     - `current = next`
3. **Repeat** until all nodes are processed.

---

# ✅ **📌 Example 1: Reverse Entire Linked List**

### **Input**
```
1 → 2 → 3 → 4 → 5  
```
### **Output**
```
5 → 4 → 3 → 2 → 1  
```

### **💡 JavaScript Solution**
```javascript
class Node {
    constructor(value) {
        this.value = value;
        this.next = null;
    }
}

function reverseLinkedList(head) {
    let prev = null;
    let current = head;

    while (current !== null) {
        let next = current.next;   // Store the next node
        current.next = prev;        // Reverse the pointer
        prev = current;             // Move prev forward
        current = next;             // Move current forward
    }

    return prev;  // New head of reversed list
}

// ✅ Example Usage
let head = new Node(1);
head.next = new Node(2);
head.next.next = new Node(3);
head.next.next.next = new Node(4);
head.next.next.next.next = new Node(5);

console.log("Original List:");
let current = head;
while (current) {
    console.log(current.value);
    current = current.next;
}

let reversedHead = reverseLinkedList(head);
console.log("\nReversed List:");
while (reversedHead) {
    console.log(reversedHead.value);
    reversedHead = reversedHead.next;
}
```
### ✅ **Time Complexity:** **O(N)**  
### ✅ **Space Complexity:** **O(1)** (No extra space used)  

---

# 🔥 **📌 Example 2: Reverse a Sublist of a Linked List**

### **Problem Statement**
Given a linked list, reverse the nodes between **position `m` and `n`**.

### **Input**
```
1 → 2 → 3 → 4 → 5  
m = 2, n = 4  
```
### **Output**
```
1 → 4 → 3 → 2 → 5  
```

### **💡 JavaScript Solution**
```javascript
function reverseBetween(head, m, n) {
    if (!head || m === n) return head;

    let dummy = new Node(0);
    dummy.next = head;
    let prev = dummy;

    // Move prev to the node before the reversal starts
    for (let i = 1; i < m; i++) {
        prev = prev.next;
    }

    let start = prev.next;    // First node of the sublist to reverse
    let then = start.next;    // Node after start

    // Reverse the sublist between m and n
    for (let i = 0; i < n - m; i++) {
        start.next = then.next;    // Detach the `then` node
        then.next = prev.next;     // Insert `then` at the beginning
        prev.next = then;          // Point `prev` to `then`
        then = start.next;         // Move `then` forward
    }

    return dummy.next;
}

// ✅ Example Usage
let head2 = new Node(1);
head2.next = new Node(2);
head2.next.next = new Node(3);
head2.next.next.next = new Node(4);
head2.next.next.next.next = new Node(5);

console.log("\nOriginal List:");
let current2 = head2;
while (current2) {
    console.log(current2.value);
    current2 = current2.next;
}

let reversedSublist = reverseBetween(head2, 2, 4);
console.log("\nReversed Sublist:");
while (reversedSublist) {
    console.log(reversedSublist.value);
    reversedSublist = reversedSublist.next;
}
```
### ✅ **Time Complexity:** **O(N)**  
### ✅ **Space Complexity:** **O(1)**  

---

# 🔥 **📌 Example 3: Reverse Linked List in k-Groups**

### **Problem Statement**
Given a linked list, reverse every **k** consecutive nodes. If the remaining nodes are fewer than **k**, leave them as is.

### **Input**
```
1 → 2 → 3 → 4 → 5 → 6 → 7 → 8  
k = 3  
```
### **Output**
```
3 → 2 → 1 → 6 → 5 → 4 → 7 → 8  
```

### **💡 JavaScript Solution**
```javascript
function reverseKGroup(head, k) {
    if (!head || k === 1) return head;

    let dummy = new Node(0);
    dummy.next = head;

    let prev = dummy;
    let current = head;

    // Count total nodes
    let count = 0;
    while (current) {
        count++;
        current = current.next;
    }

    while (count >= k) {
        current = prev.next;
        let next = current.next;

        for (let i = 1; i < k; i++) {
            current.next = next.next;
            next.next = prev.next;
            prev.next = next;
            next = current.next;
        }

        prev = current;
        count -= k;
    }

    return dummy.next;
}

// ✅ Example Usage
let head3 = new Node(1);
head3.next = new Node(2);
head3.next.next = new Node(3);
head3.next.next.next = new Node(4);
head3.next.next.next.next = new Node(5);
head3.next.next.next.next.next = new Node(6);
head3.next.next.next.next.next.next = new Node(7);
head3.next.next.next.next.next.next.next = new Node(8);

console.log("\nOriginal List:");
let current3 = head3;
while (current3) {
    console.log(current3.value);
    current3 = current3.next;
}

let reversedKGroup = reverseKGroup(head3, 3);
console.log("\nReversed k-Group List:");
while (reversedKGroup) {
    console.log(reversedKGroup.value);
    reversedKGroup = reversedKGroup.next;
}
```
### ✅ **Time Complexity:** **O(N)**  
### ✅ **Space Complexity:** **O(1)**  

---

# 🚀 **Leetcode Problems for Linked List In-Place Reversal**

# ✅ **🔥 Easy Problems**
| **Problem**                         | **Leetcode Link**                                   | **Description**                       |
|-------------------------------------|----------------------------------------------------|--------------------------------------|
| **206. Reverse Linked List**         | [🔗 Link](https://leetcode.com/problems/reverse-linked-list/)          | Reverse an entire singly linked list |
| **83. Remove Duplicates from Sorted List**  | [🔗 Link](https://leetcode.com/problems/remove-duplicates-from-sorted-list/) | Remove duplicates in-place          |
| **876. Middle of the Linked List**   | [🔗 Link](https://leetcode.com/problems/middle-of-the-linked-list/)     | Find the middle node using two pointers |
| **21. Merge Two Sorted Lists**       | [🔗 Link](https://leetcode.com/problems/merge-two-sorted-lists/)        | Merge two linked lists in-place     |
| **141. Linked List Cycle**           | [🔗 Link](https://leetcode.com/problems/linked-list-cycle/)             | Detect cycle using **slow & fast** pointers |
| **234. Palindrome Linked List**      | [🔗 Link](https://leetcode.com/problems/palindrome-linked-list/)        | Check if the list is a palindrome by reversing half |



# ✅ **⚡ Medium Problems**
| **Problem**                         | **Leetcode Link**                                   | **Description**                         |
|-------------------------------------|----------------------------------------------------|----------------------------------------|
| **92. Reverse Linked List II**      | [🔗 Link](https://leetcode.com/problems/reverse-linked-list-ii/)         | Reverse a sublist between `m` and `n` |
| **147. Insertion Sort List**        | [🔗 Link](https://leetcode.com/problems/insertion-sort-list/)            | Sort a linked list using insertion sort |
| **143. Reorder List**               | [🔗 Link](https://leetcode.com/problems/reorder-list/)                   | Rearrange nodes in-place              |
| **328. Odd Even Linked List**       | [🔗 Link](https://leetcode.com/problems/odd-even-linked-list/)           | Separate odd and even nodes           |
| **61. Rotate List**                  | [🔗 Link](https://leetcode.com/problems/rotate-list/)                    | Rotate list by `k` steps in-place     |
| **725. Split Linked List in Parts** | [🔗 Link](https://leetcode.com/problems/split-linked-list-in-parts/)     | Split a list into `k` parts in-place |
| **19. Remove Nth Node From End**    | [🔗 Link](https://leetcode.com/problems/remove-nth-node-from-end-of-list/) | Remove the `n`-th node from the end |
| **430. Flatten a Multilevel Doubly Linked List** | [🔗 Link](https://leetcode.com/problems/flatten-a-multilevel-doubly-linked-list/) | Flatten a multilevel linked list in-place |



# ✅ **🚀 Hard Problems**
| **Problem**                         | **Leetcode Link**                                   | **Description**                        |
|-------------------------------------|----------------------------------------------------|---------------------------------------|
| **25. Reverse Nodes in k-Group**    | [🔗 Link](https://leetcode.com/problems/reverse-nodes-in-k-group/)        | Reverse linked list in groups of `k` |
| **23. Merge k Sorted Lists**        | [🔗 Link](https://leetcode.com/problems/merge-k-sorted-lists/)            | Merge multiple lists in-place         |
| **146. LRU Cache**                   | [🔗 Link](https://leetcode.com/problems/lru-cache/)                        | LRU Cache implementation with linked list |
| **1474. Delete N Nodes After M Nodes of a Linked List** | [🔗 Link](https://leetcode.com/problems/delete-n-nodes-after-m-nodes-of-a-linked-list/) | Delete `n` nodes after `m` nodes |
| **138. Copy List with Random Pointer** | [🔗 Link](https://leetcode.com/problems/copy-list-with-random-pointer/)   | Clone a complex linked list           |
| **1171. Remove Zero Sum Consecutive Nodes** | [🔗 Link](https://leetcode.com/problems/remove-zero-sum-consecutive-nodes-from-linked-list/) | Remove consecutive nodes summing to zero |
| **708. Insert into a Sorted Circular Linked List** | [🔗 Link](https://leetcode.com/problems/insert-into-a-sorted-circular-linked-list/) | Insert into circular linked list |
| **815. Bus Routes**                  | [🔗 Link](https://leetcode.com/problems/bus-routes/)                       | Bus route scheduling using linked list |
| **430. Flatten Multilevel Doubly Linked List** | [🔗 Link](https://leetcode.com/problems/flatten-a-multilevel-doubly-linked-list/) | Flatten a doubly linked list |

---

# ✅ **🔥 Key Patterns for In-Place Reversal Problems**
### 🔹 **1️⃣ Reverse the Entire List**
- Use **three pointers**: `prev`, `current`, `next`.  
- Time complexity → **O(N)**  
- Space complexity → **O(1)**  

### 🔹 **2️⃣ Reverse a Sublist**
- Use two pointers to **find the sublist**.  
- Reverse the section by manipulating the links.  
- Time complexity → **O(N)**  
- Space complexity → **O(1)**  

### 🔹 **3️⃣ Reverse in k-Groups**
- Iterate through the list **k** nodes at a time.  
- Reverse the current group, keep track of the next node.  
- Time complexity → **O(N)**  
- Space complexity → **O(1)**  


