# LC-Python28
Greedy Algorithm 3


## 

June 28, 2023  4h

Congratulations!\
This is the 28th day for leetcode python study. Today we will learn about the Greedy Algorithm!\
The challenges today are especially about ~~the two jump games~~

## 1005.Maximize Sum Of Array After K Negations
[sort the positive and negative numbers](https://www.geeksforgeeks.org/python-rearrange-positive-and-negative-elements/)\
Fristly we sort the given array based on the absolute values. If the number is negative, we change it to positive. If the k is still larger than 1 and is odd after changing all negative values, we change the smallest positive number to negative.
```python 
class Solution:
    def largestSumAfterKNegations(self, nums: List[int], k: int) -> int:
        nums.sort(key=lambda x: abs(x), reverse=True)  # Step1: sort the given array according to the absolute values from largest to smallest

        for i in range(len(nums)):  # step2: cahnge all negative values to posiitive for at most k times
            if nums[i] < 0 and k > 0:
                nums[i] *= -1
                k -= 1

        if k % 2 == 1:  # step3: if k is still larger than 1 and is odd, change the smallest positive number to negative
            nums[-1] *= -1

        result = sum(nums)  # step4: calculate the sum of new array
        return result
```


## 134.Gas Station
hard, be familiar with way 2.



## 135. 
分发糖果 本题涉及到一个思想，就是想处理好一边再处理另一边，不要两边想着一起兼顾，后面还会有题目用到这个思路 





