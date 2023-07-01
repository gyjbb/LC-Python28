# LC-Python28
Greedy Algorithm 3


## 1005.Maximize Sum Of Array After K Negations, 134.Gas Station, 135.Candy

June 28, 2023  4h

Congratulations!\
This is the 28th day for leetcode python study. Today we will learn about the Greedy Algorithm!\
The challenges today are especially about sorting both  positive and negative numbers, the concept of net increase, and processing one side at each time and merging the results.


## 1005.Maximize Sum Of Array After K Negations
[sort the positive and negative numbers](https://www.geeksforgeeks.org/python-rearrange-positive-and-negative-elements/)\
Firstly we sort the given array based on the absolute values. If the number is negative, we change it to positive. If the k is still larger than 1 and is odd after changing all negative values, we change the smallest positive number to negative.
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
hard, be familiar with way 2.\
At each station, we know how much gas we can get, and how much it would cost to get to the next station. We want to know the net increase of gas. 
```python
class Solution:
    def canCompleteCircuit(self, gas: List[int], cost: List[int]) -> int:
        curSum = 0
        totalSum = 0
        start = 0

        for i in range(len(gas)):
            curSum  += gas[i] - cost[i]
            totalSum += gas[i] - cost[i]

            if curSum < 0:
                start  = i+1    #update the start station for returning the correct start
                curSum = 0      #reset curSum to 0 and start new counting
            
        if totalSum < 0:
            return -1
        return start
```


## 135.Candy
Deal with one side first, then deal with the other side. Don't process both sides together. 
```python
class Solution:
    def candy(self, ratings: List[int]) -> int:
        candyVec = [1] * len(ratings)

        #iterate from left to right
        for i in range(1, len(ratings)):
            if ratings[i] >  ratings[i-1]:
                candyVec[i] =  candyVec[i-1] + 1

        #iterate from right to left
        for i  in range(len(ratings)-2, -1, -1):
            if ratings[i] >  ratings[i+1]:
                candyVec[i] = max(candyVec[i], candyVec[i+1]+1)
        
        result = sum(candyVec)
        return result
```

