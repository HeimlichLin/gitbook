---
description: >-
  責任鏈模式（Chain of Responsibility
  Pattern）是一種行為型設計模式，它用於處理請求的分發。這種模式通常涉及一系列處理者（Handler），每個處理者都負責處理特定類型的請求，並在必要時將請求傳遞給下一個處理者。這樣形成了一個責任鏈，請求沿著鏈傳遞，直到某個處理者能夠處理它為止。
---

# 責任鏈模式（Chain of Responsibility Pattern）

責任鏈模式通常包括以下角色：

1. 抽象處理者（Handler）：定義了處理請求的接口，並包含一個指向下一個處理者的引用。處理者可以決定是否處理請求，也可以將請求傳遞給下一個處理者。
2. 具體處理者（Concrete Handler）：實現了處理請求的具體類別。每個具體處理者負責處理特定類型的請求，並在必要時將請求傳遞給下一個處理者。

以下是一個使用JAVA語言的簡單範例，說明責任鏈模式：

```java
// 抽象處理者
abstract class Handler {
    private Handler nextHandler;

    public void setNextHandler(Handler handler) {
        this.nextHandler = handler;
    }

    public void handleRequest(Request request) {
        if (canHandle(request)) {
            processRequest(request);
        } else if (nextHandler != null) {
            nextHandler.handleRequest(request);
        } else {
            System.out.println("無法處理請求：" + request.getDescription());
        }
    }

    protected abstract boolean canHandle(Request request);

    protected abstract void processRequest(Request request);
}

// 具體處理者1
class ConcreteHandler1 extends Handler {
    @Override
    protected boolean canHandle(Request request) {
        return request.getType() == RequestType.TYPE1;
    }

    @Override
    protected void processRequest(Request request) {
        System.out.println("處理請求：" + request.getDescription());
    }
}

// 具體處理者2
class ConcreteHandler2 extends Handler {
    @Override
    protected boolean canHandle(Request request) {
        return request.getType() == RequestType.TYPE2;
    }

    @Override
    protected void processRequest(Request request) {
        System.out.println("處理請求：" + request.getDescription());
    }
}

// 請求類別
class Request {
    private RequestType type;
    private String description;

    public Request(RequestType type, String description) {
        this.type = type;
        this.description = description;
    }

    public RequestType getType() {
        return type;
    }

    public String getDescription() {
        return description;
    }
}

// 請求類型
enum RequestType {
    TYPE1, TYPE2
}

public class Main {
    public static void main(String[] args) {
        // 創建具體處理者
        Handler handler1 = new ConcreteHandler1();
        Handler handler2 = new ConcreteHandler2();

        // 建立處理者鏈
        handler1.setNextHandler(handler2);

        // 創建請求
        Request request1 = new Request(RequestType.TYPE1, "處理類型1的請求");
        Request request2 = new Request(RequestType.TYPE2, "處理類型2的請求");

        // 處理請求
        handler1.handleRequest(request1);
        handler1.handleRequest(request2);
    }
}
```

在這個範例中，我們有兩個具體處理者（**`ConcreteHandler1`和`ConcreteHandler2`**），每個處理特定類型的請求。我們建立了一個處理者鏈，其中\*\*`handler1`**處理類型1的請求，**`handler2`\*\*處理類型2的請求。

當客戶端創建請求並將其傳遞給\*\*`handler1`\*\*時，該處理者會檢查請求類型並決定是否處理該請求。如果不是它能處理的類型，則將請求傳遞給下一個處理者。這樣，請求將沿著處理者鏈進行處理，直到找到能夠處理它的處理者或者無法處理時終止。這種方式使得可以輕鬆添加、刪除或調整處理者，並且讓客戶端不需要知道所有處理者的細節，實現了解耦。
