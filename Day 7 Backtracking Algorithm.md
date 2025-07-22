

# 🔸 Backtracking

**Backtracking** is a general algorithmic technique used to solve **constraint satisfaction problems** by:

1. Trying all possible solutions step by step.
2. Abandoning (backtracking) a path as soon as it’s clear that it won't lead to a valid solution.
3. Going back ("undo") and trying another path.

---



### 🔹 Key Concepts

* **Recursive** solution building
* **Try → Fail → Backtrack**
* Often used in:

  * Combinatorics (like permutations)
  * Puzzles (like Sudoku)
  * Games (like N-Queens, Knights Tour)
  * Optimization problems (like subset sum)

---

### ✅ Common Structure of Backtracking

```java
boolean backtrack(parameters) {
    if (solution found) {
        return true;
    }

    for (possible options) {
        if (option is valid) {
            choose the option;
            if (backtrack(new state)) {
                return true;
            }
            undo the choice; // backtrack
        }
    }

    return false;
}
```

---

### 🔸 Example: Backtracking to Find All Subsets (Power Set)

```java
import java.util.*;

public class SubsetBacktracking {
    public static void main(String[] args) {
        int[] nums = {1, 2, 3};
        List<List<Integer>> result = new ArrayList<>();
        backtrack(nums, 0, new ArrayList<>(), result);

        System.out.println("All subsets:");
        for (List<Integer> subset : result) {
            System.out.println(subset);
        }
    }

    static void backtrack(int[] nums, int start, List<Integer> current, List<List<Integer>> result) {
        result.add(new ArrayList<>(current)); // add copy of current subset

        for (int i = start; i < nums.length; i++) {
            current.add(nums[i]);              // choose
            backtrack(nums, i + 1, current, result); // explore
            current.remove(current.size() - 1); // un-choose (backtrack)
        }
    }
}
```

---

### 📌 Output:

```
All subsets:
[]
[1]
[1, 2]
[1, 2, 3]
[1, 3]
[2]
[2, 3]
[3]
```

---

---

# 👑 N-Queens Problem

### ❓ Problem Statement:

Place **N queens** on an **N×N chessboard** such that **no two queens attack each other**.

### ✅ Rules:

* Only **one queen per row**.
* No two queens can be on the **same column**, **same row**, or **same diagonal**.

---

### 🧠 Backtracking Approach:

1. Place a queen row by row.
2. For each row, try placing a queen in every column.
3. Check if it’s **safe** (no attacks).
4. If safe → move to the next row.
5. If not safe or stuck → **backtrack**.

---

### ✅ Java Code: N-Queens Solver

```java
import java.util.*;

public class NQueens {

    public static void main(String[] args) {
        int N = 4;  // Try 8 for 8-queens
        NQueens solver = new NQueens();
        solver.solveNQueens(N);
    }

    // Main solver
    public void solveNQueens(int n) {
        char[][] board = new char[n][n];
        for (char[] row : board)
            Arrays.fill(row, '.'); // Fill with dots

        List<List<String>> solutions = new ArrayList<>();
        backtrack(board, 0, solutions);

        // Print solutions
        System.out.println("Total Solutions: " + solutions.size());
        for (List<String> sol : solutions) {
            for (String row : sol)
                System.out.println(row);
            System.out.println();
        }
    }

    // Recursive backtracking function
    private void backtrack(char[][] board, int row, List<List<String>> solutions) {
        int n = board.length;

        if (row == n) {
            solutions.add(construct(board));
            return;
        }

        for (int col = 0; col < n; col++) {
            if (isSafe(board, row, col)) {
                board[row][col] = 'Q';                // Place queen
                backtrack(board, row + 1, solutions); // Recurse
                board[row][col] = '.';                // Backtrack
            }
        }
    }

    // Check if placing queen is safe
    private boolean isSafe(char[][] board, int row, int col) {
        int n = board.length;

        // Check column
        for (int i = 0; i < row; i++)
            if (board[i][col] == 'Q')
                return false;

        // Check diagonal (top-left)
        for (int i = row - 1, j = col - 1; i >= 0 && j >= 0; i--, j--)
            if (board[i][j] == 'Q')
                return false;

        // Check diagonal (top-right)
        for (int i = row - 1, j = col + 1; i >= 0 && j < n; i--, j++)
            if (board[i][j] == 'Q')
                return false;

        return true;
    }

    // Convert board to List<String> format
    private List<String> construct(char[][] board) {
        List<String> result = new ArrayList<>();
        for (char[] row : board)
            result.add(new String(row));
        return result;
    }
}
```

---

### 🧪 Output for N = 4:

```
Total Solutions: 2
.Q..
...Q
Q...
..Q.

..Q.
Q...
...Q
.Q..
```

Each `Q` represents a queen. Each solution is a valid configuration.

---


---

# 🔁 Permutation

A **permutation** is an arrangement of all elements of a set in every possible order.

For example:

* Input: `[1, 2, 3]`
* Output:
  `[1,2,3]`
  `[1,3,2]`
  `[2,1,3]`
  `[2,3,1]`
  `[3,1,2]`
  `[3,2,1]`

---

### ✅ Java Code to Generate Permutations

We will use **backtracking** to generate all permutations of an integer array.

```java
import java.util.*;

public class Permutations {
    public static void main(String[] args) {
        int[] nums = {1, 2, 3};
        List<List<Integer>> result = new ArrayList<>();
        backtrack(nums, new ArrayList<>(), new boolean[nums.length], result);

        System.out.println("All permutations:");
        for (List<Integer> perm : result) {
            System.out.println(perm);
        }
    }

    // Backtracking function
    static void backtrack(int[] nums, List<Integer> current, boolean[] used, List<List<Integer>> result) {
        if (current.size() == nums.length) {
            result.add(new ArrayList<>(current));  // add a copy of current permutation
            return;
        }

        for (int i = 0; i < nums.length; i++) {
            if (used[i]) continue;  // skip already used numbers

            used[i] = true;                 // choose
            current.add(nums[i]);
            backtrack(nums, current, used, result); // explore
            current.remove(current.size() - 1);     // un-choose
            used[i] = false;              // mark as unused
        }
    }
}
```

---

### 📌 Output:

```
All permutations:
[1, 2, 3]
[1, 3, 2]
[2, 1, 3]
[2, 3, 1]
[3, 1, 2]
[3, 2, 1]
```

---




