

---

### 🟡 **1. Enum → Type-safe constants**

```java
// File: TrafficSignal.java
enum Signal {
    RED, YELLOW, GREEN
}

public class TrafficSignal {
    public static void main(String[] args) {
        Signal current = Signal.RED;

        switch (current) {
            case RED -> System.out.println("STOP!");
            case YELLOW -> System.out.println("GET READY!");
            case GREEN -> System.out.println("GO!");
        }

        // Enum methods
        for (Signal s : Signal.values()) {
            System.out.println(s + " - ordinal: " + s.ordinal());
        }
    }
}
```

✅ **Key Concepts:**

* Enums give **type-safe constants** (no accidental invalid values).
* You can use `switch` with enums.
* Methods like `values()` and `ordinal()` are available automatically.

---

### 🧮 **2. Math → Mathematical operations and constants**

```java
public class MathDemo {
    public static void main(String[] args) {
        double x = 9.0;
        double y = -4.7;

        System.out.println("Square root of x: " + Math.sqrt(x));
        System.out.println("Absolute value of y: " + Math.abs(y));
        System.out.println("Max between x and y: " + Math.max(x, y));
        System.out.println("Power: 2^5 = " + Math.pow(2, 5));
        System.out.println("PI constant: " + Math.PI);
        System.out.println("E constant: " + Math.E);
    }
}
```

✅ **Key Concepts:**

* `Math` is a **final class with static methods** — no object creation.
* Common methods: `sqrt()`, `abs()`, `max()`, `pow()`, `ceil()`, `floor()`.
* Constants: `Math.PI`, `Math.E`.

---


Great question 👌
Let’s break it down step by step.

---

## 🧠 **1. What are Wrapper Classes in Java?**

In Java, **wrapper classes** are **object representations of primitive data types**.
Java is an **object-oriented language**, but primitive types like `int`, `char`, `boolean` are **not objects**.
So, Java provides **wrapper classes** in the `java.lang` package to “wrap” primitive values inside objects.

| Primitive Type | Wrapper Class |
| -------------- | ------------- |
| `byte`         | `Byte`        |
| `short`        | `Short`       |
| `int`          | `Integer`     |
| `long`         | `Long`        |
| `float`        | `Float`       |
| `double`       | `Double`      |
| `char`         | `Character`   |
| `boolean`      | `Boolean`     |

---

## 🧰 **2. Why Wrapper Classes Are Needed**

Wrapper classes are useful when:

* ✅ You want to use primitive values in **collections** like `ArrayList`, `HashMap` (which only store objects).
* ✅ You need to **convert primitives to strings** and vice versa.
* ✅ You want to use **utility methods** (e.g., `Integer.parseInt()` or `Character.isDigit()`).
* ✅ You need to **pass primitives as objects** to methods.

---

## ✨ **3. Example: Without Wrapper Class**

```java
public class WrapperExample1 {
    public static void main(String[] args) {
        int x = 10;  // primitive
        // ArrayList<int> list = new ArrayList<>(); // ❌ This gives error

        // So we can't use primitives directly in collections
    }
}
```

---

## ✨ **4. Example: Using Wrapper Class**

```java
import java.util.ArrayList;

public class WrapperExample2 {
    public static void main(String[] args) {
        Integer x = Integer.valueOf(10);  // wrapping primitive int into Integer object

        ArrayList<Integer> list = new ArrayList<>();
        list.add(x);             // ✅ works because Integer is an object
        list.add(20);            // Autoboxing happens (primitive -> object)

        System.out.println("ArrayList: " + list);
    }
}
```

📝 Output:

```
ArrayList: [10, 20]
```

---

## 🔄 **5. Autoboxing and Unboxing**

### 🟡 **Autoboxing**

Automatic conversion of **primitive → wrapper object**.

```java
int a = 5;
Integer b = a;  // autoboxing
```

---

### 🟡 **Unboxing**

Automatic conversion of **wrapper object → primitive**.

```java
Integer c = 10;
int d = c;  // unboxing
```

---

### 📌 Example with both:

```java
public class AutoBoxingUnboxing {
    public static void main(String[] args) {
        int num = 100;

        // Autoboxing: primitive -> wrapper
        Integer obj = num;
        System.out.println("Autoboxing: " + obj);

        // Unboxing: wrapper -> primitive
        int num2 = obj;
        System.out.println("Unboxing: " + num2);
    }
}
```

📝 Output:

```
Autoboxing: 100
Unboxing: 100
```

---

## 🧪 **6. Common Methods in Wrapper Classes**

| Method               | Description                          | Example                                |
| -------------------- | ------------------------------------ | -------------------------------------- |
| `parseXxx(String s)` | Converts string to primitive         | `int x = Integer.parseInt("25");`      |
| `valueOf(String s)`  | Converts string to wrapper object    | `Integer obj = Integer.valueOf("25");` |
| `xxxValue()`         | Converts wrapper object to primitive | `int x = obj.intValue();`              |
| `toString()`         | Converts object to string            | `obj.toString();`                      |

