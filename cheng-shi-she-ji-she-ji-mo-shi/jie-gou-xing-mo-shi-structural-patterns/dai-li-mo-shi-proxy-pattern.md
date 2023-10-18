---
description: >-
  代理模式（Proxy
  Pattern）是一種結構型設計模式，它提供了一個代理物件，允許代理控制對其他對象的訪問。代理通常用於實現延遲加載、訪問控制、日誌記錄、性能優化等功能。代理模式有助於實現對對象的間接訪問，同時保持對對象的控制。
---

# 代理模式（Proxy Pattern）

代理模式通常包括以下角色：

1. 主題（Subject）：定義了代理和真實對象的共同介面，這樣代理可以替代真實對象。
2. 真實主題（Real Subject）：實際執行工作的對象。代理通常將請求委派給真實主題。
3. 代理（Proxy）：保持對真實主題的引用，同時實現主題的介面。代理可以控制對真實主題的訪問，執行額外的操作，例如記錄日誌、檢查許可權等。

以下是一個使用JAVA語言的簡單範例，說明代理模式：

```java
// 主題（Subject）介面
interface Image {
    void display();
}

// 真實主題（Real Subject）類別
class RealImage implements Image {
    private String filename;

    public RealImage(String filename) {
        this.filename = filename;
        loadFromDisk();
    }

    private void loadFromDisk() {
        System.out.println("Loading image: " + filename);
    }

    @Override
    public void display() {
        System.out.println("Displaying image: " + filename);
    }
}

// 代理（Proxy）類別
class ProxyImage implements Image {
    private RealImage realImage;
    private String filename;

    public ProxyImage(String filename) {
        this.filename = filename;
    }

    @Override
    public void display() {
        if (realImage == null) {
            realImage = new RealImage(filename);
        }
        realImage.display();
    }
}

public class Main {
    public static void main(String[] args) {
        Image image1 = new ProxyImage("image1.jpg");
        Image image2 = new ProxyImage("image2.jpg");

        // 圖片1首次載入，顯示
        image1.display();
        // 圖片1再次顯示，無需再次載入
        image1.display();
        
        // 圖片2首次載入，顯示
        image2.display();
    }
}
```

在這個範例中，我們有一個主題介面\*\*`Image`**，其中定義了**`display`**方法。**`RealImage`**是真實主題，實現了**`Image`**介面，並負責載入和顯示圖片。**`ProxyImage`**是代理，同樣實現了**`Image`\*\*介面，它包含了對真實主題的引用，並在需要時創建和使用真實主題。代理模式確保了圖片只有在首次顯示時才被載入，減少了不必要的載入操作。

代理模式是一個實用的設計模式，可用於許多情況，如遠程代理、虛擬代理、保護代理等，以實現不同的功能，同時保持對對象的控制和訪問。
