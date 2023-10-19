---
description: >-
  中介者模式（Mediator
  Pattern）是一種行為型設計模式，它用於減少對象之間的直接通信，並將其集中在一個中介對象上。這種模式的主要目的是減少對象之間的耦合，並提供一個中心化的方式來協調和管理對象之間的交互。
---

# 中介者模式（Mediator Pattern）

中介者模式通常包括以下角色：

1. 中介者（Mediator）：定義一個接口，用於定義對象之間通信的方法。中介者知道所有參與的對象，並負責協調它們之間的互動。
2. 具體中介者（Concrete Mediator）：實現中介者接口，並負責協調和管理參與的對象之間的通信。具體中介者通常包含對參與對象的引用。
3. 參與對象（Colleague）：代表參與通信的對象。這些對象知道中介者並通過中介者進行通信，而不是直接與其他對象通信。

中介者模式的主要優勢是減少了對象之間的相互關聯性，使得對象可以更容易地被添加、刪除或替換，並且有助於簡化對象之間的通信。這種模式特別適用於需要協調多個對象之間互動的情況，以確保系統保持清晰、可維護和可擴展。

以下是一個使用JAVA語言的簡單範例，說明中介者模式：

```java
// 中介者接口
interface Mediator {
    void send(String message, Colleague colleague);
}

// 具體中介者
class ConcreteMediator implements Mediator {
    private Colleague colleague1;
    private Colleague colleague2;

    public void setColleague1(Colleague colleague1) {
        this.colleague1 = colleague1;
    }

    public void setColleague2(Colleague colleague2) {
        this.colleague2 = colleague2;
    }

    @Override
    public void send(String message, Colleague colleague) {
        if (colleague == colleague1) {
            colleague2.receive(message);
        } else if (colleague == colleague2) {
            colleague1.receive(message);
        }
    }
}

// 參與對象
abstract class Colleague {
    private Mediator mediator;

    public Colleague(Mediator mediator) {
        this.mediator = mediator;
    }

    public void send(String message) {
        mediator.send(message, this);
    }

    public abstract void receive(String message);
}

class ConcreteColleague1 extends Colleague {
    public ConcreteColleague1(Mediator mediator) {
        super(mediator);
    }

    @Override
    public void receive(String message) {
        System.out.println("同事1收到訊息：" + message);
    }
}

class ConcreteColleague2 extends Colleague {
    public ConcreteColleague2(Mediator mediator) {
        super(mediator);
    }

    @Override
    public void receive(String message) {
        System.out.println("同事2收到訊息：" + message);
    }
}

public class Main {
    public static void main(String[] args) {
        ConcreteMediator mediator = new ConcreteMediator();

        ConcreteColleague1 colleague1 = new ConcreteColleague1(mediator);
        ConcreteColleague2 colleague2 = new ConcreteColleague2(mediator);

        mediator.setColleague1(colleague1);
        mediator.setColleague2(colleague2);

        colleague1.send("Hello, 同事2!");
        colleague2.send("Hi, 同事1!");
    }
}
```

在這個範例中，我們有一個具體中介者（**`ConcreteMediator`**）和兩個參與對象（**`ConcreteColleague1`和`ConcreteColleague2`**）。中介者負責協調這兩個參與對象之間的通信。當參與對象發送訊息時，它們並不直接通信，而是通過中介者進行通信，中介者負責將訊息傳遞給正確的接收者。

這種方式可以減少對象之間的直接關聯，並且當需要添加更多參與對象時，不需要修改現有的對象。中介者模式將通信的細節封裝在中介者中，提高了系統的可維護性和擴展性。
