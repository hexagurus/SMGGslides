

---

# 🧠 **1. What is `TemporalAdjusters` Class?**

👉 `TemporalAdjusters` is a **utility class** in the **`java.time` package** (introduced in Java 8) that allows you to **perform common date manipulations easily**.

✅ For example:

* Find the **first day of next month**
* Find the **last day of the current year**
* Find the **next Monday**
* Find the **first Friday of next month**, etc.

👉 Instead of manually calculating dates using `plusDays()` or complex calendar logic, **`TemporalAdjusters` gives predefined methods** for such **temporal (time-based)** adjustments.

---

# 🧰 **2. Why We Use `TemporalAdjusters`**

Before Java 8, date manipulation was done using `Calendar` and `Date` classes which were:

* ❌ Complicated
* ❌ Mutable (not thread-safe)
* ❌ Required manual logic to find special dates.

With Java 8:

* ✅ `LocalDate` is immutable & thread-safe.
* ✅ `TemporalAdjusters` provides **ready-made methods** to get dates like “first day of next month” or “next Friday” without manual calculations.

---

# 📚 **3. Common TemporalAdjusters Methods**

| Method                          | Description                                      |
| ------------------------------- | ------------------------------------------------ |
| `firstDayOfMonth()`             | First day of the current month                   |
| `lastDayOfMonth()`              | Last day of the current month                    |
| `firstDayOfNextMonth()`         | First day of next month                          |
| `firstDayOfYear()`              | First day of the current year                    |
| `lastDayOfYear()`               | Last day of the current year                     |
| `next(DayOfWeek day)`           | Next occurrence of the specified day             |
| `nextOrSame(DayOfWeek day)`     | Next occurrence or same day if today matches     |
| `previous(DayOfWeek day)`       | Previous occurrence of the day                   |
| `previousOrSame(DayOfWeek day)` | Previous occurrence or same day if today matches |

---

# 🧪 **4. Example Program: TemporalAdjusters**

```java
import java.time.DayOfWeek;
import java.time.LocalDate;
import java.time.temporal.TemporalAdjusters;

public class TemporalAdjustersExample {
    public static void main(String[] args) {
        // Current date
        LocalDate today = LocalDate.now();
        System.out.println("Today's Date: " + today);

        // 1. First day of current month
        LocalDate firstDayOfMonth = today.with(TemporalAdjusters.firstDayOfMonth());
        System.out.println("First Day of This Month: " + firstDayOfMonth);

        // 2. Last day of current month
        LocalDate lastDayOfMonth = today.with(TemporalAdjusters.lastDayOfMonth());
        System.out.println("Last Day of This Month: " + lastDayOfMonth);

        // 3. First day of next month
        LocalDate firstDayNextMonth = today.with(TemporalAdjusters.firstDayOfNextMonth());
        System.out.println("First Day of Next Month: " + firstDayNextMonth);

        // 4. First day of this year
        LocalDate firstDayOfYear = today.with(TemporalAdjusters.firstDayOfYear());
        System.out.println("First Day of This Year: " + firstDayOfYear);

        // 5. Last day of this year
        LocalDate lastDayOfYear = today.with(TemporalAdjusters.lastDayOfYear());
        System.out.println("Last Day of This Year: " + lastDayOfYear);

        // 6. Next Monday
        LocalDate nextMonday = today.with(TemporalAdjusters.next(DayOfWeek.MONDAY));
        System.out.println("Next Monday: " + nextMonday);

        // 7. Previous Friday
        LocalDate previousFriday = today.with(TemporalAdjusters.previous(DayOfWeek.FRIDAY));
        System.out.println("Previous Friday: " + previousFriday);

        // 8. Next or Same Sunday
        LocalDate nextOrSameSunday = today.with(TemporalAdjusters.nextOrSame(DayOfWeek.SUNDAY));
        System.out.println("Next or Same Sunday: " + nextOrSameSunday);
    }
}
```

---

### 📝 **Sample Output (if today is 2025-10-14):**

```
Today's Date: 2025-10-14
First Day of This Month: 2025-10-01
Last Day of This Month: 2025-10-31
First Day of Next Month: 2025-11-01
First Day of This Year: 2025-01-01
Last Day of This Year: 2025-12-31
Next Monday: 2025-10-20
Previous Friday: 2025-10-10
Next or Same Sunday: 2025-10-19
```

---

# 📌 **5. How It Works Internally**

When you call:

```java
today.with(TemporalAdjusters.firstDayOfMonth());
```

* `today` returns a new `LocalDate` object with the **same year and month**, but **day set to 1**.
* It doesn’t change `today` (because `LocalDate` is immutable).

Similarly,

```java
today.with(TemporalAdjusters.next(DayOfWeek.MONDAY));
```

* It finds the **next** date after `today` that falls on a Monday.

---

# ⚠️ **6. Important Notes**

* `TemporalAdjusters` works with classes implementing the **`Temporal` interface**, e.g., `LocalDate`, `LocalDateTime`.
* It does **not** work with `java.util.Date` or `Calendar` directly.
* You can **chain** adjusters if needed.

---

# ✨ **7. Real-World Use Case**

Suppose you're generating **monthly reports**, and you always want to:

* Start from **first day of next month**
* End at **last day of next month**

You can do:

```java
LocalDate reportStart = LocalDate.now().with(TemporalAdjusters.firstDayOfNextMonth());
LocalDate reportEnd = reportStart.with(TemporalAdjusters.lastDayOfMonth());
```

This avoids manual calculations and is **clean and readable** ✅

---

# 📝 **Summary Table**

| Feature         | TemporalAdjusters                                          |
| --------------- | ---------------------------------------------------------- |
| **Package**     | `java.time.temporal`                                       |
| **Purpose**     | Perform common date adjustments easily                     |
| **Returns**     | New adjusted `LocalDate` / Temporal object                 |
| **Common Uses** | First/last day of month/year, next/previous day of week    |
| **Why Use**     | Cleaner code, avoids manual calculations, immutable & safe |

---

✅ **Quick Recap**

* `TemporalAdjusters` = **predefined date adjustment methods** (Java 8+).
* Works with `LocalDate` to get dates like “first day of next month” or “next Friday” easily.
* Improves code readability and reduces error-prone manual date calculations.

---

Would you like me to give a **small mini project** where we use `TemporalAdjusters` to generate **salary payment dates** (e.g., pay on last Friday of every month)? 💼📅
