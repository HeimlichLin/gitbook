---
description: >-
  單一職責原則（Single Responsibility
  Principle，縮寫為SRP）是面向物件設計中的一個基本原則，它建議一個類別應該只有一個單一的職責或功能，即一個類別應該只負責一個特定的工作。這個原則旨在確保類別保持簡單、易於理解和容易維護。
---

# 單一職責原則（Single Responsibility Principle，SRP）

單一職責原則有以下幾個關鍵點：

1. 每個類別只有一個原因去改變：如果一個類別具有多個職責，當其中一個職責需要變更時，可能會影響到其他職責，這會導致代碼的複雜性和風險。
2. 分離關注點：將不同的職責分開，使代碼更易於理解、測試和維護。這可以通過將相關的代碼組織在不同的類別中實現。
3. 提高代碼的可讀性和可維護性：具有單一職責的類別更容易理解，因為它們專注於特定的工作，並且更容易維護，因為變更只會影響一個地方。

以下是一個使用JAVA語言的簡單範例，說明單一職責原則：

```java
// 類別負責記錄日誌訊息
class Logger {
    public void logInfo(String message) {
        System.out.println("Info: " + message);
    }

    public void logError(String message) {
        System.out.println("Error: " + message);
    }
}

// 類別負責計算數學運算
class Calculator {
    public int add(int a, int b) {
        return a + b;
    }

    public int subtract(int a, int b) {
        return a - b;
    }
}

public class Main {
    public static void main(String[] args) {
        Logger logger = new Logger();
        Calculator calculator = new Calculator();

        logger.logInfo("這是一條資訊訊息");
        logger.logError("這是一條錯誤訊息");

        int result = calculator.add(5, 3);
        System.out.println("5 + 3 = " + result);

        result = calculator.subtract(10, 4);
        System.out.println("10 - 4 = " + result);
    }
}
```

在這個範例中，我們有兩個類別，**`Logger`和`Calculator`**。\*\*`Logger`**類別負責記錄日誌訊息，而**`Calculator`\*\*類別負責數學運算。每個類別都只有一個明確的職責，並且不牽涉到其他職責。

這遵循單一職責原則，使代碼更具可讀性和可維護性。如果需要修改日誌記錄或數學運算，只需關注相應的類別，而不需要擔心其他不相關的代碼。这提高了代碼的清晰度和可維護性。
