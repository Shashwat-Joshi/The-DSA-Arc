# Question: [Check if Array Is Sorted and Rotated](https://leetcode.com/problems/check-if-array-is-sorted-and-rotated/)


Given an array `nums`, return `true` *if the array was originally sorted in non-decreasing order, then rotated **some**number of positions (including zero)*. Otherwise, return `false`.

There may be **duplicates** in the original array.

**Note:** An array `A` rotated by `x` positions results in an array `B` of the same length such that `A[i] == B[(i+x) % A.length]`, where `%` is the modulo operation.

**Example 1:**
> **Input:** nums = [3,4,5,1,2]  
**Output:** true  
**Explanation:** [1,2,3,4,5] is the original sorted array.  
You can rotate the array by x = 3 positions to begin on the the element of value 3: [3,4,5,1,2].


**Example 2:**
> **Input:** nums = [2,1,3,4]  
**Output:** false  
Explanation: There is no sorted array once rotated that can make nums.


**Example 3:**
> **Input:** nums = [1,2,3]  
**Output:** true  
**Explanation:** [1,2,3] is the original sorted array.  
You can rotate the array by x = 0 positions (i.e. no rotation) to make nums.


  
**Constraints:**

- `1 <= nums.length <= 100`
- `1 <= nums[i] <= 100`

----

## Solution:

#### Brute Force: 


**Intution** - We will traverse the array one element at a time. If we find a sharp decrease in the graph, then we find our breakpoint or peak. Then we will check the remaining array after peak. It should be strictly increasing and each element should be less than the first element. If not, return false otherwise return true.

```java
class Solution {
    public boolean check(int[] nums) {
        int size = nums.length;
        boolean bp = false;
        
        // Finding first breakpoint
        int idx;
        for(idx = 0; idx < size - 1; idx++) {
            if(nums[idx] > nums[idx + 1]) {
                bp = true;
                break;
            }
        }

        // Setting idx to new peak start
        for(int i = idx + 1;i < size; i++) {
            if(i != idx + 1 && nums[i - 1] > nums[i]) return false;
            if(nums[i] > nums[0]) return false;
        }

        // All checks done so we return true
        return true;
    }
}
```

> TC - O(n) | SC - O(1)

<br>

#### Optimal Approach: 


**Intution** -Find total number of peeks and check if it is less than 2 anything more or equal to 2 signifies array is unsorted

NOTE: Remeber to check last element of array with first element to find one possible peak.

```java
class Solution {
    public boolean check(int[] nums) {
        int size = nums.length;
        int peaks = 0;

        for(int i = 0; i < size - 1; i++) {
            if(nums[i] > nums[i + 1]) peaks++;
        }
        
        if(nums[size - 1] > nums[0]) peaks++;

        return (peaks <= 1);
    }
}
```

> TC - O(n) | SC - O(1)

