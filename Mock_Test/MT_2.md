# DSA | Mock Test-2 | JavaScript


## 1. Given a non-negative integer x, return the square root of x rounded down to the nearest integer. The returned integer should be non-negative as well. You must not use any built-in exponent function or operator. 


```
Example 1:
Input: x = 4 Output: 2 Explanation: The square root of 4 is 2, so we return 2.

Example 2:
Input: x = 8 Output: 2 Explanation: The square root of 8 is 2.82842..., and since we round it down to the nearest integer, 2 is returned.

Constraints:
0 <= x <= 231 - 1
```


### Solution


- Time Complexity: $O(log n)$
- Space Complexity: $O(1)$


```javascript
const mySqrt = (n) => {
    if (n === 0) {
        return 0;
    }

    let left = 1;
    let right = Math.floor(n / 2) + 1;

    while (left <= right) {
        let mid = Math.floor((left + right) / 2);
        let square = mid * mid;

        if (square === n) {
            return mid;
        } else if (square < n) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }

    return right;
};
```


## 2. You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.


- You may assume the two numbers do not contain any leading zero, except the number 0 itself.


```
Example 1:
Input: l1 = [2,4,3], l2 = [5,6,4] Output: [7,0,8]
Explanation: 342 + 465 = 807.

Example 2:
Input: l1 = [0], l2 = [0] Output: [0]

Example 3:
Input: l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9] Output: [8,9,9,9,0,0,0,1]

Constraints:
The number of nodes in each linked list is in the range [1, 100].
0 <= Node.val <= 9
It is guaranteed that the list represents a number that does not have leading zeros.
```


### Solution


- Time Complexity: $O(n)$
- Space Complexity: $O(n)$


```javascript
class ListNode {
    constructor(val, next) {
        this.val = (val === undefined ? 0 : val)
        this.next = (next === undefined ? null : next)
    }
}

const addTwoNumbers = (l1, l2) => {
    let carry = 0;
    let previousNode = new ListNode();
    let headNode = previousNode;

    while (l1 || l2 || carry) {
        let val1 = 0;
        let val2 = 0;

        if (l1) {
            val1 = l1.val;
            l1 = l1.next;

        }
        
        if (l2) {
            val2 = l2.val;
            l2 = l2.next;
        }

        let sum = val1 + val2 + carry;

        carry = (sum > 9) ? 1 : 0;
        let digit = (sum % 10);

        const currentNode = new ListNode(digit);
        previousNode.next = currentNode;
        previousNode = currentNode;

    }

    return headNode.next;
};
```