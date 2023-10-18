---
description: >-
  組合模式（Composite
  Pattern）是一種結構型設計模式，它允許您將對象組織成樹狀結構，以表示「部分-整體」層次結構。組合模式用於創建樹狀結構，其中個別對象和組合的對象都以相同的方式對待。這種模式有助於客戶端代碼以一致的方式處理個別對象和組合對象，從而實現對整體結構的遞歸遍歷。
---

# 組合模式（Composite Pattern）

組合模式通常包括以下角色：

1. 組件（Component）：定義了所有對象的通用接口，包括單個對象和組合對象。
2. 葉節點（Leaf）：代表組件結構中的葉節點，它沒有子節點。
3. 組合節點（Composite）：代表組件結構中的組合節點，它可以包含葉節點和/或其他組合節點。組合節點實現了通用的操作，並將這些操作委派給它包含的子節點。

以下是一個使用JAVA語言的簡單範例，說明組合模式：

```java
import java.util.ArrayList;
import java.util.List;

// 組件（Component）介面
interface Component {
    void operation();
}

// 葉節點（Leaf）類別
class Leaf implements Component {
    private String name;

    public Leaf(String name) {
        this.name = name;
    }

    @Override
    public void operation() {
        System.out.println("葉節點 " + name + " 執行操作");
    }
}

// 組合節點（Composite）類別
class Composite implements Component {
    private List<Component> children = new ArrayList<>();
    private String name;

    public Composite(String name) {
        this.name = name;
    }

    public void add(Component component) {
        children.add(component);
    }

    public void remove(Component component) {
        children.remove(component);
    }

    @Override
    public void operation() {
        System.out.println("組合節點 " + name + " 執行操作");
        for (Component child : children) {
            child.operation();
        }
    }
}

public class Main {
    public static void main(String[] args) {
        Component root = new Composite("根節點");
        Component leaf1 = new Leaf("葉節點1");
        Component leaf2 = new Leaf("葉節點2");

        Component composite1 = new Composite("子組合節點1");
        Component leaf3 = new Leaf("葉節點3");
        Component leaf4 = new Leaf("葉節點4");

        Component composite2 = new Composite("子組合節點2");
        Component leaf5 = new Leaf("葉節點5");

        composite1.add(leaf3);
        composite1.add(leaf4);
        composite2.add(leaf5);

        root.add(leaf1);
        root.add(leaf2);
        root.add(composite1);
        root.add(composite2);

        root.operation();
    }
}
```

在這個範例中，我們有一個抽象組件\*\*`Component`**，它定義了所有對象的通用操作。然後，我們實現了葉節點**`Leaf`**和組合節點**`Composite`\*\*，分別代表組件結構中的葉節點和組合節點。

客戶端代碼可以建立一個組合結構，包括葉節點和組合節點。不管是葉節點還是組合節點，它們都可以以相同的方式調用\*\*`operation`\*\*方法，實現遞歸遍歷整個組件結構。這種組合模式有助於處理部分-整體關係，同時保持了代碼的一致性。
