A contiguous subarray refers to a portion of an array that consists of consecutive elements without any gaps.  
For example, in the array [1, 2, 3, 4, 5], the subarrays [1, 2, 3], [2, 3, 4], and [3] are all contiguous because they consist of elements that appear consecutively in the original array.  

### Problem: Maximum Subarray Sum (Kadane's Algorithm)    
One common algorithm associated with contiguous subarrays is Kadane’s Algorithm,   
which solves the problem of finding the maximum sum of a contiguous subarray within a one-dimensional numeric array.

### Problem Statement:  
Given an array of integers, find the contiguous subarray (containing at least one number) that has the largest sum and return that sum.  

For example:  
```
Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
Explanation: The subarray [4,-1,2,1] has the largest sum = 6.
Algorithm Steps (Kadane's Algorithm):
Initialize two variables:
```
#### current_max: Stores the maximum sum of the current subarray.  
#### global_max: Stores the maximum sum encountered so far.  
Iterate through the array:  
> For each element in the array, decide whether to include it in the existing subarray (current_max + num) or to start a new subarray with just the current element (num).
Update global_max if current_max exceeds it.
Return the global_max at the end, which holds the maximum sum of any contiguous subarray.

### Kadane’s Algorithm in Python:
```
def max_subarray(nums):
    current_max = global_max = nums[0]  # Initialize with the first element

    for num in nums[1:]:  # Iterate from the second element onwards
        current_max = max(num, current_max + num)  # Decide to add current element or start new subarray
        global_max = max(global_max, current_max)  # Update global max if current_max is greater

    return global_max
```
#### Explanation of Contiguity:  
In Kadane’s Algorithm, the subarrays considered are contiguous because we either:

* Add the current element num to the existing subarray (current_max + num), which means extending the current subarray with consecutive elements.  
- Start a new subarray from the current element (num), ensuring that any new subarray is also contiguous from that point onward.  
#### Example Walkthrough:
For the input nums = [-2,1,-3,4,-1,2,1,-5,4]:  

Start with current_max = global_max = -2.  
#### Move to the next element 1:  
current_max = max(1, -2 + 1) = 1  
global_max = max(-2, 1) = 1  
#### Next element -3:  
current_max = max(-3, 1 + (-3)) = -2  
global_max = max(1, -2) = 1  
#### Next element 4:  
current_max = max(4, -2 + 4) = 4  
global_max = max(1, 4) = 4  
>Continue until the array ends, updating current_max and global_max at each step.

##### At the end, global_max = 6, which is the maximum sum of the contiguous subarray [4, -1, 2, 1].

#### Time Complexity:
O(n), where n is the number of elements in the array.  
The algorithm processes each element once.  
This algorithm efficiently solves the problem in linear time.  
