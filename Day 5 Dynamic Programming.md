

# 🔸 Dynamic Programming

**Dynamic Programming (DP)** is a technique to solve problems by breaking them into **overlapping subproblems** and solving each subproblem **only once**, storing the result for future use (memoization).

It’s often used in optimization problems (minimum, maximum, longest, etc).

---

## ✅ Example Problem: Fibonacci using Dynamic Programming

### Problem:

Find the `n`th Fibonacci number using **dynamic programming**.

### 🔹 DP Solution (Bottom-Up)

```java
public class FibonacciDP {
    // Dynamic Programming (Bottom-Up approach)
    public static int fibonacci(int n) {
        if (n <= 1)
            return n;

        int[] dp = new int[n + 1];
        dp[0] = 0;
        dp[1] = 1;

        // Build the solution from bottom up
        for (int i = 2; i <= n; i++) {
            dp[i] = dp[i - 1] + dp[i - 2];
        }

        return dp[n];
    }

    public static void main(String[] args) {
        int n = 10;
        System.out.println("Fibonacci of " + n + " is: " + fibonacci(n));
    }
}
```

---

## ✅ Output:

```
Fibonacci of 10 is: 55
```

---

## 🔹 DP with Memoization (Top-Down Approach)

```java
public class FibonacciMemo {
    static int[] memo;

    public static int fibonacci(int n) {
        memo = new int[n + 1];
        return fib(n);
    }

    public static int fib(int n) {
        if (n <= 1)
            return n;

        if (memo[n] != 0)
            return memo[n];

        memo[n] = fib(n - 1) + fib(n - 2);
        return memo[n];
    }

    public static void main(String[] args) {
        int n = 10;
        System.out.println("Fibonacci of " + n + " is: " + fibonacci(n));
    }
}
```

---
