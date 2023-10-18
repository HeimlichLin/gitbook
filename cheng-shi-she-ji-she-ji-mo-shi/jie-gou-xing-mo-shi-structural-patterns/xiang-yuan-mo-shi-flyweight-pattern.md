---
description: >-
  享元模式（Flyweight
  Pattern）是一種結構型設計模式，它旨在減少對象的數量以節省內存或提高性能。這種模式的關鍵思想是共享具有相同狀態的多個對象，以減少內存使用和提高效率。享元模式通常用於當大量類似的對象需要被創建，但它們的內部狀態有些差異的情況下。
---

# 享元模式（Flyweight Pattern）

享元模式通常包括以下角色：

1. 享元（Flyweight）：定義了共享內部狀態的接口。享元對象可以接受外部狀態，但它不應該保存外部狀態。享元對象的內部狀態是可以被共享的。
2. 具體享元（Concrete Flyweight）：實現了享元接口，並維護內部狀態。具體享元對象通常是可共享的，多個客戶端可以共用同一個具體享元對象。
3. 未共享享元（Unshared Concrete Flyweight）：具有不可共享內部狀態的享元對象。這些對象通常是只針對特定客戶端的，不被其他客戶端共用。
4. 享元工廠（Flyweight Factory）：負責創建和管理享元對象，並確保已創建的享元對象可以被共用。

以下是一個使用JAVA語言的簡單範例，說明享元模式：

```java
import java.util.HashMap;
import java.util.Map;

// 享元接口
interface CoffeeOrder {
    void serveCoffee(CoffeeOrderContext context);
}

// 具體享元
class CoffeeFlavor implements CoffeeOrder {
    private final String flavor;

    public CoffeeFlavor(String flavor) {
        this.flavor = flavor;
    }

    @Override
    public void serveCoffee(CoffeeOrderContext context) {
        System.out.println("提供了 " + flavor + " 咖啡給 " + context.getTable());
    }
}

// 具體享元工廠
class CoffeeOrderContext {
    private final int tableNumber;

    public CoffeeOrderContext(int tableNumber) {
        this.tableNumber = tableNumber;
    }

    public int getTable() {
        return tableNumber;
    }
}

// 享元工廠
class CoffeeFlavorFactory {
    private Map<String, CoffeeOrder> flavors = new HashMap<>();

    public CoffeeOrder getCoffeeFlavor(String flavor) {
        if (flavors.containsKey(flavor)) {
            return flavors.get(flavor);
        } else {
            CoffeeOrder coffeeFlavor = new CoffeeFlavor(flavor);
            flavors.put(flavor, coffeeFlavor);
            return coffeeFlavor;
        }
    }

    public int getTotalCoffeeFlavorsMade() {
        return flavors.size();
    }
}

public class Main {
    public static void main(String[] args) {
        CoffeeFlavorFactory flavorFactory = new CoffeeFlavorFactory();

        // 客戶端1點了一杯深焙咖啡
        CoffeeOrder coffee1 = flavorFactory.getCoffeeFlavor("深焙咖啡");
        coffee1.serveCoffee(new CoffeeOrderContext(1));

        // 客戶端2點了一杯拿鐵咖啡
        CoffeeOrder coffee2 = flavorFactory.getCoffeeFlavor("拿鐵咖啡");
        coffee2.serveCoffee(new CoffeeOrderContext(2));

        // 客戶端3點了一杯深焙咖啡
        CoffeeOrder coffee3 = flavorFactory.getCoffeeFlavor("深焙咖啡");
```

在這個範例中，我們模擬了一個咖啡店，客戶可以點不同口味的咖啡。咖啡口味是享元對象，而每個客戶點的咖啡是具體享元對象。我們使用享元工廠來創建和管理咖啡口味的享元對象，確保可以共用相同口味的咖啡。這有助於節省記憶體，因為相同口味的咖啡只需創建一次。

享元模式在需要創建大量相似對象並且這些對象的內部狀態相對穩定時非常有用。透過共享享元對象，可以減少內存使用，提高效能。
