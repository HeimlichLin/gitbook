---
description: >-
  備忘錄模式（Memento
  Pattern）是一種行為型設計模式，它用於捕獲和存儲對象的內部狀態，以便稍後可以恢復到先前的狀態。這種模式通常在需要實現撤銷、重做或保存對象狀態的情況下使用。備忘錄模式分離了對象的狀態管理，使得對象的狀態可以被安全地保存和還原，同時保持封裝性。
---

# 備忘錄模式（Memento Pattern）

備忘錄模式通常包括以下角色：

1. 發起人（Originator）：它是需要保存和恢復狀態的對象。發起人創建備忘錄，並可以使用備忘錄來還原其內部狀態。
2. 備忘錄（Memento）：備忘錄是用來保存發起人的內部狀態的對象。備忘錄通常包含狀態的快照。
3. 管理者（Caretaker）：它是負責保存和恢復備忘錄的對象。管理者不知道備忘錄的具體內容，它只負責保存和返回備忘錄。

以下是一個使用JAVA語言的簡單範例，說明備忘錄模式：

```java
import java.util.ArrayList;
import java.util.List;

// 備忘錄
class Memento {
    private String state;

    public Memento(String state) {
        this.state = state;
    }

    public String getState() {
        return state;
    }
}

// 發起人
class Originator {
    private String state;

    public void setState(String state) {
        this.state = state;
    }

    public String getState() {
        return state;
    }

    public Memento saveStateToMemento() {
        return new Memento(state);
    }

    public void getStateFromMemento(Memento memento) {
        state = memento.getState();
    }
}

// 管理者
class Caretaker {
    private List<Memento> mementoList = new ArrayList<>();

    public void addMemento(Memento memento) {
        mementoList.add(memento);
    }

    public Memento getMemento(int index) {
        return mementoList.get(index);
    }
}

public class Main {
    public static void main(String[] args) {
        Originator originator = new Originator();
        Caretaker caretaker = new Caretaker();

        originator.setState("狀態1");
        originator.setState("狀態2");
        caretaker.addMemento(originator.saveStateToMemento());

        originator.setState("狀態3");
        caretaker.addMemento(originator.saveStateToMemento());

        System.out.println("當前狀態：" + originator.getState());

        Memento memento = caretaker.getMemento(0);
        originator.getStateFromMemento(memento);
        System.out.println("還原後的狀態：" + originator.getState());

        memento = caretaker.getMemento(1);
        originator.getStateFromMemento(memento);
        System.out.println("再次還原後的狀態：" + originator.getState());
    }
}
```

在這個範例中，我們有一個發起人（**`Originator`**）對象，它可以設置和保存內部狀態，以及使用備忘錄來還原狀態。備忘錄（**`Memento`**）是保存狀態的對象，它包含了狀態的快照。管理者（**`Caretaker`**）負責保存和恢復備忘錄。

在主程序中，我們首先設置發起人的狀態，然後保存狀態到備忘錄中。然後，我們修改狀態，再次保存狀態到另一個備忘錄中。之後，我們可以使用備忘錄來還原狀態，使得發起人回到以前的狀態。

備忘錄模式有助於實現對象的撤銷和重做功能，同時保持了對象的封裝性，確保內部狀態不會被外部直接訪問或修改。
