
# EX 3C Tug of War problem - Backtracking.
## DATE: 22-09-2025
## AIM:
To write a Java program to for given constraints.
Given an integer array nums, return true if you can partition the array into two subsets such that the sum of the elements in both subsets is equal or false otherwise.
Example 1:
Input: Enter the number of elements: 4
Enter the elements of the array:
1 5 11 5
Output: true
Explanation: The array can be partitioned as [1, 5, 5] and [11].

Constraints:

1 <= nums.length <= 200
1 <= nums[i] <= 100

## Algorithm
1. Input: Array nums[] of integers.

2. Compute sum: If total sum is odd, return false; else, set target = sum / 2.

3. Initialize DP: Boolean array dp[target + 1], set dp[0] = true.

4. Populate DP: For each num in nums, update dp[j] = dp[j] || dp[j - num] for j from target down to num.

5. Output: Return dp[target] (true if a subset with sum = target exists).

## Program:
```
Developed by: SAI VISHAL D
Register Number: 212223230180


import java.util.Scanner;
public class Solution {
    public boolean canPartition(int[] nums) {
        int sum = 0;
        for (int num : nums) sum += num;
        if (sum % 2 != 0) return false;
        int target = sum / 2;
        boolean[] dp = new boolean[target + 1];
        dp[0] = true;
        for (int num : nums) {
            for (int j = target; j >= num; j--) {
                dp[j] = dp[j] || dp[j - num];
            }
        }
        return dp[target];
    }
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Solution sol = new Solution();
        int n = scanner.nextInt();
        int[] nums = new int[n];
        for (int i = 0; i < n; i++) {
            nums[i] = scanner.nextInt();
        }
        boolean canBePartitioned = sol.canPartition(nums);
        System.out.println(canBePartitioned);
        scanner.close();
    }
}
```

## Output:

<img width="435" height="241" alt="image" src="https://github.com/user-attachments/assets/c5bb751b-aeef-41be-aa3a-98cfef8e1873" />



## Result:
The program successfully implemented and the expected output is verified.
