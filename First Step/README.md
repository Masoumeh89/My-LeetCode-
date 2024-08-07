# A place for my LeetCode Challenges

This folder contains documentation related to the LeetCode Challenges

## Contents

- [Running Sum of 1D Array](#running-sum-of-1d-array)
- [Richest Customer Wealth](#richest-customer-wealth)
- [Fizz Buzz](#fizz-buzz)
- [Middle of The Linked List](#middle-of-the-linked-list)
- [Ransom Note](#ransom-note)





## Running Sum of 1D Array

Given an array nums. We define a running sum of an array as runningSum[i] = sum(nums[0]…nums[i]).

Return the running sum of nums.

```python
class Solution:
    def runningSum(self, nums: List[int]) -> List[int]:
        for i in range(1,len(nums)):
            nums[i] = nums[i-1]+nums[i]
        return nums
```

### Example:

Input: nums = [1,2,3,4]
Output: [1,3,6,10]
Explanation: Running sum is obtained as follows: [1, 1+2, 1+2+3, 1+2+3+4].


------------------------------
## Richest Customer Wealth


You are given an m x n integer grid accounts where accounts[i][j] is the amount of money the i​​​​​​​​​​​th​​​​ customer has in the j​​​​​​​​​​​th​​​​ bank. Return the wealth that the richest customer has.

A customer's wealth is the amount of money they have in all their bank accounts. The richest customer is the customer that has the maximum wealth.''

```python
class Solution:
    def maximumWealth(self, accounts: List[List[int]]) -> int:
        max_wealth = 0
        for i in range(len(accounts)):
            total_wealth = sum(accounts[i])
            max_wealth = max(max_wealth, total_wealth)
        return max_wealth
```

### Example:

Input: accounts = [[1,2,3],[3,2,1]]
Output: 6
Explanation:
1st customer has wealth = 1 + 2 + 3 = 6
2nd customer has wealth = 3 + 2 + 1 = 6
Both customers are considered the richest with a wealth of 6 each, so return 6.


-----------------------------------


## Fizz Buzz

Given an integer n, return a string array answer (1-indexed) where:

answer[i] == "FizzBuzz" if i is divisible by 3 and 5.
answer[i] == "Fizz" if i is divisible by 3.
answer[i] == "Buzz" if i is divisible by 5.
answer[i] == i (as a string) if none of the above conditions are true.

 ```python
class Solution:
    def fizzBuzz(self, n: int) -> List[str]:
        answer = [] # Initialize an empty list to store the results
    
         # Iterate from 1 to n (inclusive)
        for i in range(1,n+1): 
            # Check if the number is divisible by both 3 and 5
            if i%3==0 and i%5==0:
                answer.append("FizzBuzz")       
            # Check if the number is divisible by 3
            elif i%3==0:
                answer.append("Fizz")
            # Check if the number is divisible by 5
            elif i%5==0:
                answer.append("Buzz")
            # If none of the above conditions are true, add number as str     
            else:
                answer.append(str(i))
        return answer
 ```


### Example:

Input: n = 3
Output: ["1","2","Fizz"]

-----------------------------------------------
## Middle of The Linked List

Given the head of a singly linked list, return the middle node of the linked list.

If there are two middle nodes, return the second middle node.


```python

 # Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def middleNode(self, head: Optional[ListNode]) -> Optional[ListNode]:
        fast = head
        slow = head

        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next
        return slow
        
```

### Example:


Input: head = [1,2,3,4,5]
Output: [3,4,5]
Explanation: The middle node of the list is node 3.


-------------------------------------------------


## Ransom Note


Given two strings ransomNote and magazine, return true if ransomNote can be constructed by using the letters from magazine and false otherwise.

Each letter in magazine can only be used once in ransomNote.

```python
 class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        from collections import Counter

        ransom_counter = Counter(ransomNote)
        magazine_counter = Counter(magazine)

        for char, count in ransom_counter.items():
            if magazine_counter[char] < count:
                return False
        return True
 ```

### Example:

Input: ransomNote = "a", magazine = "b"
Output: false

