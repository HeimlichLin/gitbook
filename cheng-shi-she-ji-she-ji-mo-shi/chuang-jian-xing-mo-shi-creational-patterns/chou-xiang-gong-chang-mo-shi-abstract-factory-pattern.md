---
description: >-
  抽象工廠模式（Abstract Factory
  Pattern）是一種創建型設計模式，它提供了一種方式來創建相關的物件家族，而無需指定具體的類別。這模式是工廠模式的擴展，它允許創建一組相關的物件，而不僅僅是單個物件。抽象工廠模式通常涉及多個抽象介面，每個介面定義了一個物件家族的相關方法。
---

# 抽象工廠模式（Abstract Factory Pattern）

抽象工廠模式包括以下主要元素：

1. 抽象工廠（Abstract Factory）：定義了一組相關產品的創建方法。通常包含多個抽象方法，每個方法用於創建特定類別的物件。
2. 具體工廠（Concrete Factory）：實作抽象工廠介面，負責創建一組相關的產品。
3. 抽象產品（Abstract Product）：定義了相關產品家族的通用方法。
4. 具體產品（Concrete Product）：實作抽象產品介面，提供特定產品家族的具體實現。

以下是一個使用JAVA語言的簡單範例，說明抽象工廠模式：

```java
// 抽象產品介面
interface Button {
    void display();
}

// 具體產品 A - 按鈕
class WindowsButton implements Button {
    @Override
    public void display() {
        System.out.println("顯示Windows風格按鈕");
    }
}

// 具體產品 B - 按鈕
class MacOSButton implements Button {
    @Override
    public void display() {
        System.out.println("顯示macOS風格按鈕");
    }
}

// 抽象產品介面
interface Checkbox {
    void display();
}

// 具體產品 A - 复选框
class WindowsCheckbox implements Checkbox {
    @Override
    public void display() {
        System.out.println("顯示Windows風格複選框");
    }
}

// 具體產品 B - 复选框
class MacOSCheckbox implements Checkbox {
    @Override
    public void display() {
        System.out.println("顯示macOS風格複選框");
    }
}

// 抽象工廠介面
interface GUIFactory {
    Button createButton();
    Checkbox createCheckbox();
}

// 具體工廠 A - Windows工廠
class WindowsFactory implements GUIFactory {
    @Override
    public Button createButton() {
        return new WindowsButton();
    }

    @Override
    public Checkbox createCheckbox() {
        return new WindowsCheckbox();
    }
}

// 具體工廠 B - macOS工廠
class MacOSFactory implements GUIFactory {
    @Override
    public Button createButton() {
        return new MacOSButton();
    }

    @Override
    public Checkbox createCheckbox() {
        return new MacOSCheckbox();
    }
}

public class Main {
    public static void main(String[] args) {
        // 選擇要使用的工廠（Windows或macOS）
        GUIFactory factory = new WindowsFactory(); // 也可以使用MacOSFactory

        // 使用工廠創建按鈕和複選框
        Button button = factory.createButton();
        Checkbox checkbox = factory.createCheckbox();

        // 顯示產品
        button.display();
        checkbox.display();
    }
}
```

在這個範例中，我們定義了兩種產品家族：按鈕和複選框，每個家族有兩個具體產品。我們還定義了一個抽象工廠介面\*\*`GUIFactory`**，它包含了兩個抽象方法，分別用於創建按鈕和複選框。然後，我們實作了兩個具體工廠**`WindowsFactory`**和**`MacOSFactory`\*\*，每個工廠負責創建相應的產品。

客戶端代碼可以通過選擇要使用的工廠來創建特定風格的按鈕和複選框，而不需要關心具體產品的實現細節。這使得我們可以輕鬆切換不同風格的介面，同時保持代碼的一致性。
