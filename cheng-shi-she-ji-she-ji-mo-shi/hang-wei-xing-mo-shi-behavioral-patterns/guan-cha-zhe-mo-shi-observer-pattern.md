---
description: >-
  觀察者模式（Observer
  Pattern）是一種行為型設計模式，它定義了一個一對多的關係，讓一個主題（或主題對象）狀態的改變能夠通知並自動通知所有依賴於該主題的觀察者（或訂閱者）。觀察者模式用於實現松耦合，當主題的狀態發生變化時，它的所有觀察者都會自動接收通知並執行相應的操作。
---

# 觀察者模式（Observer Pattern）

觀察者模式主要包含以下角色：

1. 主題（Subject）：也稱為被觀察者，負責維護一個觀察者清單，並通知觀察者當前狀態的改變。
2. 觀察者（Observer）：定義一個更新操作，用於在主題的狀態發生改變時接收通知並執行相應操作。
3. 具體主題（Concrete Subject）：實作主題介面，維護一個觀察者清單，並在狀態改變時通知觀察者。
4. 具體觀察者（Concrete Observer）：實作觀察者介面，接收主題的通知並執行相應的操作。

以下是一個使用JAVA語言的簡單範例，說明觀察者模式：

```java
import java.util.ArrayList;
import java.util.List;

// 主題（被觀察者）介面
interface Subject {
    void registerObserver(Observer observer);
    void removeObserver(Observer observer);
    void notifyObservers();
}

// 觀察者介面
interface Observer {
    void update(String message);
}

// 具體主題
class ConcreteSubject implements Subject {
    private List<Observer> observers = new ArrayList<>();
    private String message;

    @Override
    public void registerObserver(Observer observer) {
        observers.add(observer);
    }

    @Override
    public void removeObserver(Observer observer) {
        observers.remove(observer);
    }

    @Override
    public void notifyObservers() {
        for (Observer observer : observers) {
            observer.update(message);
        }
    }

    public void setMessage(String message) {
        this.message = message;
        notifyObservers();
    }
}

// 具體觀察者
class ConcreteObserver implements Observer {
    private String name;

    public ConcreteObserver(String name) {
        this.name = name;
    }

    @Override
    public void update(String message) {
        System.out.println(name + " 收到訊息: " + message);
    }
}

public class Main {
    public static void main(String[] args) {
        ConcreteSubject subject = new ConcreteSubject();

        Observer observer1 = new ConcreteObserver("觀察者1");
        Observer observer2 = new ConcreteObserver("觀察者2");

        subject.registerObserver(observer1);
        subject.registerObserver(observer2);

        subject.setMessage("新訊息來了!");

        subject.removeObserver(observer2);

        subject.setMessage("另一則新訊息");
    }
}
```

在這個範例中，我們定義了主題介面\*\*`Subject`**和觀察者介面**`Observer`**。然後，我們實作了具體主題**`ConcreteSubject`**和具體觀察者**`ConcreteObserver`\*\*。

主題負責維護觀察者清單，當主題的狀態發生變化時，它會通知所有註冊的觀察者。觀察者則負責接收通知並執行相應的操作。

在客戶端代碼中，我們創建了主題對象並註冊了兩個觀察者。當主題的狀態改變時，所有觀察者都會接收到通知並執行\*\*`update`\*\*方法，這樣我們實現了觀察者模式。觀察者模式有助於實現事件處理和松耦合的設計。
