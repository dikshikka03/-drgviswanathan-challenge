# -drgviswanathan-challenge
## 🎥 Video Explanation

[Click here to watch the video](./pascal-triangle-video.mp4)

Submission for Pascal's Triangle II problem
# Pascal's Triangle II – Leetcode #119
## Problem Statement

Given an integer `rowIndex`, return the rowIndex<sup>th</sup> (0-indexed) row of Pascal’s Triangle.

In Pascal’s Triangle, each number is the sum of the two numbers directly above it.

---

## Examples

- Input: `rowIndex = 3` → Output: `[1, 3, 3, 1]`
- Input: `rowIndex = 0` → Output: `[1]`
- Input: `rowIndex = 1` → Output: `[1, 1]`

---

## Constraints

- `0 <= rowIndex <= 33`

---

## Approach

- We build each row of Pascal's Triangle based on the previous row.
- The 0<sup>th</sup> row is always `[1]`.
- Each element (except the ends) is the sum of the two elements directly above it.
- We use one list and **update it in place** from the end to the start to avoid overwriting values.

### Time and Space Complexity:
- **Time**: O(rowIndex²)
- **Space**: O(rowIndex)

---

## Java Code

```java
class Solution {
    public List<Integer> getRow(int rowIndex) {
        List<Integer> row = new ArrayList<>();
        row.add(1); // First element is always 1

        for (int i = 1; i <= rowIndex; i++) {
            for (int j = row.size() - 1; j > 0; j--) {
                row.set(j, row.get(j) + row.get(j - 1));
            }
            row.add(1); // Last element is always 1
        }

        return row;
    }
}
