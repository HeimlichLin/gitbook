---
description: >-
  橋接模式（Bridge
  Pattern）是一種結構型設計模式，它的主要目的是將抽象部分和實作部分分離，以便它們可以獨立變化。橋接模式的關鍵思想是將一個類別的功能層次結構與另一個類別的實際實作分離開來，從而實現更好的解耦和可擴展性。
---

# 橋接模式（Bridge Pattern）

橋接模式通常包括以下角色：

1. 抽象類別（Abstraction）：定義了類別的抽象部分，通常包括一個成員變數（引用實作部分的介面）和一個抽象方法。抽象類別將客戶端的請求委派給實作部分。
2. 實作類別（Implementor）：定義了實作部分的介面，它通常包括實作方法。實作類別可以有多個不同的實作，並且可以獨立變化。
3. 擴展的抽象類別（Refined Abstraction）：擴展了抽象類別，並實現了更多的功能。這些功能可能會調用實作部分的方法，從而實現客戶端的需求。
4. 具體實作類別（Concrete Implementor）：實現了實作部分的具體實作。一個實作類別可能對應多個不同的具體實作。

以下是一個使用JAVA語言的簡單範例，說明橋接模式：

```java
// 實作類別
interface DrawingAPI {
    void drawCircle(double x, double y, double radius);
}

// 具體實作類別
class DrawingAPI1 implements DrawingAPI {
    @Override
    public void drawCircle(double x, double y, double radius) {
        System.out.printf("API1: 畫一個圓形在坐標(%f, %f) 半徑為 %f%n", x, y, radius);
    }
}

class DrawingAPI2 implements DrawingAPI {
    @Override
    public void drawCircle(double x, double y, double radius) {
        System.out.printf("API2: 畫一個圓形在坐標(%f, %f) 半徑為 %f%n", x, y, radius);
    }
}

// 抽象類別
abstract class Shape {
    protected DrawingAPI drawingAPI;

    protected Shape(DrawingAPI drawingAPI) {
        this.drawingAPI = drawingAPI;
    }

    public abstract void draw();
}

// 擴展的抽象類別
class CircleShape extends Shape {
    private double x, y, radius;

    public CircleShape(double x, double y, double radius, DrawingAPI drawingAPI) {
        super(drawingAPI);
        this.x = x;
        this.y = y;
        this.radius = radius;
    }

    @Override
    public void draw() {
        drawingAPI.drawCircle(x, y, radius);
    }
}

public class Main {
    public static void main(String[] args) {
        DrawingAPI api1 = new DrawingAPI1();
        Shape circle1 = new CircleShape(1, 2, 3, api1);
        circle1.draw();

        DrawingAPI api2 = new DrawingAPI2();
        Shape circle2 = new CircleShape(4, 5, 6, api2);
        circle2.draw();
    }
}
```

在這個範例中，我們有一個抽象類別\*\*`Shape`**，它包含了一個成員變數**`drawingAPI`**，代表實作部分的介面。我們也有一個具體的實作類別**`DrawingAPI1`**和**`DrawingAPI2`**，分別實現了**`DrawingAPI`\*\*介面。

**`CircleShape`是一個擴展的抽象類別，它繼承自`Shape`**，並實現了\*\*`draw`**方法，這個方法調用了**`drawingAPI`**的**`drawCircle`**方法。通過這種方式，我們可以將不同的實作（**`DrawingAPI1`**和**`DrawingAPI2`**）和不同的抽象類別（**`CircleShape`\*\*）組合在一起，實現了彈性的設計，同時允許抽象和實作部分獨立變化。
