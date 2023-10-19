---
description: >-
  解釋器模式（Interpreter
  Pattern）是一種行為型設計模式，它用於定義一種語言的文法規則，並提供一個解釋器，用於解釋語言中的句子或表達式。這種模式通常用於處理語言解釋、編譯器、正則表達式解析等場景。
---

# 解釋器模式（Interpreter Pattern）

解釋器模式通常包括以下角色：

1. 抽象表達式（Abstract Expression）：定義了一個解釋操作的接口，通常包括interpret方法，該方法用於解釋語言中的句子或表達式。
2. 具體表達式（Concrete Expression）：實現了抽象表達式的接口，並提供了實際的解釋邏輯。每個具體表達式對應語言中的一個文法規則。
3. 上下文（Context）：包含解釋器所需的全局信息，通常用於存儲變數、符號表等，並提供一個方法用於解釋句子或表達式。
4. 解釋器（Interpreter）：用於解釋句子或表達式，它通常包括一個interpret方法，該方法接受一個上下文對象，並根據文法規則解釋語言中的句子或表達式。

以下是一個使用JAVA語言的簡單範例，說明解釋器模式：

```java
// 抽象表達式
interface Expression {
    int interpret(Context context);
}

// 具體表達式
class TerminalExpression implements Expression {
    private String data;

    public TerminalExpression(String data) {
        this.data = data;
    }

    @Override
    public int interpret(Context context) {
        return context.lookup(data);
    }
}

class NonTerminalExpression implements Expression {
    private Expression expression1;
    private Expression expression2;

    public NonTerminalExpression(Expression expression1, Expression expression2) {
        this.expression1 = expression1;
        this.expression2 = expression2;
    }

    @Override
    public int interpret(Context context) {
        return expression1.interpret(context) + expression2.interpret(context);
    }
}

// 上下文
class Context {
    private String[] variables;

    public Context() {
        variables = new String[] { "a", "b", "c" };
    }

    public int lookup(String variable) {
        for (int i = 0; i < variables.length; i++) {
            if (variables[i].equals(variable)) {
                return i + 1; // 返回變數位置的值
            }
        }
        return 0; // 如果變數不存在，返回0
    }
}

public class Main {
    public static void main(String[] args) {
        Context context = new Context();

        Expression a = new TerminalExpression("a");
        Expression b = new TerminalExpression("b");
        Expression c = new TerminalExpression("c");

        Expression expression = new NonTerminalExpression(a, new NonTerminalExpression(b, c));

        int result = expression.interpret(context);
        System.out.println("解釋結果：" + result);
    }
}
```

在這個範例中，我們有抽象表達式（**`Expression`**）接口，其中包括\*\*`interpret`**方法，用於解釋表達式。我們有兩種具體表達式，一個是**`TerminalExpression`**，它代表變數，另一個是**`NonTerminalExpression`**，它代表表達式的加法操作。上下文（**`Context`\*\*）包含變數和其值，並用於查找變數的值。

在主程序中，我們創建了一個複雜的表達式，然後使用上下文和解釋器來解釋這個表達式，最終得到結果。這個範例演示了如何使用解釋器模式來解釋表達式，以及如何定義不同的具體表達式來處理不同的文法規則。
