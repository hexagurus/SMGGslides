# slide-1

<img width="834" height="510" alt="image" src="https://github.com/user-attachments/assets/7ce83d9d-c453-42f7-a2f1-aa11f57d27f0" />

<p>
Packages in Java are like folders in your computer. Imagine if you kept all your project files in a single folder — it would get chaotic. Packages help us group related classes together, making code modular and easy to navigate.

They also prevent class name conflicts. For example, two teams can both create a Student class in different packages (com.college.Student vs com.training.Student) without issues.

Packages also help in access control and versioning, especially in larger enterprise apps.

Lastly, Java uses the package name to mirror folder structure, which makes compilation and build automation smooth. For example, a class in com.example.util must be stored in com/example/util folders </p>

## Implementation

Great question 👌
For the **first topic – “Introduction to Packages”**, it’s mostly conceptual, but we can still give students a **very simple implementation example** to demonstrate **how packages actually work in a real Java project**.

Below is a **clean, classroom-friendly implementation** you can show live or paste into slides:

---

### 🧪 **Implementation Example: Basic Package Structure**

#### 🗂 **Folder Structure**

```
src/
 └── com/
     └── myapp/
         ├── Main.java
         └── utils/
             └── Greeting.java
```

---

#### 📄 **Greeting.java**

Located in: `src/com/myapp/utils/Greeting.java`

```java
package com.myapp.utils;

public class Greeting {
    public static void sayHello(String name) {
        System.out.println("Hello, " + name + "! Welcome to Java Packages.");
    }
}
```

---

#### 📄 **Main.java**

Located in: `src/com/myapp/Main.java`

```java
package com.myapp;

// Import the Greeting class from utils package
import com.myapp.utils.Greeting;

public class Main {
    public static void main(String[] args) {
        Greeting.sayHello("Students");
    }
}
```

---

#### 🧰 **How to Compile & Run (Command Line)**

From the root folder (where `src` exists):

```bash
javac -d out src/com/myapp/utils/Greeting.java src/com/myapp/Main.java
java -cp out com.myapp.Main
```

✅ **Output:**

```
Hello, Students! Welcome to Java Packages.
```

---
---

