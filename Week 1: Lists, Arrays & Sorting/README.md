# Week 1: Lists, Arrays, and Sorting

Welcome to the first week of our LeetCode Bootcamp. This week, we will dive into Lists, Arrays, and Sorting in Python, alongside introducing powerful problem-solving patterns like the Two-Pointer Approach and the Sliding Window Technique.

## Class Agenda (2 Hours)

### 1. Overview of the Bootcamp Syllabus

- Introduction to the course structure
- Objectives and outcomes

### 2. Python Overview of Lists, Arrays, and Sorting

Please review the following resources:

- [Exercism: Python Lists](https://exercism.org/tracks/python/concepts/lists)
- [Python.org: List Comprehensions](https://docs.python.org/3/tutorial/datastructures.html#list-comprehensions)
- [Python.org: Sequence Types - list, tuple, range](https://docs.python.org/3/library/stdtypes.html#sequence-types-list-tuple-range)
- [Python.org: Sorting HOW TO](https://docs.python.org/3/howto/sorting.html#)
- [Real Python: Python Lists and Tuples](https://realpython.com/python-lists-tuples/) 

### 3. Pattern Introduction

- Two-Pointer Approach
![alt text](./TwoPointerApproach.png)
- Sliding Window Technique
![alt text](./SlidingWindowApproach.png)


### 4. Problems Covered This Week

- [Merge Intervals](https://leetcode.com/problems/merge-intervals/description/)

#### Brute Force Approach

A simple approach is to start from the first interval and compare it with all other intervals for overlapping, if it overlaps with any other interval, then remove the other interval from the list and merge the other into the first interval. Repeat the same steps for the remaining intervals after the first.

Time Complexity: O(n^2)

```python
# Optimized Solution 
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:   
        merged = []
        #  Sort the intervals based on their start times
        intervals.sort(key=lambda x: x[0])
        prev = intervals[0]
        for interval in intervals[1:]:
            #If the start time of current interval <=  end time of the prev interval
            if interval[0] <= prev[1]:
                prev[1] = max(prev[1], interval[1])
            else:
                #Intervals don't overlap, add the prev interval to the merged list
                merged.append(prev)
                prev = interval
        #Adding the Last Interval
        merged.append(prev)
        return merged

# Time Complexity: O(nlogn)
```

- [Best time to buy and sell stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

```python

# Brute Force Approach
  def maxProfit(self, prices: List[int]) -> int:
      max_profit = 0
      n = len(prices)
      for i in range(n):
          for j in range(i+1, n):
              profit = prices[j] - prices[i]
              if profit > max_profit:
                  max_profit = profit
      return max_profit

# Time Complexity: O(n^2)

# Two Pointer Approach
    def maxProfit(self, prices: List[int]) -> int:
        left = 0 #Buy
        right = 1 #Sell
        max_profit = 0
        while right < len(prices):
            currentProfit = prices[right] - prices[left] #our current Profit
            #price[left] < price[right] which means we will get profit  
            if prices[left] < prices[right]:
                max_profit = max(currentProfit,max_profit)
            else:
                #Price[left] > price[right] so we will move left pointer to the right 
                left = right
            right += 1
        return max_profit

# Time Complexity: O(n)
```

- [Container With Most Water](https://leetcode.com/problems/container-with-most-water/)

```python

# Brute Force Approach
  def maxArea(self, height: List[int]) -> int:
      area = 0
      for i in range(len(height)):
          for j in range(i + 1, len(height)):
              # Calculating the max area
              area = max(area, min(height[j], height[i]) * (j - i))
      return area

# Time Complexity: O(n^2)

# Optimized Solution 
    def maxArea(self, height: List[int]) -> int:
        max_area = 0
        left = 0
        right = len(height) - 1

        while left < right: 
            max_area = max(max_area, (right - left) * min(height[left], height[right]))
            # Multiple width of the container and minimum of the heights of the two lines.
            if height[left] < height[right]:
                left += 1
            else:
                right -= 1
        return max_area

  # Time Complexity: O(n)
```

- [Maximum Product Subarray](https://leetcode.com/problems/maximum-product-subarray/description/)

```python

#Brute Force Approach
  def maxProduct(self, arr):
    n = len(arr)
    result = arr[0]
    for i in range(n):
        mul = 1    
        for j in range(i, n):
            mul *= arr[j]
            result = max(result, mul)       
    return result

# Time Complexity: O(n^2)

# Optimized Solution
    def maxProduct(self, arr):
      n = len(arr)  # size of array
      pre = 1
      suff = 1
      ans = float('-inf')     
      for i in range(n):
          if pre == 0:
              pre = 1
          if suff == 0:
              suff = 1
          
          pre *= arr[i]
          suff *= arr[n - i - 1]
          ans = max(ans, pre, suff)        
      return ans

  # Time Complexity: O(n)

```

### 5. Homework Problems 

- [Two Sum II - Input Array Is Sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/)
- [Products of array discluding self](https://leetcode.com/problems/product-of-array-except-self/description/)
- [Sort Colors](https://leetcode.com/problems/sort-colors/description/)

