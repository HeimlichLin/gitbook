---
description: >-
  工廠模式（Factory
  Pattern）是一種創建型設計模式，它提供一個統一的介面來創建物件，但允許子類別選擇實際要實例化的類別。這使得客戶端代碼與具體的類別實作分離，從而提高了程式碼的可擴展性和可維護性。
---

# 工廠模式（Factory Pattern）

工廠模式包括以下幾個主要元素：

1. #### 產品介面（Product Interface）：定義了要由工廠創建的物件的通用方法。
2. 具體產品（Concrete Products）：實作產品介面的具體類別。
3. 工廠介面（Factory Interface）：定義了創建產品的方法，通常包括一個或多個工廠方法。
4. 具體工廠（Concrete Factory）：實作工廠介面，負責實際創建具體產品的實例。

以下是一個使用JAVA語言的簡單範例來說明工廠模式：

```java
// 產品介面
interface Product {
    void display();
}

// 具體產品 A
class ConcreteProductA implements Product {
    @Override
    public void display() {
        System.out.println("這是具體產品 A。");
    }
}

// 具體產品 B
class ConcreteProductB implements Product {
    @Override
    public void display() {
        System.out.println("這是具體產品 B。");
    }
}

// 工廠介面
interface Factory {
    Product createProduct();
}

// 具體工廠 A
class ConcreteFactoryA implements Factory {
    @Override
    public Product createProduct() {
        return new ConcreteProductA();
    }
}

// 具體工廠 B
class ConcreteFactoryB implements Factory {
    @Override
    public Product createProduct() {
        return new ConcreteProductB();
    }
}

public class Main {
    public static void main(String[] args) {
        // 創建工廠 A 並使用它創建產品 A
        Factory factoryA = new ConcreteFactoryA();
        Product productA = factoryA.createProduct();
        productA.display();

        // 創建工廠 B 並使用它創建產品 B
        Factory factoryB = new ConcreteFactoryB();
        Product productB = factoryB.createProduct();
        productB.display();
    }
}
```

在這個範例中，我們定義了一個產品介面\*\*`Product`**，並實作了兩個具體產品**`ConcreteProductA`**和**`ConcreteProductB`**，它們實作了**`display`**方法以提供特定的功能。然後，我們定義了工廠介面**`Factory`**，並實作了兩個具體工廠**`ConcreteFactoryA`**和**`ConcreteFactoryB`\*\*，每個工廠負責創建相對應的產品。

當我們在\*\*`Main`**類別中創建具體工廠，然後使用工廠的**`createProduct`\*\*方法時，它將返回相應的產品，而客戶端代碼無需關心具體的實現細節。這使得程式碼更具靈活性，並允許輕鬆添加新的產品和工廠類別，同時保持客戶端代碼的不變。
