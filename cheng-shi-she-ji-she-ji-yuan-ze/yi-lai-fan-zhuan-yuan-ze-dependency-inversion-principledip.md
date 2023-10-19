---
description: >-
  依賴反轉原則（Dependency Inversion
  Principle，縮寫為DIP）是面向物件設計中的一個SOLID原則，它強調高層次模組不應該依賴於低層次模組，兩者都應該依賴於抽象。換句話說，DIP提倡程式碼應該針對接口或抽象類別進行編程，而不是針對具體實現進行編程。
---

# 依賴反轉原則（Dependency Inversion Principle，DIP）

DIP主要觀點如下：

1. 高層次模組不應該依賴於低層次模組。兩者都應該依賴於抽象。高層次模組指的是應用程序的主要邏輯，而低層次模組是支持高層次模組的實現細節。
2. 抽象不應該依賴於細節，細節應該依賴於抽象。這意味著抽象類別或接口定義了一個合同，而具體實現必須遵循這個合同。
3. DIP有助於降低代碼的耦合性，提高代碼的可維護性和可擴展性。

以下是一個使用JAVA語言的簡單範例，說明依賴反轉原則：

```java
// 定義抽象的開關介面
interface Switchable {
    void turnOn();
    void turnOff();
}

// 具體的燈泡類別實現開關介面
class LightBulb implements Switchable {
    @Override
    public void turnOn() {
        System.out.println("燈泡已打開");
    }

    @Override
    public void turnOff() {
        System.out.println("燈泡已關閉");
    }
}

// 具體的風扇類別實現開關介面
class Fan implements Switchable {
    @Override
    public void turnOn() {
        System.out.println("風扇已打開");
    }

    @Override
    public void turnOff() {
        System.out.println("風扇已關閉");
    }
}

// 高層次模組，接受開關介面依賴
class RemoteControl {
    private Switchable device;

    public RemoteControl(Switchable device) {
        this.device = device;
    }

    public void turnOn() {
        device.turnOn();
    }

    public void turnOff() {
        device.turnOff();
    }
}

public class Main {
    public static void main(String[] args) {
        Switchable bulb = new LightBulb();
        Switchable fan = new Fan();

        RemoteControl remote1 = new RemoteControl(bulb);
        RemoteControl remote2 = new RemoteControl(fan);

        remote1.turnOn();
        remote1.turnOff();

        remote2.turnOn();
        remote2.turnOff();
    }
}
```

在這個範例中，我們定義了抽象的開關介面\*\*`Switchable`**，它包含了**`turnOn`**和**`turnOff`**方法。然後，我們實作了兩個具體的類別**`LightBulb`**和**`Fan`**，它們都實現了**`Switchable`\*\*介面。

高層次模組\*\*`RemoteControl`**不依賴於具體的**`LightBulb`**或**`Fan`**類別，而是依賴於**`Switchable`\*\*介面。這遵循了DIP原則，高層次模組和低層次模組都依賴於抽象。

這使得我們可以輕鬆地擴展應用程序，例如，添加新的開關設備，而不需要修改\*\*`RemoteControl`\*\*類別，這符合依賴反轉原則的要求。
