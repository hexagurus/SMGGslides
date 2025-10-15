

---

### 🟦 **Slide: `java.util.Random` Class**

**📝 Slide Content (PPT):**

```
• Pseudo-random number generator (PRNG) in Java  
• Can be seeded for reproducible sequences  
• Common methods:
   - nextInt() / nextInt(bound)
   - nextDouble(), nextFloat(), nextLong()
   - nextBoolean(), nextGaussian()
• ThreadLocalRandom is preferred for concurrent apps  
• SecureRandom for cryptographically secure use cases
```

---

### 💻 **Example Program: Random, ThreadLocalRandom & SecureRandom**

```java
import java.util.Random;
import java.util.concurrent.ThreadLocalRandom;
import java.security.SecureRandom;

public class RandomExample {
    public static void main(String[] args) {
        // 1️⃣ Random with seed
        Random rand = new Random(42);
        System.out.println("Random int [0..99]: " + rand.nextInt(100));
        System.out.println("Random double: " + rand.nextDouble());

        // 2️⃣ ThreadLocalRandom - modern, faster for concurrent code
        int dice = ThreadLocalRandom.current().nextInt(1, 7);
        System.out.println("Dice roll [1..6]: " + dice);

        // 3️⃣ SecureRandom - cryptographic
        byte[] token = new byte[8];
        new SecureRandom().nextBytes(token);
        System.out.print("Secure token: ");
        for (byte b : token) System.out.printf("%02X", b);
    }
}
```

✅ **Sample Output**

```
Random int [0..99]: 30
Random double: 0.639426798
Dice roll [1..6]: 4
Secure token: 8FA3C1B2A05C44F1
```

---

### 🟨 **Trainer Notes (Explanation):**

> * `Random` is **pseudo-random**, not truly random — same seed → same sequence.
> * Use `nextInt(bound)` for **bounded values** (e.g., dice = 1..6).
> * `ThreadLocalRandom` gives better performance in multi-threaded apps.
> * `SecureRandom` is essential for **passwords, keys, tokens** — slower but secure.
> * `nextGaussian()` gives normally distributed random numbers (mean=0, sd=1). Useful in simulations.
> * Show them what happens if you use the **same seed twice** → same output.

💡 *Quick demo idea:* Run `Random rand = new Random(42);` twice and show that the output matches exactly.

---

### 📸 **Slide Visual:**

Let’s generate a **white background visual** with:

* `Random` → seed → pseudo-random sequence
* `ThreadLocalRandom` node
* `SecureRandom` node with lock icon (security)


✅ **Random Class** slide is ready with clean bullet points, diagram, and example program.
👉 [Download Slide – Random Class](sandbox:/mnt/data/A_slide_from_a_presentation_titled_%22Random_Class%22_.png)

---

Would you like me to move on to the **java.time Package** (Instant, Date/Time Formatting, Temporal Adjusters)?
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/c23fd912-970a-4fc3-89e6-39464b2d7488" />


---
Perfect 👌
Let’s move to **Slide 9 (java.time Package)** — this is a very important modern Java API that replaced the old `Date` and `Calendar` classes in Java 8.
We’ll make this section **clear and practical**, covering:

* 📅 `Instant` (machine time)
* 🕒 Date & Time Formatting
* 🧭 Temporal Adjusters (date arithmetic helpers)

We’ll break it into **three focused slides** for clarity:

---

## 🟦 **Slide 1: java.time Package — Overview**

**📝 Slide Content (PPT):**

```
• Introduced in Java 8 — modern date and time API  
• Replaces java.util.Date and Calendar (which were error-prone and mutable)  
• Immutable, thread-safe classes  
• Key classes:
   - Instant → machine timestamp (UTC)
   - LocalDate / LocalTime / LocalDateTime → human-readable date/time
   - ZonedDateTime → date-time with timezone
   - Duration / Period → time and date differences
   - DateTimeFormatter → parsing and formatting
   - TemporalAdjusters → date arithmetic helpers
```

---

### 🟨 **Trainer Notes (Overview):**

