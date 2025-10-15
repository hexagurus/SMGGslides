Perfect 👏
Let’s now move to one of the **most important topics in Exception Handling**:

# 🎓 **Slide: Checked vs Unchecked Exceptions in Java**

---

## 🧩 **1️⃣ What Are Checked Exceptions?**

### 📘 **Definition:**

> Checked Exceptions are the exceptions that are **checked at compile-time**.
> The Java compiler forces you to **handle them** (either using `try-catch` or `throws`).

### 🧠 **Key Points:**

* Occur due to **external factors** (like user input, files, network).
* Must be handled using **try-catch** or declared using **throws**.
* Compiler gives an **error** if not handled.

### 💡 **Example: Checked Exception**

```java
class CheckedDemo {
    static void validate(int age) throws Exception {
        if (age < 18)
            throw new Exception("Not eligible to vote");
        else
            System.out.println("Eligible to vote");
    }

    public static void main(String[] args) {
        try {
            validate(15);
        } catch (Exception e) {
            System.out.println("Caught checked exception: " + e.getMessage());
        }
    }
}
```

### 🧾 **Output:**

```
Caught checked exception: Not eligible to vote
```

🧠 **Explanation:**
`Exception` is a **checked** type, so the compiler requires handling it with a `try-catch` or `throws`.

---

## 🧩 **2️⃣ What Are Unchecked Exceptions?**

### 📘 **Definition:**

> Unchecked Exceptions are the exceptions that occur **at runtime** and are **not checked by the compiler**.

### 🧠 **Key Points:**

* Occur due to **programming mistakes** (like division by zero, null access).
* Handling them is **optional**, not required by compiler.
* All unchecked exceptions are subclasses of **RuntimeException**.

### 💡 **Example: Unchecked Exception**

```java
public class UncheckedDemo {
    public static void main(String[] args) {
        int[] arr = {10, 20, 30};
        try {
            System.out.println(arr[5]);  // ArrayIndexOutOfBoundsException
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Caught unchecked exception: " + e);
        }
        System.out.println("Program continues...");
    }
}
```

### 🧾 **Output:**

```
Caught unchecked exception: java.lang.ArrayIndexOutOfBoundsException: Index 5 out of bounds for length 3
Program continues...
```

🧠 **Explanation:**
`ArrayIndexOutOfBoundsException` is a **RuntimeException**, which is **unchecked**, so no compiler error even if we don’t handle it.

---

## ⚖️ **Difference Between Checked & Unchecked Exceptions**

| **Aspect**             | **Checked Exception**                                   | **Unchecked Exception**                                                         |
| ---------------------- | ------------------------------------------------------- | ------------------------------------------------------------------------------- |
| **Compile-time Check** | Checked at compile time                                 | Not checked by compiler                                                         |
| **Type**               | Subclasses of `Exception` (except `RuntimeException`)   | Subclasses of `RuntimeException`                                                |
| **Handling Required?** | ✅ Yes, must handle or declare using `throws`            | ❌ No, handling is optional                                                      |
| **Common Causes**      | Input/Output, Database, Network errors                  | Logic or programming errors                                                     |
| **Examples**           | `IOException`, `SQLException`, `ClassNotFoundException` | `NullPointerException`, `ArithmeticException`, `ArrayIndexOutOfBoundsException` |
| **When to Use**        | When error comes from outside the program               | When error is due to programmer’s fault                                         |

---

## 🧠 **When We Use Each:**

* **Checked:** When program deals with **external resources** (network, DB, files).
* **Unchecked:** When handling **logic-related issues** in the code itself.

---

## 🧩 **3️⃣ Quick Summary**

✅ **Checked = compile-time validation**
✅ **Unchecked = runtime validation**
✅ **Both** inherit from `Throwable`, but through **different subclasses**

---

Would you like me to now **generate an image/slide design** for this topic —
a diagram showing two branches from `Exception`:

* one labeled **Checked Exceptions (compile-time)**
* one labeled **Unchecked Exceptions (runtime)**
  with examples under each?
