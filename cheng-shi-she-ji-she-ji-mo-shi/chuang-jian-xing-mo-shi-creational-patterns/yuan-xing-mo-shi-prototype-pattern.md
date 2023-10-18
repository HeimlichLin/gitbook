---
description: >-
  原型模式（Prototype
  Pattern）是一種創建型設計模式，它允許通過複製現有對象來創建新的對象，而無需使用標準的構造方法。原型模式主要用於減少對象創建的成本，特別是當創建一個對象的過程很昂貴或複雜時。
---

# 原型模式（Prototype Pattern）

原型模式通常包括以下主要元素：

1. 原型介面（Prototype Interface）：定義了克隆方法，用於創建新對象的複本。
2. 具體原型（Concrete Prototype）：實作了原型介面，並實現了克隆方法以複製自身。
3. 客戶端（Client）：負責使用原型對象來創建新對象的複本。

以下是一個使用JAVA語言的簡單範例，說明原型模式：

```java
// 原型介面
interface CloneablePrototype extends Cloneable {
    CloneablePrototype clone();
}

// 具體原型
class ConcretePrototype implements CloneablePrototype {
    private String name;

    public ConcretePrototype(String name) {
        this.name = name;
    }

    @Override
    public CloneablePrototype clone() {
        // 使用Java的淺拷貝來創建複本
        try {
            return (CloneablePrototype) super.clone();
        } catch (CloneNotSupportedException e) {
            return null;
        }
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }
}

public class Main {
    public static void main(String[] args) {
        ConcretePrototype original = new ConcretePrototype("原型物件");

        // 使用原型物件創建新的複本
        ConcretePrototype copy1 = (ConcretePrototype) original.clone();
        ConcretePrototype copy2 = (ConcretePrototype) original.clone();

        // 修改複本的屬性不影響原型
        copy1.setName("複本1");
        copy2.setName("複本2");

        System.out.println("原型物件名稱: " + original.getName()); // 原型物件名稱: 原型物件
        System.out.println("複本1名稱: " + copy1.getName()); // 複本1名稱: 複本1
        System.out.println("複本2名稱: " + copy2.getName()); // 複本2名稱: 複本2
    }
}
```

在這個範例中，我們首先定義了一個原型介面\*\*`CloneablePrototype`**，它包含了**`clone`**方法用於創建新對象的複本。然後，我們實作了具體原型**`ConcretePrototype`**，並實現了**`clone`\*\*方法，使用Java的淺拷貝來創建複本。

在客戶端代碼中，我們創建一個原型對象，然後使用\*\*`clone`\*\*方法來創建新的複本。修改複本的屬性不影響原型，因為它們是獨立的對象。這使得我們可以輕鬆地創建多個相似的對象，同時降低對象創建的成本。
