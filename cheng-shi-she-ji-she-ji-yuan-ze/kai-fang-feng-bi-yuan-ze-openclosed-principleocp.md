---
description: >-
  開放/封閉原則（Open/Closed
  Principle，縮寫為OCP）是面向物件設計中的一個基本原則，它建議軟體實體（如類別、模組、函式等）應該對擴展開放，對修改封閉。這意味著當需求改變時，應該通過擴展現有代碼來引入新功能，而不是修改既有的代碼。這有助於減少對現有代碼的風險，同時提高代碼的可維護性和可擴展性。
---

# 開放/封閉原則（Open/Closed Principle，OCP）

開放/封閉原則有以下主要觀點：

1. 對擴展開放：應該能夠在不修改現有代碼的情況下引入新功能。這通常涉及定義擴展點或介面，以便在後續擴展中實現新功能。
2. 對修改封閉：不應該修改既有的代碼，因為這可能會導致現有功能的破壞或其他問題。應該努力保持現有代碼的穩定性。
3. 抽象化：使用抽象化和介面來實現開放/封閉原則，以確保代碼的靈活性和可擴展性。

以下是一個使用JAVA語言的簡單範例，說明開放/封閉原則：

```java
// 開放/封閉原則的示例
class Shape {
    // 形狀的名稱
    private String name;

    public Shape(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    // 計算面積的方法
    public double area() {
        return 0.0;
    }
}

class Circle extends Shape {
    private double radius;

    public Circle(String name, double radius) {
        super(name);
        this.radius = radius;
    }

    @Override
    public double area() {
        return Math.PI * radius * radius;
    }
}

class Rectangle extends Shape {
    private double width;
    private double height;

    public Rectangle(String name, double width, double height) {
        super(name);
        this.width = width;
        this.height = height;
    }

    @Override
    public double area() {
        return width * height;
    }
}

public class Main {
    public static void main(String[] args) {
        Circle circle = new Circle("圓形", 5.0);
        Rectangle rectangle = new Rectangle("矩形", 4.0, 6.0);

        System.out.println(circle.getName() + " 的面積為 " + circle.area());
        System.out.println(rectangle.getName() + " 的面積為 " + rectangle.area());
    }
}
```

在這個範例中，我們定義了一個抽象類別\*\*`Shape`**，它包含一個名稱和一個計算面積的方法**`area`**。然後，我們實作了兩個具體的子類別**`Circle`**和**`Rectangle`**，分別代表圓形和矩形。每個子類別覆寫了**`area`\*\*方法以提供特定形狀的面積計算。

根據開放/封閉原則，如果需要添加新的形狀，我們只需創建一個新的子類別，而不需要修改\*\*`Shape`\*\*類別的代碼。這樣我們保持了現有代碼的封閉性，同時實現了擴展性。這符合開放/封閉原則的核心理念。
