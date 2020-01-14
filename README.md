|  #  |                    Title                    |      Related Topics      |            Company           |
|-----|---------------------------------------------|--------------------------|------------------------------|
|  1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
|  2  | [Add Two Number](#2-add-two-numbers)        | Linked List, Math        | Google,Facebook,Amazon,Apple |
|  3  | [Longest Substring Without Repeating Characters](#3-longest-substring-without-repeating-characters)| Linked List, Math        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
| 1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |




### 1. Two Sum
_Easy_

Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

Example:
```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```
```swift
class Solution {
    func twoSum(_ nums: [Int], _ target: Int) -> [Int] {
        var result: [Int] = []
        var dict:[Int: Int] = [:]     
        for (index,num) in nums.enumerated() {
            if let sum = dict[target - num] {
                result.append(index)
                result.append(sum)
            } 
            dict[num] = index
        }
        return result
    }
}
```

### 2. Add Two Numbers
_Medium_

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

Example:
```
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
Explanation: 342 + 465 = 807.
```

```swift
class Solution {
    func addTwoNumbers(_ l1: ListNode?, _ l2: ListNode?) -> ListNode? {
        var c1: ListNode? = l1
        var c2: ListNode? = l2
        if c1 == nil {
            return c2
        }
        
        if c2 == nil {
            return c1
        }
        
        var helper = ListNode(0)
        var dummy: ListNode? = helper
        var sum = 0
        
        while c1 != nil || c2 != nil {
            sum /= 10
            if c1 != nil {
                sum += c1!.val
                c1 = c1!.next
            }
            if c2 != nil {
                sum += c2!.val
                c2 = c2!.next
            }
            dummy!.next = ListNode(sum % 10)
            dummy = dummy!.next

        }
        
        if sum / 10 == 1 {
            dummy!.next = ListNode(1)
        }
        
        return helper.next
    }
}
```

### 3. Longest Substring Without Repeating Characters
_Medium_

Given a string, find the length of the longest substring without repeating characters.

Example 1:
```
Input: "abcabcbb"
Output: 3 
Explanation: The answer is "abc", with the length of 3. 
```
Example 2:
```
Input: "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```
Example 3:
```
Input: "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3. 
             Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
```


          
