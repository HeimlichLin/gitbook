---
description: >-
  模板方法模式（Template Method
  Pattern）是一種行為型設計模式，它定義了一個算法的骨架，並將某些步驟的實現延遲到子類別中。這種模式允許子類別重新定義算法的某些步驟，而保持算法的整體結構不變。
---

# 模板方法模式（Template Method Pattern）

模板方法模式通常包括以下角色：

1. 抽象模板（Abstract Template）：定義了算法的骨架，包括一系列步驟。這個抽象類別通常包含一個模板方法，該方法包括算法的步驟，其中的某些步驟可能由子類別實現。
2. 具體模板（Concrete Template）：實現了抽象模板中的某些或所有步驟，以完成特定的算法。這些具體類別通常不改變算法的整體結構。

以下是一個使用JAVA語言的簡單範例，說明模板方法模式：

```java
// 抽象模板
abstract class CoffeeTemplate {
    // 模板方法，定義了煮咖啡的算法骨架
    public final void makeCoffee() {
        boilWater();
        brewCoffeeGrinds();
        pourInCup();
        addCondiments();
    }

    // 煮水
    public void boilWater() {
        System.out.println("煮水");
    }

    // 泡咖啡粉
    public void brewCoffeeGrinds() {
        System.out.println("泡咖啡粉");
    }

    // 倒入杯子
    public void pourInCup() {
        System.out.println("倒入杯子");
    }

    // 添加調味料，由子類別實現
    public abstract void addCondiments();
}

// 具體模板1
class CoffeeWithMilk extends CoffeeTemplate {
    @Override
    public void addCondiments() {
        System.out.println("加奶");
    }
}

// 具體模板2
class CoffeeWithSugar extends CoffeeTemplate {
    @Override
    public void addCondiments() {
        System.out.println("加糖");
    }
}

public class Main {
    public static void main(String[] args) {
        CoffeeTemplate coffee1 = new CoffeeWithMilk();
        CoffeeTemplate coffee2 = new CoffeeWithSugar();

        System.out.println("製作咖啡1：");
        coffee1.makeCoffee();

        System.out.println("\n製作咖啡2：");
        coffee2.makeCoffee();
    }
}
```

在這個範例中，我們有一個抽象模板類別\*\*`CoffeeTemplate`\*\*，它定義了煮咖啡的算法骨架，包括煮水、泡咖啡粉、倒入杯子和添加調味料這幾個步驟。其中，添加調味料的步驟是由子類別實現的。

我們有兩個具體模板，即\*\*`CoffeeWithMilk`**和**`CoffeeWithSugar`\*\*，它們分別實現了添加不同調味料的方法。當我們使用這兩個具體模板來製作咖啡時，煮水、泡咖啡粉、倒入杯子等步驟都是一樣的，只有添加調味料的步驟不同，這符合模板方法模式的特點。
