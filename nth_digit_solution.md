[Nth digit Problem](https://leetcode.com/problems/nth-digit/)
# Solution
## Overview
Natural numbers are split into chunks, due to the number of digits in number.
- 1 .. 9: have exactly 1 `digit`, `chunkSize` = 9
- 10 .. 99: have exactly 2 `digits`, `chunkSize` = 90
- 100 .. 999: have exactly 3 `digits`, `chunkSize` = 900
- and so on.


You can notice that the next chunk has exactly `1` more `digit` than the last, and the `chunkSize` increases by `10`.
The digit we are searching for is located in one of those chunks.
![Numbers split into chunks](https://github.com/ava8katushka/leetcode/blob/main/digits_and_chunks.png)
### How many digits are in a chunk? 
This question is really easy to answer: `chunkSize` times `digits` capacity of the chunk.
![Digits passsed while travelling from chunk to chunk](https://github.com/ava8katushka/leetcode/blob/main/digits_passed.png)
## Approach 1: Search
### Intuition
Let's travel from one chunk to the next, until we get to the chunk where the `digit with number n` is located. 
### Algorithm
1. Start with the first chunk
2. Iterate to the next chunk if the `digit with number n` is not in this chunk
3. When we arrive, find the `number` to which the `digit with number n` belongs to
4. Calculate the `position` of the `digit with number n` in this `number`
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

        number = chunkStart + (n - digitsPassed - 1) / digits
        position = (n - digitsPassed - 1) % digits
        
        return str(number)[position]
```
### Complexity Analysis
- Time complexity: **O(log<sub>10</sub>n)**.

The `digit with number n` > `number` it belongs to. How many digits `number` has? **log<sub>10</sub>n** digits. Algorithm iterates through the chunks until the number of digits in the chunk == number of digits in the `number`.


- Space complexity: **O(log<sub>10</sub>n)**.

Algorithm uses the most space when it converts the number to a string. You can reduce space complexity to **O(1)** by extracting the `digit with number n` from the `number` mathematically. 
