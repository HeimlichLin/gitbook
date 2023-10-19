---
description: >-
  訪問者模式（Visitor
  Pattern）是一種行為型設計模式，它用於將算法與對象結構分離，以便可以為對象結構中的每個元素定義不同的操作，而不需要更改這些元素的類別。這種模式的主要目的是實現在不修改元素類別的情況下，對元素進行新的操作。
---

# 訪問者模式（Visitor Pattern）

訪問者模式通常包括以下角色：

1. 訪問者（Visitor）：定義了一系列可以訪問不同元素的訪問方法。每個訪問方法接受一個元素作為參數，並執行特定的操作。
2. 具體訪問者（Concrete Visitor）：實現了訪問者接口，並實現對元素的具體訪問方法。每個具體訪問者定義了不同的操作，可以應用於元素。
3. 元素（Element）：定義了接受訪問者訪問的接口。通常包括一個accept方法，該方法接受一個訪問者作為參數，並調用訪問者的訪問方法。
4. 具體元素（Concrete Element）：實現了元素接口，並實現accept方法。具體元素允許訪問者訪問自己，並調用適當的訪問方法。
5. 對象結構（Object Structure）：包含一個集合或結構，可以存儲不同類型的元素。對象結構允許訪問者遍歷其中的元素並執行操作。

以下是一個使用JAVA語言的簡單範例，說明訪問者模式：

```java
// 訪問者接口
interface Visitor {
    void visit(ElementA element);
    void visit(ElementB element);
}

// 具體訪問者A
class ConcreteVisitorA implements Visitor {
    @Override
    public void visit(ElementA element) {
        System.out.println("具體訪問者A訪問了元素A，執行操作A");
    }

    @Override
    public void visit(ElementB element) {
        System.out.println("具體訪問者A訪問了元素B，執行操作B");
    }
}

// 具體訪問者B
class ConcreteVisitorB implements Visitor {
    @Override
    public void visit(ElementA element) {
        System.out.println("具體訪問者B訪問了元素A，執行操作C");
    }

    @Override
    public void visit(ElementB element) {
        System.out.println("具體訪問者B訪問了元素B，執行操作D");
    }
}

// 元素接口
interface Element {
    void accept(Visitor visitor);
}

// 具體元素A
class ElementA implements Element {
    @Override
    public void accept(Visitor visitor) {
        visitor.visit(this);
    }

    public void operationA() {
        System.out.println("元素A執行操作A");
    }
}

// 具體元素B
class ElementB implements Element {
    @Override
    public void accept(Visitor visitor) {
        visitor.visit(this);
    }

    public void operationB() {
        System.out.println("元素B執行操作B");
    }
}

// 對象結構
class ObjectStructure {
    private List<Element> elements = new ArrayList<>();

    public void addElement(Element element) {
        elements.add(element);
    }

    public void removeElement(Element element) {
        elements.remove(element);
    }

    public void accept(Visitor visitor) {
        for (Element element : elements) {
            element.accept(visitor);
        }
    }
}

public class Main {
    public static void main(String[] args) {
        ObjectStructure objectStructure = new ObjectStructure();
        Element elementA = new ElementA();
        Element elementB = new ElementB();

        objectStructure.addElement(elementA);
        objectStructure.addElement(elementB);

        Visitor visitorA = new ConcreteVisitorA();
        Visitor visitorB = new ConcreteVisitorB();

        objectStructure.accept(visitorA);
        objectStructure.accept(visitorB);
    }
}
```

在這個範例中，我們有兩個具體訪問者（ConcreteVisitorA和ConcreteVisitorB），兩個具體元素（ElementA和ElementB），以及一個對象結構（ObjectStructure）。訪問者訪問元素，並執行不同的操作，而不需要修改元素的類別。通過訪問者模式，我們實現了算法和元素的分離，並提供了一個靈活的方式來擴展操作，而不會影響元素的結構。這種模式在訪問大型對象結構並且需要執行多個不同操作時特別有用。
