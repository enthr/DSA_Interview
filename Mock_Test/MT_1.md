# DSA | Mock Test-1 | JavaScript


## 1. Move Zeroes


- Given an integer array nums, move all 0's to the end of it while maintaining the relative order of the non-zero elements.
- Note that you must do this in-place without making a copy of the array.


```
Example 1:
Input: nums = [0,1,0,3,12]
Output: [1,3,12,0,0]

Example 2:
Input: nums = [0]
Output: [0]

Constraints:
a. 1 <= nums.length <= 10^4
b. -2^31 <= nums[i] <= 2^31 - 1
```


### Solution


- Time Complexity: $O(n)$
- Space Complexity: $O(1)$


```javascript
const moveZeros = (nums) => {
    let count = 0;
    for (let i = 0; i < nums.length; i++) {
        if (nums[i] !== 0) {
            nums[count] = nums[i];
            count++;
        }
    }
    for (count; count < nums.length; count++) {
        nums[count] = 0;
    }
    return nums;
}
console.log('Array: ', moveZeros(nums));
```


## 2. First Unique Character in a String


- Given a string s, find the first non-repeating character in it and return its index. If it does not exist, return -1.


```
Example 1:
Input: s = "leetcode"
Output: 0

Example 2:
Input: s = "loveleetcode"
Output: 2

Example 3:
Input: s = "aabb"
Output: -1

Constraints:
a. 1 <= s.length <= 10^5
b. s consists of only lowercase English letters.
```


### Solution - 1 | General Approach


- Time Complexity: $O(n)$ where n = length of string
- Space Complexity: $O(k)$ where k = number of unique characters


```javascript
const s = 'loveleetcode';
const firstUniqueChar = (s) => {
    const map = new Map();
    for (let i = 0; i < s.length; i++) {
        if (map.has(s[i])) { 
            map.set(s[i], map.get(s[i]) + 1);
        }
        else {
            map.set(s[i], 1);
        }
    }
    for (let i = 0; i < s.length; i++) {
        if (map.get(s[i]) === 1) {
            return i;
        } 
    }

    return -1;
};
console.log('First Unique Character Index: ', firstUniqueChar(s));
```


### Solution - 2 | Considering Constraints


- Time Complexity: $O(n)$ where n = length of string
- Space Complexity: $O(1)$


```javascript
// Since All Characters are Lowercase Letters, We Can Use an Array of 26 to Store the Frequency of Each Character
// Then We Can Iterate Through the String Again to Find the First Character with Frequency of 1
const s = 'loveleetcode';
const firstUniqueChar = (s) => {
    const map = new Array(26).fill(0);
    for (let i = 0; i < s.length; i++) {
        const index = s.charCodeAt(i) - 'a'.charCodeAt(0);
        map[index] = map[index] + 1;
    }

    for (let i = 0; i < s.length; i++) {
        const index = s.charCodeAt(i) - 'a'.charCodeAt(0);
        if (map[index] === 1) {
            return i;
        }
    }
    return -1;
};
console.log('First Unique Character Index: ', firstUniqueChar(s));
```