```java
public class WrapperMethods {
    public static void main(String[] args) {
        String s = "123";

        int x = Integer.parseInt(s);  // string to int
        Integer y = Integer.valueOf(s); // string to Integer object

        System.out.println(x + 10);
        System.out.println(y.toString());
    }
}
```

---

## 🌟 **7. Character and Boolean Wrappers**

```java
public class WrapperSpecial {
    public static void main(String[] args) {
        Character ch = 'A';
        System.out.println(Character.isLetter(ch));   // true
        System.out.println(Character.isDigit('5'));   // true

        Boolean bool = Boolean.valueOf("true");
        if (bool) {
            System.out.println("It’s true!");
        }
    }
}
```

---

## 📝 **8. Key Points to Remember**

* Wrapper classes make primitives **object-like**.
* Useful for **collections**, **parsing**, and **method arguments**.
* Autoboxing/unboxing helps avoid manual conversion.
* All wrapper classes are **immutable** (once created, their value cannot change).
* They belong to `java.lang` (import not required explicitly).

---

### ✅ **Summary**

> **Wrapper classes** = Object versions of primitive data types.
> They allow primitives to be used where objects are required, and provide many utility methods.

---


Here are **clear and classroom-friendly Java example programs** — **one for each subtopic** you listed under `java.lang`:

---

### 🟡 **1. Enum → Type-safe constants**

```java
// File: TrafficSignal.java
enum Signal {
    RED, YELLOW, GREEN
}

public class TrafficSignal {
    public static void main(String[] args) {
        Signal current = Signal.RED;

        switch (current) {
            case RED -> System.out.println("STOP!");
            case YELLOW -> System.out.println("GET READY!");
            case GREEN -> System.out.println("GO!");
        }

        // Enum methods
        for (Signal s : Signal.values()) {
            System.out.println(s + " - ordinal: " + s.ordinal());
        }
    }
}
```

✅ **Key Concepts:**

* Enums give **type-safe constants** (no accidental invalid values).
* You can use `switch` with enums.
* Methods like `values()` and `ordinal()` are available automatically.

---

### 🧮 **2. Math → Mathematical operations and constants**

```java
public class MathDemo {
    public static void main(String[] args) {
        double x = 9.0;
        double y = -4.7;

        System.out.println("Square root of x: " + Math.sqrt(x));
        System.out.println("Absolute value of y: " + Math.abs(y));
        System.out.println("Max between x and y: " + Math.max(x, y));
        System.out.println("Power: 2^5 = " + Math.pow(2, 5));
        System.out.println("PI constant: " + Math.PI);
        System.out.println("E constant: " + Math.E);
    }
}
```

✅ **Key Concepts:**

* `Math` is a **final class with static methods** — no object creation.
* Common methods: `sqrt()`, `abs()`, `max()`, `pow()`, `ceil()`, `floor()`.
* Constants: `Math.PI`, `Math.E`.

---

### 🧱 **3. Wrapper Classes → Object representation of primitives**

```java
public class WrapperDemo {
    public static void main(String[] args) {
        // Primitive to Wrapper (Boxing)
        int a = 25;
        Integer objA = Integer.valueOf(a);
        Double objB = Double.valueOf(12.5);

        // Wrapper to Primitive (Unboxing)
        int num = objA.intValue();
        double d = objB.doubleValue();

        System.out.println("Boxed Integer: " + objA);
        System.out.println("Boxed Double: " + objB);
        System.out.println("Unboxed int: " + num);
        System.out.println("Unboxed double: " + d);

        // Wrapper utility methods
        System.out.println("Integer MAX: " + Integer.MAX_VALUE);
        System.out.println("Integer MIN: " + Integer.MIN_VALUE);
        System.out.println("Parsed from String: " + Integer.parseInt("123"));
    }
}
```

✅ **Key Concepts:**

* Each primitive has a corresponding wrapper class (e.g., `int → Integer`).
* Wrappers are immutable objects.
* Provide utility methods like `parseInt()`, `MAX_VALUE`.

---

### 🔄 **4. Autoboxing & Unboxing → Automatic conversion**

```java
import java.util.ArrayList;

public class AutoBoxingDemo {
    public static void main(String[] args) {
        // Autoboxing: primitive → object automatically
        Integer num = 10;   // Compiler converts to Integer.valueOf(10)
        ArrayList<Integer> list = new ArrayList<>();
        list.add(20);       // Autoboxed

        // Unboxing: object → primitive automatically
        int val = num;      // Compiler converts to num.intValue()
        int sum = val + list.get(0);  // list.get(0) is unboxed

        System.out.println("Value of num: " + num);
        System.out.println("List element: " + list.get(0));
        System.out.println("Sum: " + sum);

        // ⚠️ NullPointerException if unboxing null
        Integer n = null;
        // int x = n; // This would throw NPE!
    }
}
```

