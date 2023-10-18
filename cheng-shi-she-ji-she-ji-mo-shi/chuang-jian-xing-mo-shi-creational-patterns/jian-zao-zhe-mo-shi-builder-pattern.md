---
description: >-
  建造者模式（Builder
  Pattern）是一種創建型設計模式，用於創建複雜對象。它通常用於創建一個複雜的對象，並將其構建過程和表示分離。這允許用戶端代碼創建一個對象，並通過將不同的部分或屬性添加到該對象來自訂該對象。
---

# 建造者模式（Builder Pattern）

建造者模式通常包括以下主要元素：

1. 產品（Product）：要創建的複雜對象，通常包括多個部分或屬性。
2. 抽象建造者（Abstract Builder）：定義了建造對象的方法，通常包括設定每個部分或屬性的方法。
3. 具體建造者（Concrete Builder）：實作抽象建造者介面，負責構建實際的產品。
4. 指導者（Director）：協調具體建造者以創建產品。指導者並不直接創建產品，而是通過具體建造者執行創建過程。

以下是一個使用JAVA語言的簡單範例，說明建造者模式：

```java
// 產品 - 複雜對象
class Computer {
    private String CPU;
    private String RAM;
    private String storage;

    public Computer(String CPU, String RAM, String storage) {
        this.CPU = CPU;
        this.RAM = RAM;
        this.storage = storage;
    }

    public void display() {
        System.out.println("CPU: " + CPU);
        System.out.println("RAM: " + RAM);
        System.out.println("Storage: " + storage);
    }
}

// 抽象建造者
interface ComputerBuilder {
    void buildCPU(String CPU);
    void buildRAM(String RAM);
    void buildStorage(String storage);
    Computer build();
}

// 具體建造者
class BasicComputerBuilder implements ComputerBuilder {
    private String CPU;
    private String RAM;
    private String storage;

    @Override
    public void buildCPU(String CPU) {
        this.CPU = CPU;
    }

    @Override
    public void buildRAM(String RAM) {
        this.RAM = RAM;
    }

    @Override
    public void buildStorage(String storage) {
        this.storage = storage;
    }

    @Override
    public Computer build() {
        return new Computer(CPU, RAM, storage);
    }
}

// 指導者
class Director {
    public Computer buildComputer(ComputerBuilder builder) {
        builder.buildCPU("Intel Core i7");
        builder.buildRAM("16GB");
        builder.buildStorage("512GB SSD");
        return builder.build();
    }
}

public class Main {
    public static void main(String[] args) {
        Director director = new Director();
        ComputerBuilder builder = new BasicComputerBuilder();

        Computer computer = director.buildComputer(builder);
        computer.display();
    }
}
```

在這個範例中，我們定義了一個複雜的對象\*\*`Computer`**，包含CPU、RAM和儲存等屬性。我們還定義了一個抽象建造者**`ComputerBuilder`**，它包括了設定這些屬性的方法，以及一個**`build`**方法來創建**`Computer`\*\*對象。

我們實作了具體建造者\*\*`BasicComputerBuilder`**，並實現了**`ComputerBuilder`**介面中的方法。然後，我們定義了一個指導者**`Director`**，它負責協調具體建造者以創建**`Computer`\*\*對象。

在客戶端代碼中，我們通過指導者來建立一個\*\*`Computer`\*\*對象，並使用具體建造者來自訂該對象的屬性。這使得我們可以輕鬆地創建複雜的對象，同時保持其建造過程的可讀性和可維護性。
