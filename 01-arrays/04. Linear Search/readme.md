# Question: [Linear Search](https://www.geeksforgeeks.org/problems/who-will-win-1587115621/1)


Given an array **arr[]** sorted in ascending order of size **N** and an integer **K**. Check if K is present in the array or not.

**Example 1:**
> **Input:** N = 5, K = 6  
arr[] = {1,2,3,4,6}  
**Output:** 1   
**Exlpanation:** Since, 6 is present in the array at index 4 (0-based indexing), output is 1.


**Example 2:**
> **Input:** N = 5, K = 2  
arr[] = {1,3,4,5,6}  
**Output:** -1   
**Exlpanation:** Since, 2 is not present in the array, output is -1.


  
**Constraints:**


- `1 <= N <= 10^6`
- `1 <= K <= 10^6`
- `1 <= arr[i] <= 106`


----

## Solution:


#### Brute Force: 


**Intution** - We do a linear search and check all elements

```java
class Solution{
    static int searchInSorted(int arr[], int N, int K)
    {
        // Your code here
        for(int ele : arr) {
            if(ele == K)
                return 1;
        }
        return -1;
    }
}
```

> TC - O(n) | SC - O(1)

<br>

#### Optimal Approach: 


**Intution** - As the array is sorted we can use binary search approach to finish the search in logarithmic time.

```java
class Solution{
    static int searchInSorted(int arr[], int N, int K)
    {
        // Your code here
        int low = 0, high = N - 1;
        while(low <= high) {
            int mid = (low + high) / 2;
            if(arr[mid] < K) low = mid + 1;
            else if(arr[mid] > K) high = mid - 1;
            else return 1;
        }
        
        return -1;
    }
}
```

> TC - O(logn) | SC - O(1)