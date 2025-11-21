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
	

```

  
## Why it works:

## Mistakes or Traps:

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

  

