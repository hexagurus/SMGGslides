Excellent 👏
Let’s move on to the next topic:

# 🎓 **Slide: Class `Throwable` in Java**

---

## 🧩 **What is `Throwable`?**

### 📘 **Definition:**

> In Java, the **`Throwable`** class is the **superclass** of all errors and exceptions that can be thrown and caught in a program.

Everything that can be used with `throw` or caught in a `catch` block is a subclass of `Throwable`.

---

## 🧠 **Hierarchy Overview**

```
Object
 └── Throwable
      ├── Exception
      │    └── RuntimeException
      │         ├── ArithmeticException
      │         ├── NullPointerException
      │         └── ArrayIndexOutOfBoundsException
      └── Error
           ├── OutOfMemoryError
           ├── StackOverflowError
           └── VirtualMachineError
```

🧩 **Explanation:**

* **`Throwable`** → root of exception/error hierarchy.
* **`Exception`** → recoverable issues.
* **`Error`** → serious system-level failures.

---

## 💡 **Why We Use `Throwable`:**

✅ To access useful information about exceptions like:

* The **message** describing the error
* The **stack trace** showing where it occurred
* The **class name** of the thrown exception

✅ Useful for **logging**, **debugging**, and **error reporting**

---

## ⚙️ **Important Methods in `Throwable`:**

| Method              | Description                                      |
| ------------------- | ------------------------------------------------ |
| `getMessage()`      | Returns the description message of the exception |
| `toString()`        | Returns a short description of the throwable     |
| `printStackTrace()` | Prints the detailed stack trace of the throwable |
| `getCause()`        | Returns the cause of the exception (if any)      |

---

## 💡 **Basic Example: Using `getMessage()` and `toString()`**

```java
public class ThrowableBasic {
    public static void main(String[] args) {
        try {
            int a = 10 / 0;  // ArithmeticException
        } catch (Throwable t) { // can catch both Exception and Error
            System.out.println("Message: " + t.getMessage());
            System.out.println("ToString: " + t.toString());
        }
    }
}
```

### 🧾 **Output:**

```
Message: / by zero
ToString: java.lang.ArithmeticException: / by zero
```

🧠 **Explanation:**

* `Throwable` can catch **any exception or error**, but generally, we catch specific types.
* `getMessage()` gives the detail string.
* `toString()` includes the class name and message.

---

## 💡 **Medium Example: Using `printStackTrace()`**

```java
public class ThrowableMedium {
    public static void main(String[] args) {
        try {
            String s = null;
            System.out.println(s.length());
        } catch (Throwable t) {
            System.out.println("Exception caught!");
            t.printStackTrace(); // prints entire call stack
        }
        System.out.println("Program continues normally...");
    }
}
```

### 🧾 **Output (example):**

```
Exception caught!
java.lang.NullPointerException
	at ThrowableMedium.main(ThrowableMedium.java:5)
Program continues normally...
```

🧠 **Explanation:**

* `printStackTrace()` shows **where** the exception occurred (class, method, line number).
* It helps programmers **debug errors** effectively.

---

## ⚖️ **Summary**

| **Property**   | **Description**                                       |
| -------------- | ----------------------------------------------------- |
| **Superclass** | `Throwable` is the root of all errors and exceptions  |
| **Subclasses** | `Exception`, `Error`                                  |
| **Purpose**    | To represent all objects that can be thrown or caught |
| **Methods**    | `getMessage()`, `toString()`, `printStackTrace()`     |

---

## 🧠 **When to Use:**

* When you want to **log detailed exception info**
* When you need to **debug exception origins**
* When writing **custom logging frameworks** or **global exception handlers**

---

Would you like me to now **generate a PowerPoint-style image** showing the `Throwable` class hierarchy tree (Object → Throwable → Exception/Error) with method icons and arrows for your slide?
