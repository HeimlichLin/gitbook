---
description: >-
  適配器模式（Adapter
  Pattern）是一種結構型設計模式，它允許不相容的接口能夠協同工作。這種模式通常用於兩個不同接口的對象需要互相合作，但它們的接口不匹配。適配器模式通過引入一個適配器來使這些對象能夠協同工作，而無需改變它們的原始接口。
---

# 適配器模式（Adapter Pattern）

適配器模式通常包括以下角色：

1. 目標介面（Target Interface）：客戶端期望與之互動的接口。
2. 具體目標類別（Concrete Target Class）：實現了目標介面的具體類別。
3. 適配器（Adapter）：實現了目標介面，同時包含一個對不相容接口的引用。適配器將不相容的接口轉換為目標介面，使得兩者能夠協同工作。
4. 被適配者（Adaptee）：具有不相容接口的類別，需要被適配成目標介面。

以下是一個使用JAVA語言的簡單範例，說明適配器模式：

```java
// 目標介面
interface MediaPlayer {
    void play(String audioType, String fileName);
}

// 具體目標類別
class AudioPlayer implements MediaPlayer {
    @Override
    public void play(String audioType, String fileName) {
        if (audioType.equalsIgnoreCase("mp3")) {
            System.out.println("播放MP3音樂：" + fileName);
        } else if (audioType.equalsIgnoreCase("vlc") || audioType.equalsIgnoreCase("mp4")) {
            MediaAdapter mediaAdapter = new MediaAdapter(audioType);
            mediaAdapter.play(audioType, fileName);
        } else {
            System.out.println("不支援的媒體格式：" + audioType);
        }
    }
}

// 被適配者
class VlcPlayer {
    public void playVlc(String fileName) {
        System.out.println("播放VLC音樂：" + fileName);
    }
}

class Mp4Player {
    public void playMp4(String fileName) {
        System.out.println("播放MP4音樂：" + fileName);
    }
}

// 適配器
class MediaAdapter implements MediaPlayer {
    private VlcPlayer vlcPlayer;
    private Mp4Player mp4Player;

    public MediaAdapter(String audioType) {
        if (audioType.equalsIgnoreCase("vlc")) {
            vlcPlayer = new VlcPlayer();
        } else if (audioType.equalsIgnoreCase("mp4")) {
            mp4Player = new Mp4Player();
        }
    }

    @Override
    public void play(String audioType, String fileName) {
        if (audioType.equalsIgnoreCase("vlc")) {
            vlcPlayer.playVlc(fileName);
        } else if (audioType.equalsIgnoreCase("mp4")) {
            mp4Player.playMp4(fileName);
        }
    }
}

public class Main {
    public static void main(String[] args) {
        MediaPlayer audioPlayer = new AudioPlayer();

        audioPlayer.play("mp3", "song.mp3");
        audioPlayer.play("vlc", "video.vlc");
        audioPlayer.play("mp4", "video.mp4");
        audioPlayer.play("avi", "video.avi"); // 不支援的格式
    }
}
```

在這個範例中，我們有一個目標介面\*\*`MediaPlayer`**，以及一個具體目標類別**`AudioPlayer`**，它實現了目標介面。**`VlcPlayer`**和**`Mp4Player`\*\*是兩個具有不相容接口的被適配者。

\*\*`MediaAdapter`**是適配器，它實現了**`MediaPlayer`**介面，同時包含了**`VlcPlayer`**和**`Mp4Player`\*\*的引用，並將它們的接口轉換成目標介面。

客戶端代碼使用\*\*`AudioPlayer`\*\*來播放不同格式的音樂，適配器模式使得不同格式的音樂可以協同工作，而不需要改變原始類別的接口。這提供了更好的可擴展性和互換性。
