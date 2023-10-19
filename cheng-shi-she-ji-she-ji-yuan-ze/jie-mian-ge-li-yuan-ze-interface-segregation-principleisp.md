---
description: >-
  介面隔離原則（Interface Segregation
  Principle，簡稱ISP）是SOLID原則之一，它強調應該將一個大接口（介面）分割成多個小接口，以使客戶端不應該被強迫依賴它們不使用的方法。ISP的目的是保持接口的精簡性，提高代碼的可維護性、可讀性，同時減少不必要的依賴關係。
---

# 介面隔離原則（Interface Segregation Principle，ISP）

ISP的關鍵思想可以總結為以下幾點：

1. 用戶（客戶端）不應該被迫依賴它們不使用的接口方法。
2. 接口應該足夠小，每個接口應該只包含用戶需要的方法。
3. 接口的設計應該基於用戶的需求，而不是基於實現者的需求。

以下是一個使用JAVA語言的簡單範例，說明介面隔離原則：

```java
// 不符合ISP的接口設計
interface Worker {
    void work();
    void eat();
}

class SuperWorker implements Worker {
    @Override
    public void work() {
        // 執行工作
    }

    @Override
    public void eat() {
        // 吃午餐
    }
}

class NormalWorker implements Worker {
    @Override
    public void work() {
        // 執行工作
    }

    @Override
    public void eat() {
        // 吃午餐
    }
}

// 符合ISP的接口設計
interface Workable {
    void work();
}

interface Eatable {
    void eat();
}

class SuperWorker implements Workable, Eatable {
    @Override
    public void work() {
        // 執行工作
    }

    @Override
    public void eat() {
        // 吃午餐
    }
}

class NormalWorker implements Workable {
    @Override
    public void work() {
        // 執行工作
    }
}
```

在不符合ISP的示例中，\*\*`Worker`**接口包含了**`work`**和**`eat`**方法，這導致**`SuperWorker`**和**`NormalWorker`**兩個實現者必須實現**`eat`\*\*方法，即使有些工作者不需要這個方法。

在符合ISP的示例中，我們將\*\*`Worker`**接口分割為兩個小接口**`Workable`**和**`Eatable`**，每個接口只包含用戶需要的方法。這樣，**`SuperWorker`**實現了兩個接口，而**`NormalWorker`**只實現了**`Workable`\*\*接口，從而減少了不必要的依賴關係。

符合ISP的接口設計使代碼更容易理解，並確保每個類別只依賴它們需要的方法，從而提高代碼的可讀性和可維護性。這也有助于减少對不需要的方法的實現，提高代碼的復用性。
