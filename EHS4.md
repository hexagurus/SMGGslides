Perfect 👍
Let’s move to the next topic:

# 🎓 **Slide: Multiple Catch Clauses in Java**

This is a very important concept that helps handle **different types of exceptions** separately in a single `try` block.

---

## 🧩 **What Are Multiple Catch Clauses?**

### 📘 **Definition:**

> Multiple catch clauses allow you to write **different exception handlers** for **different exception types** that may occur within the same `try` block.

---

### 🧠 **Why & When We Use It:**

✅ When **a single block of code** can throw **multiple types** of exceptions.
✅ When **different actions** are required for each exception type.
✅ Helps make exception handling **more specific and readable**.

---

## ⚙️ **Syntax:**

```java
try {
    // code that may throw different exceptions
} catch (ExceptionType1 e1) {
    // handler 1
} catch (ExceptionType2 e2) {
    // handler 2
} catch (ExceptionType3 e3) {
    // handler 3
}
```

---

## 💡 **Basic Example — Separate Catch Blocks**

```java
public class MultipleCatchBasic {
    public static void main(String[] args) {
        try {
            int[] numbers = {10, 20, 30};
            int result = numbers[3] / 0;  // Two potential exceptions
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Array index issue: " + e);
        } catch (ArithmeticException e) {
            System.out.println("Arithmetic issue: " + e);
        }
        System.out.println("Program completed");
    }
}
```

### 🧾 **Output:**

```
Array index issue: java.lang.ArrayIndexOutOfBoundsException: Index 3 out of bounds for length 3
Program completed
```

🧠 **Explanation:**

* The `try` block has two risky operations.
* JVM checks **each catch block in order**.
* The first matching exception type is executed; others are skipped.

---

## 💡 **Medium Example — Catching Multiple Exceptions Together (Java 7+)**

Sometimes, you may want to **handle multiple exception types in the same way**.
Java 7 introduced **multi-catch** using the `|` (pipe) operator.

```java
public class MultipleCatchMedium {
    public static void main(String[] args) {
        try {
            String s = null;
            System.out.println(s.length());  // NullPointerException
        } catch (ArithmeticException | ArrayIndexOutOfBoundsException | NullPointerException e) {
            System.out.println("Handled exception: " + e);
        }
        System.out.println("Program continues normally");
    }
}
```

### 🧾 **Output:**

```
Handled exception: java.lang.NullPointerException
Program continues normally
```

🧠 **Explanation:**

* All three exception types share the same handling logic.
* You can combine related exception types using `|`.
* The variable `e` is **final** in a multi-catch — you can’t reassign it.

---

## ⚠️ **Common Rule:**

❌ You **cannot** catch a superclass before a subclass.
Otherwise, the subclass catch becomes unreachable code.

### 🚫 Wrong Example:

```java
try {
    int a = 5 / 0;
} catch (Exception e) {
    System.out.println("Generic exception");
} catch (ArithmeticException e) {  // ❌ Compile-time error
    System.out.println("Specific exception");
}
```

---

## 🧠 **Summary:**

| **Concept**           | **Description**                                  |                                       |
| --------------------- | ------------------------------------------------ | ------------------------------------- |
| **Multiple catch**    | Handling different exceptions separately         |                                       |
| **Order**             | Always catch from **specific → general**         |                                       |
| **Multi-catch (`      | `)**                                             | Handle multiple types with same block |
| **Unreachable catch** | Occurs when superclass is caught before subclass |                                       |

---

### ✅ **When to Use:**

* When one `try` block can throw **multiple exception types**
* When you want to **customize messages or recovery logic** per exception
* When maintaining **clean and readable** code structure

---

Would you like me to now **generate an image for this slide** (diagram showing one `try` with three `catch` blocks and exception flow arrows)?
