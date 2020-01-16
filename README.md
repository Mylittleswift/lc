|  #  |                    Title                    |      Related Topics      |            Company           |
|-----|---------------------------------------------|--------------------------|------------------------------|
|  1  | [Two Sum](#1-two-sum)                       | Array, Hash Table        | Google,Facebook,Amazon,Apple |
|  2  | [Add Two Number](#2-add-two-numbers)        | Linked List, Math        | Google,Facebook,Amazon,Apple |
|  3  | [Longest Substring Without Repeating Characters](#3-longest-substring-without-repeating-characters)| Linked List, Math        | Google,Facebook,Amazon,Apple |





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

```swift
class Solution {
 func lengthOfLongestSubstring(_ s: String) -> Int {
     var right = 1
     var left = 0
     var i = 0
     var result = 0
     
     if s.count > 0 {
         result = right - left
         let chars = Array(s.utf8)
         
         //Interate in a incremental window 
         while right < chars.count {
             i = left
                while i < right {
                    //Check if a duplicate is found
                    if chars[i] == chars[right] {
                        left = i + 1
                        break
                    } 
                i = i + 1
             }
         result = max(result,right-left+1)     
         right = right + 1
     }
     }
     return result
     }
}
```


### 4. Median of Two Sorted Arrays
_Hard_

There are two sorted arrays nums1 and nums2 of size m and n respectively.

Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).

You may assume nums1 and nums2 cannot be both empty.

Example 1:
```
nums1 = [1, 3]
nums2 = [2]
The median is 2.0
```
Example 2:
```
nums1 = [1, 2]
nums2 = [3, 4]
The median is (2 + 3)/2 = 2.5
```

```swift
class Solution {
func findMedianSortedArrays(_ nums1: [Int], _ nums2: [Int]) -> Double {
    var i = 0, j = 0
    var m = nums1.count, n = nums2.count
    var arr1 = nums1, arr2 = nums2
    if m > n {
        swap(&m, &n)
        swap(&arr1, &arr2)
    }
    let half = (m + n) / 2

    var leftMax = 0, rightMin = 0
    
    // 长度为m的数组分割，有m+1种分割方法，所以 0 <= i <= m
    var min = 0, max = m
    while min <= max {
        i = (min + max) / 2
        j = half - i
        if i > 0 && arr1[i-1] > arr2[j] {
            max = i - 1
        } else if i < m && arr2[j-1] > arr1[i] {
            min = i + 1
        } else {
            // arr1 所有元素都在左边，则min(Right) = arr2[j]
            if i == m {
                rightMin = arr2[j]
            } else if j == n {
                rightMin = arr1[i]
            } else {
                rightMin = arr1[i] > arr2[j] ? arr2[j] : arr1[i]
            }
            
            if (m + n) % 2 == 1 {
                return Double(rightMin)
            }
            
            if i == 0 {
                leftMax = arr2[j - 1]
            } else if j == 0 {
                leftMax = arr1[i - 1]
            } else {
                leftMax = arr1[i-1] > arr2[j-1] ? arr1[i-1] : arr2[j-1]
            }
            return Double(leftMax + rightMin) / 2.0
        }
    }
    return 0
}
}
```
```swift
class Solution {
    func findMedianSortedArrays(_ nums1: [Int], _ nums2: [Int]) -> Double {
        let mergeArray = (nums1 + nums2).sorted()
        let isOdd = mergeArray.count % 2
        if isOdd != 0 {
            return Double(mergeArray[(mergeArray.count / 2)])
        } else {
            let medianRight = mergeArray.count / 2
            let medianLeft = medianRight - 1
            return Double(mergeArray[medianRight] + mergeArray[medianLeft]) / 2
        }
    }
}
```