> * `java.time` is inspired by the Joda-Time library, and **fixes all the issues** with old date APIs.
> * All classes are **immutable** and **thread-safe**, so no more unexpected bugs.
> * Think of `Instant` like a **timestamp in UTC**, and `LocalDate` like a **calendar date** in your timezone.
> * `ZonedDateTime` attaches the timezone explicitly.
> * `Duration` and `Period` represent time differences.
> * `DateTimeFormatter` replaces `SimpleDateFormat`.
> * `TemporalAdjusters` simplify tasks like “first Monday of next month”.

---

## 🟦 **Slide 2: Instant & Date-Time Formatting**

**📝 Slide Content (PPT):**

```
• Instant represents a point on the timeline (UTC)  
• Common methods:
   - Instant.now()
   - Instant.ofEpochMilli(...)
   - Duration.between(Instant, Instant)
• ZonedDateTime attaches timezone to date-time
• DateTimeFormatter formats and parses dates
```

---

### 💻 **Example Program: Instant + Formatting**

```java
import java.time.*;
import java.time.format.DateTimeFormatter;

public class InstantDemo {
    public static void main(String[] args) throws InterruptedException {
        // Capture start and end instants
        Instant start = Instant.now();
        Thread.sleep(500);
        Instant end = Instant.now();

        Duration duration = Duration.between(start, end);
        System.out.println("Elapsed millis: " + duration.toMillis());

        // Format current ZonedDateTime
        ZonedDateTime now = ZonedDateTime.now(ZoneId.of("Asia/Kolkata"));
        DateTimeFormatter fmt = DateTimeFormatter.ofPattern("dd-MMM-yyyy HH:mm:ss z");
        System.out.println("Current time: " + now.format(fmt));

        // Parsing ISO date
        LocalDate date = LocalDate.parse("2025-10-14");
        System.out.println("Parsed date: " + date);
    }
}
```

✅ Output Example:

```
Elapsed millis: 501
Current time: 14-Oct-2025 16:02:15 IST
Parsed date: 2025-10-14
```

---

### 🟨 **Trainer Notes (Instant & Formatting):**

> * `Instant.now()` is perfect for timestamps and logging.
> * `ZonedDateTime` adds timezone context — useful for user-facing applications.
> * `DateTimeFormatter` uses patterns like `dd-MMM-yyyy`.
> * Unlike `SimpleDateFormat`, **no need to worry about thread safety** here.
> * Show students how **sleeping for 500 ms** affects the Duration.

---

## 🟦 **Slide 3: Temporal Adjusters**

**📝 Slide Content (PPT):**

```
• TemporalAdjusters = date arithmetic helpers  
• Examples:
   - firstDayOfMonth()
   - lastDayOfMonth()
   - next(DayOfWeek)
   - previousOrSame(DayOfWeek)
   - firstInMonth(DayOfWeek)
• Returns a new adjusted LocalDate
```

---

### 💻 **Example Program: Temporal Adjusters**

```java
import java.time.*;
import java.time.temporal.TemporalAdjusters;
import static java.time.DayOfWeek.MONDAY;

public class AdjustersDemo {
    public static void main(String[] args) {
        LocalDate today = LocalDate.now();

        LocalDate firstMondayNextMonth = today
                .with(TemporalAdjusters.firstDayOfNextMonth())
                .with(TemporalAdjusters.nextOrSame(MONDAY));

        LocalDate monthEnd = today.with(TemporalAdjusters.lastDayOfMonth());

        System.out.println("First Monday of next month: " + firstMondayNextMonth);
        System.out.println("Last day of this month: " + monthEnd);
    }
}
```

✅ Sample Output:

```
First Monday of next month: 2025-11-03
Last day of this month: 2025-10-31
```

---

### 🟨 **Trainer Notes (Adjusters):**

> * Adjusters **make date calculations extremely simple**.
> * You don’t have to manually calculate weekdays or month-end anymore.
> * Common real-world uses: payroll dates, scheduling reports, holidays.
> * All adjusters return **new LocalDate** objects — no mutation.

---

### 📸 **Slide Visuals Planned:**

* **Slide 1:** Overview diagram of `java.time` classes (Instant, LocalDate, ZonedDateTime, Duration, etc.)
* **Slide 2:** Instant & formatting flow (UTC Instant → ZonedDateTime → formatted string)
* **Slide 3:** Calendar with arrows showing “first Monday next month” & “last day of month”

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
