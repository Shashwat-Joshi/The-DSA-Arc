# Question: [Second Largest Element in an Array without sorting](https://takeuforward.org/data-structure/find-second-smallest-and-second-largest-element-in-an-array/)


Given an array **arr**, return the **second largest** distinct element from an array. If the second largest element doesn't exist then return **-1**.

**Example 1:**
> **Input:** arr = [12,35,1,10,34,1]  
**Output:** 34  
**Explanation:** The largest element of the array is 35 and the second largest element is 34.


**Example 2:**
> **Input:** arr = [10, 10]  
**Output:** -1  
**Explanation:** The largest element of the array is 10 and the second largest element does not exist so answer is -1.


  
**Constraints:**


- `2 ≤ arr.size() ≤ 10^5`
- `1 ≤ arr[i] ≤ 10^5`


----

## Solution:

#### Brute Force: 


**Intution** - Sort array and traverse from the end of array look for first non duplicate entry than end element. Voila!

```java
class Solution {
    public int print2largest(List<Integer> arr) {
        // Code Here
        Collections.sort(arr);
        
        int idx = arr.size() - 1;
        while(idx > 0) {
            int last = arr.get(idx);
            int secondLast = arr.get(idx - 1);
            if(last != secondLast) return secondLast;
            idx--;
        }
        
        return -1;
    }
}
```

> TC - O(nlogn) | SC - O(1)

<br>

#### Optimal Approach: 


**Intution** - Maintain two variables max and secondmax and iterate through the array. If we find any number greater than max we update max and seconMax. Second case is that the current number is not greater than max but can be greater than secondMax so we handle that as well.

```java
class Solution {
    public int print2largest(List<Integer> arr) {
        // Code Here
        int max = arr.get(0), secondMax = -1;
    
        for(int i = 1; i < arr.size(); i++) {
            int cur = arr.get(i);
            if(cur > max) {
                secondMax = max;
                max = cur;
            } else if(cur != max && cur > secondMax) {
                secondMax = cur;   
            }
        }
        
        return secondMax;
    }
}
```

> TC - O(n) | SC - O(1)

