# Question: [Largest Element in an Array](https://www.geeksforgeeks.org/problems/largest-element-in-array4009/0?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=largest-element-in-array) 


Given an array **arr**, the task is to find the largest element in it.

**Examples:**
> **Input:** arr= [1, 8, 7, 56, 90]
> **Output:** 90
> **Explanation:** The largest element of given array is 90.

> **Input:** arr = [5, 5, 5, 5]
> **Output:** 5
> **Explanation:** The largest element of given array is 5.

> **Input:** arr = [10]
> **Output:** 10
> **Explanation:** There is only one element which is the largest


**Expected Time Complexity:** O(n)
**Expected Auxiliary Space:** O(1)

**Constraints:**
1 <= arr.size()<= 10^5
0 <= arr[i] <= 10^5
arr may contain duplicate elements.

----

## Solution:


#### Brute Force: 


**Intution** - Sort array and return last element

```java
class Solution {
    public static int largest(int n, int[] arr) {
        // code here
        Arrays.sort(arr);
        return arr[n - 1];
    }
}
```

> TC - O(nlogn) | SC - O(1)

<br>

#### Optimal Approach: 

**Intution** - Pick first element as max, then iterate entire array and compare all elements while updating max.

```java
class Solution {
    public static int largest(int n, int[] arr) {
        // code here
        int max = arr[0];
        
        for(int ele : arr) {
            if(ele > max) max = ele;
        }
        
        return max;
    }
}

```

> TC - O(n) | SC - O(1)

