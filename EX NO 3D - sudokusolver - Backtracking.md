
# EX 3D Sudoku solver - Backtracking.
## DATE: 25-09-2025
## AIM:
To write a Java program to solve a Sudoku puzzle by filling the empty cells.

For example:

<img width="357" height="322" alt="image" src="https://github.com/user-attachments/assets/334b8c39-d547-4743-aca0-de92e38bdd1c" />



## Algorithm
1. Input: 9×9 Sudoku board with empty cells as 0.

2. Check safety: A number num can be placed at board[row][col] if it does not exist in the same row, column, or 3×3 subgrid.

3. Backtracking: Start from the first cell; if cell is empty, try numbers 1–9.

4. Recur: Place a number if safe, recursively solve the next cell; if it leads to no solution, reset the cell to 0 (backtrack).

5. Output: Print the completed board if solved; otherwise, indicate no solution exists.

## Program:
```
Developed by: SAI VISHAL D
Register Number: 212223230180

import java.util.Scanner;

public class SudokuSolver {

    static boolean isSafe(int[][] board, int row, int col, int num) {
        for (int i = 0; i < 9; i++) {
            if (board[row][i] == num || board[i][col] == num)
                return false;
        }

        int startRow = row - row % 3;
        int startCol = col - col % 3;

        for (int i = 0; i < 3; i++)
            for (int j = 0; j < 3; j++)
                if (board[startRow + i][startCol + j] == num)
                    return false;

        return true;
    }

    static boolean solveSudoku(int[][] board, int row, int col) {
        if (row == 9) return true;
        if (col == 9) return solveSudoku(board, row + 1, 0);
        if (board[row][col] != 0) return solveSudoku(board, row, col + 1);

        for (int num = 1; num <= 9; num++) {
            if (isSafe(board, row, col, num)) {
                board[row][col] = num;
                if (solveSudoku(board, row, col + 1)) return true;
                board[row][col] = 0;
            }
        }
        return false;
    }

    static void printBoard(int[][] board) {
        for (int[] row : board) {
            for (int val : row)
                System.out.print(val + " ");
            System.out.println();
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int[][] board = new int[9][9];

        for (int i = 0; i < 9; i++)
            for (int j = 0; j < 9; j++)
                board[i][j] = sc.nextInt();

        if (solveSudoku(board, 0, 0)) {
            System.out.println("Solved Sudoku:");
            printBoard(board);
        } else {
            System.out.println("No solution exists.");
        }

        sc.close();
    }
}
```

## Output:
<img width="705" height="646" alt="image" src="https://github.com/user-attachments/assets/42da650c-ea48-455b-9c67-32ab0696d9ea" />




## Result:
The program successfully implemented and the expected output is verified.