✅ **Key Concepts:**

* Introduced in Java 5.
* Happens automatically during assignments, arithmetic, and method calls.
* ⚠️ Unboxing null causes `NullPointerException`.

---

### 🟨 **Trainer Tips for Teaching This Section:**

* **Run each program live** after explaining the concept — these are all short and compile instantly.
* Use **Enum** for relatable examples (e.g., Traffic lights, Days of the Week).
* For **Wrapper Classes**, explain the **difference between primitive vs object memory behavior**.
* **Autoboxing pitfalls**: explicitly show what happens with `null` unboxing — it’s a great trick interviewers use too.

---

Excellent 👌 — This is a **very important concept** in Java, especially when working with Collections and Wrapper Classes.
Let’s understand it step by step 👇

---

## 🧠 **1. What is Autoboxing?**

👉 **Autoboxing** is the **automatic conversion** by the Java compiler of a **primitive type → its corresponding wrapper class object**.
This was introduced in **Java 5** to make code cleaner and more readable.

### 🔸 Example:

```java
int num = 10;
Integer obj = num;   // ✅ Autoboxing happens here
```

👉 Internally, the compiler does something like:

```java
Integer obj = Integer.valueOf(num);
```

### ✅ Why Autoboxing is Needed:

* Java Collections (e.g., `ArrayList`) can **store only objects**, not primitive values.
* Earlier, we had to manually convert primitives to objects using methods like `Integer.valueOf()`.
* Autoboxing removes this **manual wrapping**.

---

## 🧠 **2. What is Auto-unboxing?**

👉 **Auto-unboxing** is the **reverse process** — automatic conversion of a **wrapper object → its corresponding primitive type**.

### 🔸 Example:

```java
Integer obj = 20;
int num = obj;   // ✅ Auto-unboxing happens here
```

👉 Internally, the compiler does:

```java
int num = obj.intValue();
```

### ✅ Why Auto-unboxing is Needed:

* When you perform arithmetic operations or use wrapper objects in places where primitives are expected, Java automatically converts them back.

---

## 🧪 **3. Example Program: Autoboxing and Auto-unboxing**

```java
public class AutoBoxingUnboxingExample {
    public static void main(String[] args) {
        // 👇 Primitive type
        int a = 100;

        // ✅ Autoboxing: primitive → Wrapper object
        Integer objA = a;
        System.out.println("Autoboxing: Integer object value = " + objA);

        // 👇 Wrapper object
        Integer objB = Integer.valueOf(50);

        // ✅ Auto-unboxing: Wrapper object → primitive
        int b = objB;
        System.out.println("Auto-unboxing: Primitive int value = " + b);

        // 🔸 Autoboxing inside collections
        java.util.ArrayList<Integer> list = new java.util.ArrayList<>();
        list.add(10); // primitive int is automatically autoboxed to Integer object
        list.add(20);
        list.add(a);  // same here

        System.out.println("ArrayList after Autoboxing: " + list);

        // 🔸 Auto-unboxing during arithmetic operations
        Integer x = 5;
        Integer y = 10;

        int sum = x + y;  // both x and y are auto-unboxed to int during addition
        System.out.println("Sum after Auto-unboxing: " + sum);
    }
}
```

### 📝 **Output:**

```
Autoboxing: Integer object value = 100
Auto-unboxing: Primitive int value = 50
ArrayList after Autoboxing: [10, 20, 100]
Sum after Auto-unboxing: 15
```

---

## 📝 **4. Key Points to Remember**

| Autoboxing                         | Auto-unboxing                               |
| ---------------------------------- | ------------------------------------------- |
| Converts **primitive → object**    | Converts **object → primitive**             |
| Uses `valueOf()` internally        | Uses `xxxValue()` internally                |
| Useful when storing in collections | Useful when doing arithmetic or assignments |
| Example: `Integer obj = 5;`        | Example: `int x = obj;`                     |

---

## ⚠️ **5. Caution**

Autoboxing can sometimes lead to **NullPointerException** if you try to unbox a `null` object:

```java
Integer obj = null;
int num = obj;   // ❌ Runtime error: NullPointerException
```

So always make sure the object is not null before unboxing.

---

### ✅ **Summary**

* **Autoboxing** = Primitive → Wrapper (automatic)
* **Auto-unboxing** = Wrapper → Primitive (automatic)
* Introduced in Java 5 to make code cleaner and avoid manual conversions.
* Widely used in **collections**, **method calls**, and **arithmetic operations**.

---







