---
description: >-
  狀態模式（State
  Pattern）是一種行為型設計模式，它用於在對象內部狀態發生變化時改變對象的行為。這種模式的核心思想是將對象的狀態抽象為不同的狀態類別，當狀態變化時，對象可以切換到不同的狀態，並根據當前狀態執行相對應的行為。狀態模式有助於使代碼更清晰、可維護和可擴展，因為它將每個狀態的行為封裝在狀態類別中，而不是將所有行為集中在一個龐大的條件語句中。
---

# 狀態模式（State Pattern）

狀態模式通常包括以下角色：

1. 上下文（Context）：維護一個對當前狀態對象的引用，並在需要時切換狀態。上下文通常包含一個方法，用於執行當前狀態的操作。
2. 抽象狀態（State）：定義了所有具體狀態類別的共同接口，並將上下文對象傳遞給每個狀態，以便狀態可以訪問上下文的信息。
3. 具體狀態（Concrete State）：實現了抽象狀態接口，並包含了該狀態下的具體行為。

以下是一個使用JAVA語言的簡單範例，說明狀態模式：

```java
// 抽象狀態
interface State {
    void doAction(Context context);
}

// 具體狀態1
class State1 implements State {
    @Override
    public void doAction(Context context) {
        System.out.println("執行狀態1的操作");
        context.setState(new State2()); // 切換到狀態2
    }
}

// 具體狀態2
class State2 implements State {
    @Override
    public void doAction(Context context) {
        System.out.println("執行狀態2的操作");
        context.setState(new State1()); // 切換到狀態1
    }
}

// 上下文
class Context {
    private State state;

    public Context() {
        state = new State1(); // 初始狀態為狀態1
    }

    public void setState(State state) {
        this.state = state;
    }

    public void doAction() {
        state.doAction(this);
    }
}

public class Main {
    public static void main(String[] args) {
        Context context = new Context();

        context.doAction(); // 執行狀態1的操作
        context.doAction(); // 執行狀態2的操作
        context.doAction(); // 執行狀態1的操作
    }
}
```

在這個範例中，我們有兩個具體狀態，即\*\*`State1`**和**`State2`**，每個狀態實現了抽象狀態接口中的**`doAction`**方法，並根據需要切換到另一個狀態。上下文對象**`Context`**包含一個對當前狀態的引用，並提供了一個**`doAction`\*\*方法，用於執行當前狀態的操作。

當客戶端使用上下文對象執行操作時，上下文根據當前狀態執行相對應的操作。然後，根據操作的結果，上下文可以切換到不同的狀態，並執行下一個操作。這樣，不同狀態下的操作行為被有效地封裝在狀態類別中，使得代碼更具可維護性和擴展性。狀態模式尤其適用於當對象有多個狀態且其行為隨狀態改變時的情況。
