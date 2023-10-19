---
description: >-
  里氏替換原則（Liskov Substitution
  Principle，縮寫為LSP）是面向物件設計中的一個基本原則，是SOLID設計原則中的其中一個，提出了一個重要的概念：如果一個類別是另一個類別的子類別，那麼它們應該可以互相替換而不影響程式的正確性。換句話說，子類別應該保持對父類別的完全兼容性。
---

# 里氏替換原則（Liskov Substitution Principle，LSP）

里氏替換原則的主要觀點如下：

1. 子類別必須能夠替換父類別並保持程式的正確性。這意味著子類別在其父類別的任何位置都可以替代使用，而不會導致意外的行為。
2. 子類別應該保留父類別的所有行為和屬性，並且可以擴展或修改部分行為，但不應該重寫或刪除父類別的行為。
3. 里氏替換原則有助於確保代碼的一致性和可擴展性，並降低代碼錯誤的風險。

以下是一個使用JAVA語言的簡單範例，說明里氏替換原則：

```java
// 父類別
class Bird {
    void fly() {
        System.out.println("鳥類可以飛行");
    }

    void eat() {
        System.out.println("鳥類可以進食");
    }
}

// 子類別1
class Sparrow extends Bird {
    // 子類別保持父類別的行為，不修改或刪除
}

// 子類別2
class Ostrich extends Bird {
    // 子類別可以擴展部分行為
    void run() {
        System.out.println("鴕鳥可以奔跑");
    }
}

public class Main {
    public static void main(String[] args) {
        Bird sparrow = new Sparrow();
        Bird ostrich = new Ostrich();

        sparrow.fly();
        sparrow.eat();

        ostrich.fly();
        ostrich.eat();
        ostrich.run();
    }
}
```

在這個範例中，我們有一個父類別\*\*`Bird`**，它有兩個方法：**`fly`**和**`eat`**。然後，我們創建了兩個子類別**`Sparrow`**和**`Ostrich`**，它們都繼承自父類別**`Bird`\*\*。

根據里氏替換原則，我們可以將子類別的實例替換為父類別的實例，而不會導致任何問題。子類別保留了父類別的所有行為，並且在\*\*`Ostrich`**類別中還擴展了一個新的行為**`run`\*\*。這確保了代碼的一致性和可擴展性，同時符合里氏替換原則的要求。
