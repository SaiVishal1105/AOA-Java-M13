
# EX 3E Generate Permutations using Backtracking  Approach.
## DATE: 29-09-2025
## AIM:
To write a Java program to for given constraints.
Given an array nums of distinct integers, return all the possible Permutation. You can return the answer in any order.
Example 1:
Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
For example:
## Algorithm
1. Input: Array nums[] of integers. Initialize ans list to store permutations.

2. Backtracking: Start with an empty curr list representing the current permutation.

3. Base case: If curr.size() == nums.length, add a copy of curr to ans.

4. Recur: For each number in nums, if it’s not in curr, add it, recursively generate permutations, then remove it (backtrack).

5. Output: Return ans containing all possible permutations.
  
## Program:
```

Developed by: NISHA D
Register Number: 212223230143

import java.util.*;

public class Solution {

    public List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> ans = new ArrayList<>();
        backtrack(new ArrayList<>(), ans, nums);
        return ans;
    }

    public void backtrack(List<Integer> curr, List<List<Integer>> ans, int[] nums) {
        if (curr.size() == nums.length) {
            ans.add(new ArrayList<>(curr));
            return;
        }
        for (int num : nums) {
            if (curr.contains(num)) continue;
            curr.add(num);
            backtrack(curr, ans, nums);
            curr.remove(curr.size() - 1);
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String inputLine = scanner.nextLine().trim();
        inputLine = inputLine.replaceAll(".*\\[|\\].*", ""); 
        String[] parts = inputLine.split(",");
        if (parts.length == 1 && parts[0].trim().isEmpty()) {
            System.out.println("[]");
            return;
        }

        int[] nums = new int[parts.length];
        for (int i = 0; i < parts.length; i++) {
            nums[i] = Integer.parseInt(parts[i].trim());
        }
        Solution solution = new Solution();
        List<List<Integer>> permutations = solution.permute(nums);
        System.out.println(permutations);
        scanner.close();
    }
}

```

## Output:

<img width="1237" height="173" alt="image" src="https://github.com/user-attachments/assets/6210996d-d327-4cec-ad56-11749e3c5e37" />



## Result:
The program successfully implemented and the expected output is verified.
