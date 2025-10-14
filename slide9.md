

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


