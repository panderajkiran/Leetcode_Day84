# Leetcode_Day84
# Day 84: Majority Element

**LeetCode Problem:** 169. Majority Element  
**Difficulty:** Easy  
**Language:** Java  
**Topics:** Arrays, HashMap, Counting

## Problem Description

Given an integer array `nums` of size `n`, find the majority element.

The majority element is the element that appears **more than `n / 2` times** in the array.

You can assume that the majority element always exists.

## Approach

### 1. Create a HashMap

Use a `HashMap` to store each number and its frequency.

- The key represents an array element.
- The value represents how many times that element appears.

### 2. Count the Frequency

Traverse the array and update each element's frequency using `getOrDefault()`.

```java
map.put(num, map.getOrDefault(num, 0) + 1);
```

This increases the count if the element already exists or starts its count at `1`.

### 3. Find the Majority Element

Traverse the HashMap entries.

If an element's frequency is greater than `n / 2`, return that element.

Since the problem guarantees that a majority element exists, the answer will always be found.

## Java Solution

```java
import java.util.HashMap;

class Solution {
    public int majorityElement(int[] nums) {
        HashMap<Integer, Integer> map = new HashMap<>();

        for (int num : nums) {
            map.put(num, map.getOrDefault(num, 0) + 1);
        }

        for (int key : map.keySet()) {
            if (map.get(key) > nums.length / 2) {
                return key;
            }
        }

        return -1;
    }
}
```

## Example

**Input:**
```text
nums = [2, 2, 1, 1, 1, 2, 2]
```

**Output:**
```text
2
```

**Explanation:**

The array contains 7 elements, so the majority element must appear more than `7 / 2 = 3` times.

- Element `1` appears 3 times.
- Element `2` appears 4 times.

Therefore, `2` is the majority element.

## Complexity Analysis

Let `n` be the length of the array.

**Time Complexity:** `O(n)`

- Counting frequencies takes `O(n)` time.
- Finding the majority element takes `O(n)` time in the worst case.

**Space Complexity:** `O(n)`

The HashMap may store up to `n` distinct elements.

## What I Learned

- How to use a HashMap to count element frequencies.
- How `getOrDefault()` simplifies frequency counting.
- How to identify a majority element using a frequency threshold.
- How HashMaps help solve array problems efficiently.

## Takeaway

**Sometimes, finding the answer becomes easier when we stop looking at individual elements and start looking at patterns in their frequency.**

Day 84 complete! Another problem solved, another concept learned, and another step forward in my DSA journey.
