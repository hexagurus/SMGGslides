Nice — here are clear, slide-ready explanations **and simple example programs (no file I/O)** for each keyword: **`try` / `catch`**, **`finally`**, **`throw`**, and **`throws`**. For each: what it is, a short “when/why to use”, a compact program (basic → medium), and a one-line explanation of output/behavior.

# Slide: `try` & `catch`

**What:** `try` wraps code that *may* throw an exception. `catch` receives and handles that exception.
**When/why:** Use when you expect a runtime problem (divide-by-zero, array access, null deref) and you want the program to continue instead of crashing.

### Basic example — handle division by zero

```java
public class TryCatchBasic {
    public static void main(String[] args) {
        int a = 10, b = 0;
        try {
            int r = a / b;                 // may throw ArithmeticException
            System.out.println("Result: " + r);
        } catch (ArithmeticException e) {
            System.out.println("Caught: " + e); // handle it
        }
        System.out.println("After try-catch");
    }
}
```

**Behavior:** Prints the exception message and continues. Use for small, local runtime errors.

### Medium example — multiple catch (different error types)

```java
public class TryCatchMedium {
    public static void main(String[] args) {
        try {
            String s = null;
            System.out.println(s.length());   // may throw NullPointerException
            int[] arr = new int[2];
            System.out.println(arr[5]);       // may throw ArrayIndexOutOfBoundsException
        } catch (NullPointerException npe) {
            System.out.println("Null pointer: " + npe);
        } catch (ArrayIndexOutOfBoundsException aioobe) {
            System.out.println("Array index bad: " + aioobe);
        } catch (RuntimeException re) {
            System.out.println("Other runtime exception: " + re);
        }
        System.out.println("End main");
    }
}
```

**Behavior:** First matching `catch` is executed; subsequent `catch` blocks are skipped.

---

# Slide: `finally`

**What:** Block that executes **always** after `try`/`catch` (even if `return` or exception occurs), typically for cleanup.
**When/why:** Use when you must run some code no matter what — e.g., releasing resources, resetting flags, logging a final message.

### Basic example — always runs

```java
public class FinallyBasic {
    public static void main(String[] args) {
        try {
            System.out.println("In try");
            int x = 5 / 0;               // throws
        } catch (ArithmeticException e) {
            System.out.println("In catch: " + e.getMessage());
        } finally {
            System.out.println("In finally (always runs)");
        }
        System.out.println("After finally");
    }
}
```

**Behavior:** `finally` message prints even though exception occurred.

### Medium example — finally with return (still executes)

```java
public class FinallyWithReturn {
    public static int test() {
        try {
            System.out.println("try");
            return 1;
        } catch (Exception e) {
            System.out.println("catch");
            return -1;
        } finally {
            System.out.println("finally (executes before actual return)");
        }
    }

    public static void main(String[] args) {
        System.out.println("Returned: " + test());
    }
}
```

**Behavior:** `finally` runs before the method actually returns. Useful for guaranteeable cleanup.

---

# Slide: `throw`

**What:** Used to **manually throw** an exception object (either built-in or custom).
**When/why:** Use to signal an error condition detected by your code (invalid argument, failed validation). `throw` is how you create and propagate that error immediately.

### Basic example — throw a runtime exception

```java
public class ThrowBasic {
    public static void check(int age) {
        if (age < 18) {
            throw new ArithmeticException("Underage: " + age);
        }
    }
    public static void main(String[] args) {
        try {
            check(15);
        } catch (ArithmeticException e) {
            System.out.println("Caught: " + e.getMessage());
        }
    }
}
```

**Behavior:** `throw` creates an `ArithmeticException` which is then caught in caller.

### Medium example — throw a custom checked exception (but thrown as Runtime for demonstration)

```java
// custom unchecked (Runtime) shown here for simplicity:
class ValidationException extends RuntimeException {
    public ValidationException(String msg) { super(msg); }
}

public class ThrowMedium {
    static void validateName(String name) {
        if (name == null || name.isBlank()) {
            throw new ValidationException("Name required");
        }
    }
    public static void main(String[] args) {
        try {
            validateName("");
        } catch (ValidationException ve) {
            System.out.println("Validation failed: " + ve.getMessage());
        }
    }
}
```

**Behavior:** `throw` lets you create domain-specific errors the same way Java does.

---

# Slide: `throws`

**What:** Declares in a method signature that the method *may* throw a checked exception (or any exception). It tells the caller: “handle or further declare this.”
**When/why:** Use when a method cannot or should not handle an error internally and wants the caller to handle it. Note: for **checked** exceptions, `throws` is required by compiler.

> You requested no file handling. To demonstrate `throws` without files, we’ll make a **custom checked exception**.

### Custom checked exception + `throws` example (medium)

```java
// Define a checked exception by extending Exception
class AgeTooLowException extends Exception {
    public AgeTooLowException(String msg) { super(msg); }
}

public class ThrowsExample {
    // declare that this method may throw a checked exception
    static void register(int age) throws AgeTooLowException {
        if (age < 18) {
            throw new AgeTooLowException("Age " + age + " is less than 18");
        }
        System.out.println("Registered successfully");
    }

    public static void main(String[] args) {
        try {
            register(15);  // caller must handle or declare
        } catch (AgeTooLowException e) {
            System.out.println("Registration failed: " + e.getMessage());
        }
    }
}
```

**Behavior:** Because `AgeTooLowException` is checked, the compiler forces handling; `throws` informs callers of that contract.

### Simple `throws` with unchecked (allowed but not required)

```java
static void doWork() throws RuntimeException {
    throw new RuntimeException("Boom");
}
```

**Note:** Declaring unchecked exceptions with `throws` is legal but not required — it's mostly useful for documentation.

---

# Quick checklist — when to use each

* `try`/`catch`: Surround risky code and handle anticipated runtime problems.
* `finally`: Always run cleanup code regardless of exception or return.
* `throw`: When your method detects an error condition and must signal it immediately.
* `throws`: When your method wants to pass responsibility of handling a (checked) exception to its caller.

---

If you want, I can:

* Format each of these into **individual slide images** (design + code) like your previous slides, or
* Generate a single downloadable **.pptx** with these slides and code blocks formatted nicely.

Which would you like next?
