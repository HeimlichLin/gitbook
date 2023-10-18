---
description: >-
  裝飾者模式（Decorator
  Pattern）是一種結構型設計模式，它允許你動態地將新功能附加到對象上，而不需要修改其原始結構。這種模式的關鍵思想是創建一個裝飾器類別，它實現了相同的介面並包含一個對原始對象的參考，然後在其中添加額外的行為。裝飾者模式達到了功能擴展的效果，同時保持了對修改封閉的原則（開放/封閉原則）。
---

# 裝飾者模式（Decorator Pattern）

裝飾者模式包括以下主要角色：

1. Component（元件）：定義了原始對象和裝飾者共同實現的介面。
2. ConcreteComponent（具體元件）：實現了元件介面的具體類別，這是我們想要擴展的原始對象。
3. Decorator（裝飾者）：抽象裝飾者類別，包含一個對元件的參考，並實現了元件介面。這是裝飾者的基類。
4. ConcreteDecorator（具體裝飾者）：實現了裝飾者介面的具體類別，添加了額外的功能或狀態。

以下是一個使用JAVA語言的簡單範例，說明裝飾者模式：

```java
// Component（元件）介面
interface Coffee {
    String getDescription();
    double cost();
}

// ConcreteComponent（具體元件）
class Espresso implements Coffee {
    @Override
    public String getDescription() {
        return "Espresso";
    }

    @Override
    public double cost() {
        return 2.0;
    }
}

// Decorator（裝飾者）抽象類別
abstract class CoffeeDecorator implements Coffee {
    private final Coffee decoratedCoffee;

    public CoffeeDecorator(Coffee coffee) {
        this.decoratedCoffee = coffee;
    }

    @Override
    public String getDescription() {
        return decoratedCoffee.getDescription();
    }

    @Override
    public double cost() {
        return decoratedCoffee.cost();
    }
}

// ConcreteDecorator（具體裝飾者）
class MilkDecorator extends CoffeeDecorator {
    public MilkDecorator(Coffee coffee) {
        super(coffee);
    }

    @Override
    public String getDescription() {
        return super.getDescription() + ", Milk";
    }

    @Override
    public double cost() {
        return super.cost() + 0.5;
    }
}

class SugarDecorator extends CoffeeDecorator {
    public SugarDecorator(Coffee coffee) {
        super(coffee);
    }

    @Override
    public String getDescription() {
        return super.getDescription() + ", Sugar";
    }

    @Override
    public double cost() {
        return super.cost() + 0.2;
    }
}

public class Main {
    public static void main(String[] args) {
        Coffee espresso = new Espresso();
        System.out.println("訂購 " + espresso.getDescription() + "，價格：" + espresso.cost() + "元");

        Coffee milkCoffee = new MilkDecorator(espresso);
        System.out.println("訂購 " + milkCoffee.getDescription() + "，價格：" + milkCoffee.cost() + "元");

        Coffee sugarMilkCoffee = new SugarDecorator(milkCoffee);
        System.out.println("訂購 " + sugarMilkCoffee.getDescription() + "，價格：" + sugarMilkCoffee.cost() + "元");
    }
}
```

在這個範例中，我們有一個介面\*\*`Coffee`**代表咖啡，**`Espresso`**是具體元件，它實現了**`Coffee`**介面。然後，我們定義了一個抽象裝飾者類別**`CoffeeDecorator`**，它實現了**`Coffee`**介面，並包含一個對元件的參考。**`MilkDecorator`**和**`SugarDecorator`**是具體裝飾者，它們繼承自**`CoffeeDecorator`\*\*並擴展了功能。

在客戶端代碼中，我們創建了一杯Espresso，然後透過裝飾者模式，我們可以動態地為該咖啡添加牛奶和糖，而不需要修改原始咖啡的程式碼。這個範例展示了如何使用裝飾者模式實現功能的動態擴展。
