# *01. Multiply Two Linked Lists*

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/multiply-two-linked-lists/1)

### Problem Description

 You are given two singly linked lists, L1 and L2, where each node holds a digit. These digits, when read in sequence, form two numbers

- The task is to calculate the product of these two numbers and return the result modulo \(10^9 + 7\).
  
#### Example 1:

Input: 
- LinkedList L1: 3 -> 2
- LinkedList L2: 2
  
Output: 
- 64

Explanation: The first list represents the number 32, and the second list represents the number 2. The product of 32 and 2 is 64..


### Constraints:
- \(1 \leq \text{number of nodes} \leq 10^5\).
- \(1 \leq \text{node.data} \leq 10^3\).

### My Approach

1. **Converting Linked Lists to Numbers:**
   - Traverse through each linked list, treating the digits as part of a number. As you accumulate the digits, take modulo \(10^9 + 7\) at each step to prevent overflow.

2. **Multiplication and Modulo Operation:**
   - Multiply the two numbers obtained from the linked lists.
   - Take the result modulo \(10^9 + 7\) to ensure the result is within the specified range.

3. **Handling Edge Cases:**
   - Both linked lists have only one node, making the result straightforward.
   - Consider large numbers with long lists by applying the modulo at every step to manage overflow.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** (O(max(n, m))), where (n) is the length of L1 and (m) is the length of L2, as we need to traverse each list once to convert it into a number.
- **Expected Auxiliary Space Complexity:** (O(1)), since no extra space beyond a few variables is required.

### Code (C++)

```cpp
class Solution {
  public:
    long long multiplyTwoLists(Node *first, Node *second) {
        long long num1 = 0, num2 = 0;
        const int MOD = 1000000007;
        while (first != NULL) {
            num1 = (num1 * 10 + first->data) % MOD;
            first = first->next;
        }
        while (second != NULL) {
            num2 = (num2 * 10 + second->data) % MOD;
            second = second->next;
        }
        return (num1 * num2) % MOD;
    }
};
```

### Code (Java)

```java
class Solution {
    public long multiplyTwoLists(Node first, Node second) {
        long num1 = 0, num2 = 0;
        final int MOD = 1000000007;

        while (first != null) {
            num1 = (num1 * 10 + first.data) % MOD;
            first = first.next;
        }

        while (second != null) {
            num2 = (num2 * 10 + second.data) % MOD;
            second = second.next;
        }

        return (num1 * num2) % MOD;
    }
}
```

### Code (Python)

```python
class Solution:
    def multiply_two_lists(self, first, second):
        num1 = 0
        num2 = 0
        MOD = 1000000007
        while first is not None:
            num1 = (num1 * 10 + first.data) % MOD
            first = first.next
        while second is not None:
            num2 = (num2 * 10 + second.data) % MOD
            second = second.next
        return (num1 * num2) % MOD
```
