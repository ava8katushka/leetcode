[Nth digit Problem](https://leetcode.com/problems/nth-digit/)
# Solution
## Overview
## Approach 1: Brute Force
### Intuition
### Algorithm
### Complexity Analysis
## Approach 2: Search
### Intuition
### Algorithm
### Code
```python
def findNthDigit(self, n):
        digits = 1
        digitsPassed = 0
        chunkStart = 1
        chunkSize = 9

        while n > digitsPassed + chunkSize * digits:
            digitsPassed += chunkSize * digits
            digits += 1
            chunkStart += chunkSize
            chunkSize *= 10

        index = (n - digitsPassed - 1) / digits
        digit = (n - digitsPassed - 1) % digits
        
        return str(chunkStart + index)[digit]
```
### Complexity Analysis
