# [704. Binary Search](https://leetcode.com/problems/binary-search)

[中文文档](/solution/0700-0799/0704.Binary%20Search/README.md)

## Description

<p>Given a <strong>sorted</strong> (in ascending order) integer array <code>nums</code> of <code>n</code> elements and a <code>target</code> value, write a function to search <code>target</code> in <code>nums</code>. If <code>target</code> exists, then return its index, otherwise return <code>-1</code>.</p>

<p><br />

<strong>Example 1:</strong></p>

<pre>

<strong>Input:</strong> <code>nums</code> = [-1,0,3,5,9,12], <code>target</code> = 9

<strong>Output:</strong> 4

<strong>Explanation:</strong> 9 exists in <code>nums</code> and its index is 4



</pre>

<p><strong>Example 2:</strong></p>

<pre>

<strong>Input:</strong> <code>nums</code> = [-1,0,3,5,9,12], <code>target</code> = 2

<strong>Output:</strong> -1

<strong>Explanation:</strong> 2 does not exist in <code>nums</code> so return -1

</pre>

<p>&nbsp;</p>

<p><strong>Note:</strong></p>

<ol>
    <li>You may assume that all elements in <code>nums</code> are unique.</li>
    <li><code>n</code> will be in the range <code>[1, 10000]</code>.</li>
    <li>The value of each element in <code>nums</code> will be in the range <code>[-9999, 9999]</code>.</li>
</ol>

## Solutions

<!-- tabs:start -->

### **Python3**

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        low, high = 0, len(nums) - 1
        while low <= high:
            mid = (low + high) >> 1
            if nums[mid] == target:
                return mid
            if nums[mid] < target:
                low = mid + 1
            else:
                high = mid - 1
        return -1
```

### **Java**

```java
class Solution {
    public int search(int[] nums, int target) {
        int low = 0, high = nums.length - 1;
        while (low <= high) {
            int mid = (low + high) >>> 1;
            if (nums[mid] == target) {
                return mid;
            }
            if (nums[mid] < target) {
                low = mid + 1;
            } else {
                high = mid - 1;
            }
        }
        return -1;
    }
}
```

### **...**

```

```

<!-- tabs:end -->
