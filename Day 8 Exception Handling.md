


# 🔸 1. Exception Handling

**Exception Handling** is a mechanism to handle runtime errors so that normal flow of the program can be maintained.

Java handles exceptions using:

```java
try {
    // code that may throw an exception
} catch (ExceptionType e) {
    // code to handle the exception
} finally {
    // (optional) code that always executes
}
```

---

# 🔹 2. Types of Exceptions in Java

## ➤ A. **Checked Exceptions** (Compile-Time)

* **Checked by the compiler**.
* Must be **declared** with `throws` or **handled** with `try-catch`.
* Occurs during file handling, database access, etc.


 
---

### ✅ **Checked Exceptions Examples**

| **Exception Name**             | **When It Occurs**                                           | **Handled Using**       |
| ------------------------------ | ------------------------------------------------------------ | ----------------------- |
| `FileNotFoundException`        | Trying to open a file that does not exist                    | `try-catch` or `throws` |
| `IOException`                  | Input/output operation failure (file read/write/network)     | `try-catch` or `throws` |
| `SQLException`                 | Database access or connection error                          | `try-catch` or `throws` |
| `ParseException`               | Failure while parsing strings (like date format errors)      | `try-catch` or `throws` |
| `ClassNotFoundException`       | Trying to load a class that does not exist at runtime        | `try-catch` or `throws` |
| `InterruptedException`         | When a thread is interrupted during sleep or wait            | `try-catch` or `throws` |
| `InstantiationException`       | Trying to create an object of an abstract class or interface | `try-catch` or `throws` |
| `CloneNotSupportedException`   | When object cloning is not allowed                           | `try-catch` or `throws` |
| `NoSuchMethodException`        | When a method does not exist via reflection                  | `try-catch` or `throws` |
| `UnsupportedEncodingException` | Invalid character encoding used in input/output operations   | `try-catch` or `throws` |

---


#### ✅ Example: Checked Exception

```java
import java.io.*;

public class CheckedExample {
    public static void main(String[] args) {
        try {
            FileReader file = new FileReader("test.txt");
        } catch (FileNotFoundException e) {
            System.out.println("Checked Exception: File not found.");
        }
    }
}
```

Here, `FileNotFoundException` is a **checked exception**. The compiler forces you to handle it.

---

## ➤ B. **Unchecked Exceptions** (Runtime)

* **Not checked by the compiler**.
* Occurs due to **programming mistakes** (e.g. divide by zero, null access).
* Belong to the `RuntimeException` class.



---

### ❌ **Unchecked Exceptions Examples**

| **Exception Name**                | **When It Occurs**                                    | **Common Cause / Example**             |
| --------------------------------- | ----------------------------------------------------- | -------------------------------------- |
| `ArithmeticException`             | Performing illegal math operations                    | Division by zero: `int x = 5 / 0;`     |
| `NullPointerException`            | Accessing a method or field of a null object          | `String s = null; s.length();`                     |
| `ArrayIndexOutOfBoundsException`  | Accessing array with invalid index                    | `int[] arr = {1}; arr[5];`                         |
| `StringIndexOutOfBoundsException` | Accessing invalid index in a string                   | `"abc".charAt(5);`                                 |
| `NumberFormatException`           | Converting string to number and string is invalid     | `Integer.parseInt("abc");`                         |
| `IllegalArgumentException`        | Passing illegal or inappropriate argument to a method | `Thread.sleep(-100);`                              |
| `ClassCastException`              | Invalid type casting at runtime                       | `Object x = new Integer(5); String s = (String)x;` |
| `IllegalStateException`           | Method called at wrong time or in wrong state         | Using iterator after collection modified           |
| `UnsupportedOperationException`   | Attempting an unsupported operation                   | Removing item from unmodifiable list               |
| `NegativeArraySizeException`      | Creating an array with negative size                  | `int[] arr = new int[-5];`                         |

---



### ✅ Example: Unchecked Exception

```java
public class UncheckedExample {
    public static void main(String[] args) {
        try {
            int[] numbers = {1, 2, 3};
            System.out.println(numbers[5]);  // Invalid index
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Unchecked Exception: " + e);
        }
    }
}
```

Here, `ArrayIndexOutOfBoundsException` is an **unchecked exception** and does **not need to be caught**, but we can handle it for safety.

---

## 🔁 3. Difference Between Checked and Unchecked Exceptions

| Feature                     | Checked Exception                      | Unchecked Exception                           |
| --------------------------- | -------------------------------------- | --------------------------------------------- |
| Checked at compile time     | ✅ Yes                                  | ❌ No                                          |
| Inherits from               | `Exception` (but not RuntimeException) | `RuntimeException`                            |
| Must be handled or declared | ✅ Yes                                  | ❌ No (optional)                               |
| Example                     | `IOException`, `SQLException`          | `NullPointerException`, `ArithmeticException` |

---

### 🛠 4. Optional: `finally` Block

The `finally` block is always executed whether an exception is thrown or not.

```java
try {
    int result = 10 / 0;
} catch (ArithmeticException e) {
    System.out.println("Handled ArithmeticException.");
} finally {
    System.out.println("Finally block always runs.");
}
```

---


