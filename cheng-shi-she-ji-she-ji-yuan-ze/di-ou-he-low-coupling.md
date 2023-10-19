---
description: >-
  低耦合（Low
  Coupling）是軟體工程中的一個設計原則，它指的是模組或類別之間的相互依賴應該盡量減少。低耦合的設計有助於提高代碼的可維護性、可擴展性、可讀性和重用性。當模組之間耦合較低時，它們更容易獨立開發、測試和修改，並且變更一個模組不太可能影響其他模組。
---

# 低耦合（Low Coupling）

低耦合的設計原則可以通過以下方法實珸：

1. 使用介面（Interface）：使用介面來定義模組之間的合同，而不是直接依賴具體類別。這樣，當需要更改實現時，只需更改具體類別，而不影響依賴它的其他模組。
2. 依賴注入（Dependency Injection）：通過依賴注入將依賴關係的建立移到外部，模組只需要關心它的功能，而不需要擔心如何獲取依賴的實例。
3. 使用中介者（Mediator）模式：中介者模式可以減少模組之間的直接通信，將通信集中到中介者，降低了模組之間的耦合度。

以下是一個使用JAVA語言的簡單範例，說明低耦合的設計：

```java
// 低耦合的示例

// 介面定義
interface MessageService {
    void sendMessage(String message);
}

// 實現介面的具體類別
class EmailService implements MessageService {
    @Override
    public void sendMessage(String message) {
        System.out.println("發送郵件: " + message);
    }
}

class SMSService implements MessageService {
    @Override
    public void sendMessage(String message) {
        System.out.println("發送短信: " + message);
    }
}

// 類別之間的低耦合
class NotificationService {
    private MessageService messageService;

    public NotificationService(MessageService messageService) {
        this.messageService = messageService;
    }

    public void sendNotification(String message) {
        messageService.sendMessage(message);
    }
}

public class Main {
    public static void main(String[] args) {
        MessageService emailService = new EmailService();
        NotificationService emailNotification = new NotificationService(emailService);

        MessageService smsService = new SMSService();
        NotificationService smsNotification = new NotificationService(smsService);

        emailNotification.sendNotification("這是一封郵件通知");
        smsNotification.sendNotification("這是一條短信通知");
    }
}
```

在這個示例中，我們定義了一個MessageService介面，並實現了兩個具體的類別EmailService和SMSService，它們分別負責發送郵件和短信通知。NotificationService是一個通知服務，它依賴MessageService介面。通過使用介面和依賴注入，我們實現了低耦合，NotificationService不需要知道具體的通知方式，只需要關心如何使用MessageService來發送通知。這樣的設計使代碼易於維護和擴展，並且減少了模組之間的耦合度。
