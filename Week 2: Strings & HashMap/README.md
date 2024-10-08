# Week 2: Strings and HashMap

Welcome to the second week of our LeetCode Bootcamp. This week, we will dive into Strings and HashMap in Python, alongside introducing powerful problem-solving patterns like the Hash Map Pattern.

## Class Agenda (2 Hours)

### 1. Python Overview of Strings and HashMap

Please review the following resources:

- [Exercism: Strings](https://exercism.org/tracks/python/concepts/strings)
- [Python.org: String Methods](https://docs.python.org/3/library/stdtypes.html#string-methods)
- [Exercism: Sets](https://exercism.org/tracks/python/concepts/sets)
- [Exercism: Dicts](https://exercism.org/tracks/python/concepts/dicts)
- [Exercism: Dicts Methods](https://exercism.org/tracks/python/concepts/dict-methods)
- [Python.org: Mapping Types](https://docs.python.org/3/library/stdtypes.html#mapping-types-dict)
- [Python.org: Dictionaries](https://docs.python.org/3/tutorial/datastructures.html#dictionaries)

 ### 2. Pattern Introduction

- Hash Map Pattern
![alt text](./HashMap.png)

### 4. Problems Covered This Week

- [Valid Palindrome](https://leetcode.com/problems/valid-palindrome/description/)

```python
# Optimized Solution 
class Solution:
   def isPalindrome(self, s: str) -> bool:
       l = 0
       r = len(s) - 1
       while l <= r:
           if not s[l].isalnum():
               l += 1
           elif not s[r].isalnum():
               r -= 1
           elif s[l].lower() == s[r].lower():
               l += 1
               r -= 1
           else:
               return False
       return True
            

# Time Complexity: O(n)
```

- [Subdomain Visit Count](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

 ```python
 #Optimized Solution

 class Solution(object):
   def subdomainVisits(self, cpdomains):
       ans = collections.Counter()
       for domain in cpdomains:
           count, domain = domain.split()
           count = int(count)
           frags = domain.split('.')
           for i in range(len(frags)):
               ans[".".join(frags[i:])] += count

       formatted_list  = []
       for dom, ct in ans.items():
           formatted_string = "{} {}".format(ct, dom)
           formatted_list.append(formatted_string)

       return formatted_list

# Time Complexity: O(n)
 ```

- [Two sum](https://leetcode.com/problems/two-sum/description/)

 ```python
 #Optimized Solution

class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        hashmap = {}
        for i in range(len(nums)): 
            complement = target - nums[i]
            if complement in hashmap: 
                return [i, hashmap[complement]]
            hashmap[nums[i]] = i
    
        

# Time Complexity: O(n)
 ```

- [Longest Substring without repeating characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/)

 ```python
 #Optimized Solution

class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        seen = {}
        l = 0
        length = 0
        for r in range(len(s)): 
            char = s[r] 
            if char in seen and seen[char] >= l:
                l = seen[char] + 1
            else:
                length = max(length, r - l + 1) 
            seen[char] = r
        return length
        
        

# Time Complexity: O(n)
 ```


- [Group Anagrams](https://leetcode.com/problems/group-anagrams/description/)

 ```python
 #Optimized Solution
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        dic={}
        k=[]
        for i in strs:
            l="".join(sorted(i))
            dic.setdefault(l,[]).append(i)
      
        return dic.values()
        
# Time Complexity: O(n)
 ```

## Take-Home Problems

To help solidify your understanding and practice further, here are some take-home problems:

1. [String to integer atoi](https://leetcode.com/problems/string-to-integer-atoi/description/)
2. [Find all anagrams in a string](https://leetcode.com/problems/find-all-anagrams-in-a-string/description/)
3. [Reverse Words in a string](https://leetcode.com/problems/reverse-words-in-a-string/description/)
