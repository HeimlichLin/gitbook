---
description: >-
  命令模式（Command
  Pattern）是一種行為型設計模式，它旨在將請求或操作封裝為一個對象，從而可以參數化用戶端對請求的不同方式，排入佇列，或者支持可撤銷的操作。這種模式可以使客戶端和接收者（實際執行操作的對象）之間達到更佳的解耦，同時提供更多的靈活性和可擴展性。
---

# 命令模式（Command Pattern）

命令模式主要包括以下角色：

1. Command（命令）：定義了執行請求的介面，通常包括一個execute方法。
2. ConcreteCommand（具體命令）：實現了Command介面，並封裝了具體的請求和接收者。
3. Receiver（接收者）：執行實際操作的對象，可以是任何類別。
4. Invoker（調用者）：負責接收和執行命令的對象，它包含一個命令對象，可以設定不同的命令。

以下是一個使用JAVA語言的簡單範例，說明命令模式：

```java
// Command（命令）介面
interface Command {
    void execute();
}

// Receiver（接收者）類別
class Light {
    public void turnOn() {
        System.out.println("燈光已打開");
    }

    public void turnOff() {
        System.out.println("燈光已關閉");
    }
}

// ConcreteCommand（具體命令）類別
class TurnOnLightCommand implements Command {
    private Light light;

    public TurnOnLightCommand(Light light) {
        this.light = light;
    }

    @Override
    public void execute() {
        light.turnOn();
    }
}

class TurnOffLightCommand implements Command {
    private Light light;

    public TurnOffLightCommand(Light light) {
        this.light = light;
    }

    @Override
    public void execute() {
        light.turnOff();
    }
}

// Invoker（調用者）類別
class RemoteControl {
    private Command command;

    public void setCommand(Command command) {
        this.command = command;
    }

    public void pressButton() {
        command.execute();
    }
}

public class Main {
    public static void main(String[] args) {
        Light livingRoomLight = new Light();

        Command turnOnCommand = new TurnOnLightCommand(livingRoomLight);
        Command turnOffCommand = new TurnOffLightCommand(livingRoomLight);

        RemoteControl remote = new RemoteControl();

        remote.setCommand(turnOnCommand);
        remote.pressButton();

        remote.setCommand(turnOffCommand);
        remote.pressButton();
    }
}
```

在這個範例中，我們定義了命令介面\*\*`Command`**，並實作了兩個具體命令類別**`TurnOnLightCommand`**和**`TurnOffLightCommand`**，它們都實現了**`Command`\*\*介面並封裝了相應的操作。

\*\*`Light`\*\*是接收者，它實際執行開關燈的操作。

\*\*`RemoteControl`\*\*是調用者，它包含了一個命令對象，並在按下按鈕時執行該命令。客戶端代碼示範了如何使用命令模式，將開啟和關閉燈的命令封裝成對象，同時實現了命令的可配置性和可擴展性。這種方式使得客戶端代碼不需要關心實際的操作細節，同時能夠支持不同的命令。
