---
description: >-
  外觀模式（Facade
  Pattern）是一種結構型設計模式，它提供一個統一的接口，用於訪問子系統中的一群介面，以簡化客戶端的使用。外觀模式的目的是將複雜的子系統或類別庫封裝起來，提供一個簡單的介面，同時隱藏了子系統的複雜性，讓客戶端更容易使用。
---

# 外觀模式（Facade Pattern）

外觀模式通常包括以下角色：

1. 外觀（Facade）：提供統一的介面，用於訪問子系統的功能。外觀通常將客戶端的請求轉發給適當的子系統對象。
2. 子系統（Subsystems）：包含一群相關的類別，負責執行具體的功能。這些子系統的細節被外觀所隱藏，只有外觀可以訪問它們。

以下是一個使用JAVA語言的簡單範例，說明外觀模式：

```java
// 子系統1
class CPU {
    public void start() {
        System.out.println("CPU 開始運行");
    }
}

// 子系統2
class Memory {
    public void load() {
        System.out.println("記憶體正在載入");
    }
}

// 子系統3
class HardDrive {
    public void readData() {
        System.out.println("硬碟正在讀取數據");
    }
}

// 外觀
class ComputerFacade {
    private CPU cpu;
    private Memory memory;
    private HardDrive hardDrive;

    public ComputerFacade() {
        this.cpu = new CPU();
        this.memory = new Memory();
        this.hardDrive = new HardDrive();
    }

    public void startComputer() {
        System.out.println("正在啟動電腦...");
        cpu.start();
        memory.load();
        hardDrive.readData();
        System.out.println("電腦已經啟動完成！");
    }
}

public class Main {
    public static void main(String[] args) {
        ComputerFacade computer = new ComputerFacade();
        computer.startComputer();
    }
}
```

在這個範例中，我們有三個子系統，分別是\*\*`CPU`**、**`Memory`**和**`HardDrive`**，它們分別負責電腦的不同功能。然後我們引入了一個外觀**`ComputerFacade`**，它將這些子系統的細節隱藏起來，提供了一個簡單的**`startComputer`\*\*方法，用於啟動電腦。

客戶端代碼只需要使用\*\*`ComputerFacade`\*\*來啟動電腦，而不需要了解電腦啟動的細節。外觀模式有助於降低系統的複雜性，提供一個更容易使用的介面，同時隱藏了子系統的實現細節。這種方式提高了代碼的可維護性和可讀性，並簡化了客戶端的操作。
