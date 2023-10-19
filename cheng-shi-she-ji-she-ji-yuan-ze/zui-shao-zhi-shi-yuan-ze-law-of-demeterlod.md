---
description: >-
  最少知識原則（Law of
  Demeter，簡稱LoD）是一個軟體設計原則，它強調一個對象（或模組）應該只與它直接合作的對象有關，不應該知道更多關於其他對象的細節。換句話說，一個對象應該限制對其他對象的交互，只與它的密切合作者（closest
  friends）進行交互。這有助於減少對象之間的依賴關係，提高代碼的模組性、可讀性和可維護性。
---

# 最少知識原則（Law of Demeter，LoD）

最少知識原則可以總結為以下幾點：

1. 一個對象應該只認識以下對象：
   * 自身
   * 直接合作對象（成員對象）
   * 通過參數傳遞給方法的對象
   * 通過對象的方法返回值得到的對象
2. 一個對象不應該認識以下對象：
   * 超出上述範圍的對象，尤其是全局對象
   * 任何對象的內部結構和細節

以下是一個使用JAVA語言的簡單範例，說明最少知識原則：

```java
// 不符合LoD的設計
class Person {
    private String name;

    public Person(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public void introduceYourself(Team team) {
        System.out.println("我叫" + name + "，我在" + team.getName() + "這個團隊工作。");
    }
}

class Team {
    private String name;

    public Team(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }
}

public class Main {
    public static void main(String[] args) {
        Person person = new Person("Alice");
        Team team = new Team("開發團隊");
        person.introduceYourself(team);
    }
}
```

在這個不符合LoD的示例中，\*\*`Person`**類別的**`introduceYourself`**方法需要知道**`Team`**類別的細節，包括如何獲得團隊的名稱。這導致**`Person`**類別對**`Team`**類別有過多的依賴，並且可能需要了解**`Team`\*\*類別的內部結構。

下面是一個符合LoD的示例：

```java
// 符合LoD的設計
class Person {
    private String name;

    public Person(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public void introduceYourself() {
        System.out.println("我叫" + name + "，我在這個團隊工作。");
    }
}

class Team {
    public String getName() {
        return "開發團隊";
    }
}

public class Main {
    public static void main(String[] args) {
        Person person = new Person("Alice");
        person.introduceYourself();
    }
}
```

在這個符合LoD的示例中，Person類別的introduceYourself方法不再需要知道Team類別的細節。它僅使用自身的信息來介紹自己。這樣，我們減少了對其他對象的依賴，提高了代碼的模組性和可維護性。最少知識原則有助於保持對象之間的鬆散耦合，從而使代碼更容易擴展和維護。
