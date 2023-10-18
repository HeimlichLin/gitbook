---
description: >-
  單例模式（Singleton
  Pattern）是一種創建型設計模式，它確保一個類別僅有一個唯一的實例，並提供一個全域訪問點，以確保在應用程式中的任何位置都能夠訪問該實例。單例模式通常用於需要全局設置或共享資源的情況，以確保只有一個實例存在，並提供對該實例的單一點訪問。
---

# 單例模式（Singleton Pattern）

以下是一個使用JAVA語言的簡單範例來說明單例模式：

```java
public class Singleton {
    // 創建一個私有靜態實例變數
    private static Singleton instance;

    // 將建構子設為私有，以防止外部實例化
    private Singleton() {
    }

    // 提供一個公共方法來獲取唯一實例
    public static Singleton getInstance() {
        // 如果實例尚未創建，則在第一次調用時創建它
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
    
    // 添加其他實例方法
    public void doSomething() {
        System.out.println("單例實例正在執行操作。");
    }
}

public class Main {
    public static void main(String[] args) {
        // 透過 Singleton.getInstance() 獲取單例實例
        Singleton singleton1 = Singleton.getInstance();
        Singleton singleton2 = Singleton.getInstance();
        
        // 檢查兩個實例是否相同
        System.out.println(singleton1 == singleton2); // 應該輸出 true
        
        // 使用單例實例執行操作
        singleton1.doSomething();
    }
}
```

在這個範例中，我們創建了一個名為\*\*`Singleton`**的類別，它包含一個私有的靜態實例變數，一個私有的建構子，以及一個公共的**`getInstance`**方法，該方法負責創建並返回唯一的實例。當我們在**`Main`**類別中調用**`Singleton.getInstance()`**時，將始終返回相同的實例，確保只有一個唯一的**`Singleton`\*\*實例存在。

這有助於確保全域資源的合理使用，並避免多次創建不必要的實例。單例模式在實際應用中非常常見，特別是在需要共享資源或設置的情況下。
