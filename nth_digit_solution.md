[Nth digit Problem](https://leetcode.com/problems/nth-digit/)
# Solution
## Overview
Natural numbers are split into chunks, due to the number of digits in number.
- 1 .. 9: have exactly 1 `digit`, `chunkSize` = 9
- 10 .. 99: have exactly 2 `digits`, `chunkSize` = 90
- 100 .. 999: have exactly 3 `digits`, `chunkSize` = 900
- and so on.
The digit we are searching for would be in one of those chunks.
![Numbers split into chunks](https://github.com/ava8katushka/leetcode/blob/main/digits_and_chunks.png)
### How many digits are in a chunk? 
This question is really easy to answer: `chunkSize` times `digits` capacity of the chunk.
![Digits passsed while travelling from chunk to chunk](https://github.com/ava8katushka/leetcode/blob/main/digits_passed.png)
## Approach 1: Search
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
