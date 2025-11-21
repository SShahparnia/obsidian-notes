# Contains Duplicate

## Key Idea: 

- return true if we have duplicate values in our integer array (hash map)
- We could use brute force
- brute force comparisons + sorted list
- hashmap (set)
## Steps to Solve: Hash set implementation 

1. We create our hash set
2. We check each value in our array nums
3. We check if they’re in our hashset already
4. We return True if they are
5. If not True, we add them to the hashset 
6. Return false if we find that we have no duplicates when trying to add to our hashset
## Code:
```python
Class Solution:
	def hasDuplicate(self, nums: List[int]) -> bool:
		hashset = set()
		for i in nums:
			if i in hashset:
				return True
			hashset.add(i)
		return False

```
## Why it works:

Brute force, even with a sorted list, is too primitive. The space complexity for them is good as we are directly accessing the original array, howevever, using a hashset we can maximize both the time and space complexity at O(n). this works by iterating through the original array nums[], adding each value to the hashset, then seeing if there is another of same in the hashset again after each iteration.

## Mistakes or Traps:

- one mistake i made at first was improper syntax (nested for loops because I didn't take my time and think through what the logic of my code was actually doing).
	- having a second nested for loop instead of the conditional results in updated the variable i instead of performing a comparison with the hashset

## Complexity:

### We could use brute force 
- Time: O(n^2)
- Space: O(1)
### brute force comparisons + sorted list
- Time: O(n log n)
- Space: O(1)
### hashmap (set)
- Time: O(n)
- Space: O(n)
# Valid Anagram

## Key Idea: 

- return true if count(char) in string s = string t
- otherwise false
## Steps to Solve: HashMap implementation 
1. Check if strings are the same length
	1. if they're not we automatically return false
2. define our hashmaps for strings 's' and 't'
3. loop through each index in s
4. look at s[i], if exists in countS then + 1
5. same idea for string t countT + 1
6. return countS == countT (compare the two hashmaps)
## Code:

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False

        countS, countT = {}, {}

        for i in range(len(s)):
            countS[s[i]] = 1 + countS.get(s[i], 0)
            countT[t[i]] = 1 + countT.get(t[i], 0)
        return countS == countT
	
```
## Why it works:
1. if the lengths differ, they can't be anagrams which returns false immediately (base case)
2. two empty dictionaries are created to store the counts for each string (hash map)
3. The loop runs through each index in the string and for each char:
	1. countS adds one to the count of s[i]
	2. countT adds one to the count of t[i]
	3. using get(char, 0) ensures missing char start at 0
4. after loop each dictionary contains exact num of occurrence for each char in strings s,t
5. if the 2 dict countS == countT, anagram
## Mistakes or Traps:
1. assuming same length is enough
2. not having length check then using range(len(s)) which assumes s and t are same length
3. case sensitivity not enforced
4. inefficient for large strings

## Complexity:
- Time complexity:
	- O(n + m)
- Space complexity:
	- O(1)
		- for typical anagram problems, the complexity is O(1) as we have the fixed alphabet
		- for problems where we have many unique characters in the string the worst case is O(k)




  

