# 🚀 **Linked List In-Place Reversal Technique**
---

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

# 🔥 **🔹 Leetcode Problems for Practice**
✅ Here are **Leetcode problems** that can be solved using **In-Place Linked List Reversal**:

| **Problem** | **Difficulty** | **Link** |
|-------------|----------------|----------|
| **206. Reverse Linked List** | Easy | [🔗 Link](https://leetcode.com/problems/reverse-linked-list/) |
| **92. Reverse Linked List II** | Medium | [🔗 Link](https://leetcode.com/problems/reverse-linked-list-ii/) |
| **25. Reverse Nodes in k-Group** | Hard | [🔗 Link](https://leetcode.com/problems/reverse-nodes-in-k-group/) |
| **143. Reorder List** | Medium | [🔗 Link](https://leetcode.com/problems/reorder-list/) |
| **328. Odd Even Linked List** | Medium | [🔗 Link](https://leetcode.com/problems/odd-even-linked-list/) |

---

# 🚀 **🔹 Summary**
✅ **Key Techniques**:
- Reverse the list in-place using **three pointers**.  
- Reverse **sub-lists** or **k-groups** efficiently.  
- Time Complexity → **O(N)**  
- Space Complexity → **O(1)**  

---

🔥 **Next Steps?**  
Try solving the **Leetcode problems** above and let me know if you need explanations! 😊🚀
