# 🚀 Jump Game II (LeetCode 45)

## 📌 Problem Statement

You are given a **0-indexed array** `nums` where each element represents your maximum jump length from that position.

* You start at index `0`
* Each element `nums[i]` allows jumping to any index:

  `i + j` where `0 ≤ j ≤ nums[i]`

### 🎯 Goal

Return the **minimum number of jumps** required to reach the last index.

---

## 🧠 Approach (Greedy)

Instead of checking all paths (which is slow), we use a **greedy strategy**:

* Track the **farthest index** reachable
* Maintain the **current jump range**
* When you reach the end of the current range, you must take a jump

---

## ⚙️ Algorithm

1. Initialize:

   * `jumps = 0`
   * `end = 0`
   * `farthest = 0`

2. Loop through the array:

   * Update `farthest = max(farthest, i + nums[i])`
   * If `i == end`:

     * Increment `jumps`
     * Update `end = farthest`

---

## 💻 Code (C++)

```cpp
class Solution {
public:
    int jump(vector<int>& nums) {
        int jumps = 0;
        int end = 0;
        int farthest = 0;

        for (int i = 0; i < nums.size() - 1; i++) {
            farthest = max(farthest, i + nums[i]);

            if (i == end) {
                jumps++;
                end = farthest;
            }
        }

        return jumps;
    }
};
```

---

## 📊 Example

### Input:

```
nums = [2,3,1,1,4]
```

### Output:

```
2
```

### Explanation:

* Jump from index `0 → 1`
* Jump from index `1 → 4`

---

## ⏱ Complexity Analysis

* **Time Complexity:** `O(n)`
* **Space Complexity:** `O(1)`

---

## 🏷 Tags

* Greedy
* Array
* Dynamic Programming (conceptual alternative)

---

## ⭐ Key Insight

You don’t need to try every jump — always jump **within the best reachable range**.

---

## 📂 Repository Name Suggestion

```
jump-game-ii-greedy
```

---

## 🙌 Contribute

Feel free to fork this repo, improve the solution, or add explanations in other languages!
