---
description: >-
  策略模式（Strategy
  Pattern）是一種行為型設計模式，它定義了一系列的算法，把它們封裝起來，並使它們可以互相替換。策略模式允許客戶端選擇要使用的算法，而不需要改變其結構。這種模式有助於使算法與客戶端代碼獨立，同時保持程式碼的可擴展性和可維護性。
---

# 策略模式（Strategy Pattern）

策略模式主要包括以下角色：

1. Context（上下文）：維護一個對策略介面的參考，並在需要時使用該策略對象來執行具體的操作。
2. Strategy（策略）：定義了一個共同的介面，所有具體策略類別都實現這個介面，並提供了不同的算法實現。
3. ConcreteStrategy（具體策略）：實現了策略介面，提供了特定的算法實現。

以下是一個使用JAVA語言的簡單範例，說明策略模式：

```java
// Strategy（策略）介面
interface PaymentStrategy {
    void pay(int amount);
}

// ConcreteStrategy（具體策略）類別
class CreditCardPayment implements PaymentStrategy {
    private String cardNumber;
    private String name;

    public CreditCardPayment(String cardNumber, String name) {
        this.cardNumber = cardNumber;
        this.name = name;
    }

    @Override
    public void pay(int amount) {
        System.out.println(amount + "元已使用信用卡支付，卡號：" + cardNumber + "，持卡人：" + name);
    }
}

class PayPalPayment implements PaymentStrategy {
    private String email;

    public PayPalPayment(String email) {
        this.email = email;
    }

    @Override
    public void pay(int amount) {
        System.out.println(amount + "元已使用PayPal支付，Email：" + email);
    }
}

// Context（上下文）類別
class ShoppingCart {
    private PaymentStrategy paymentStrategy;

    public void setPaymentStrategy(PaymentStrategy paymentStrategy) {
        this.paymentStrategy = paymentStrategy;
    }

    public void checkout(int amount) {
        paymentStrategy.pay(amount);
    }
}

public class Main {
    public static void main(String[] args) {
        ShoppingCart cart = new ShoppingCart();

        // 使用信用卡支付
        PaymentStrategy creditCard = new CreditCardPayment("1234-5678-9012-3456", "John Doe");
        cart.setPaymentStrategy(creditCard);
        cart.checkout(100);

        // 使用PayPal支付
        PaymentStrategy payPal = new PayPalPayment("john.doe@example.com");
        cart.setPaymentStrategy(payPal);
        cart.checkout(50);
    }
}
```

在這個範例中，我們定義了策略介面\*\*`PaymentStrategy`**，它包含了一個**`pay`**方法。然後，我們實作了兩個具體的策略類別**`CreditCardPayment`**和**`PayPalPayment`**，它們都實現了**`PaymentStrategy`\*\*介面並提供了不同的支付方式。

在\*\*`ShoppingCart`**類別中，我們設定了一個**`paymentStrategy`**屬性，客戶端可以使用**`setPaymentStrategy`**方法來設定支付策略。然後，在**`checkout`\*\*方法中，我們使用所選的策略來支付購物車中的金額。

客戶端代碼示範了如何使用策略模式，動態地選擇不同的支付方式，同時保持了\*\*`ShoppingCart`\*\*類別的不變。這使得程式碼更具靈活性，並有助於減少代碼中的條件分支。策略模式的核心思想是"分離變化"，使不同的算法實現可以獨立變化而不影響客戶端代碼。
