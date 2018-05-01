[（全体設計のくわしい説明）](design.md)

# Scratch 2.0 オフラインで使える音声対話ロボット／音声対話システム用ブロック

気軽に対話システムや対話ロボット，スマートスピーカーを作成するには，音声合成，音声認識，および電子回路（目が光る，頭が動く）を Scratch で使えるとよさそうです．それに，常にインターネットに接続できる環境にいるとは限らないので，すべてオフラインで行えるようにしたいところ．それを可能にするための Scratch ブロックを紹介します．

[<img alt="音声合成 s2speak" src="https://github.com/memakura/s2speak/raw/master/images/ScratchSpeechSynth.png" width="10%">](https://github.com/memakura/s2speak/wiki) [<img alt="音声認識 s2listen" src="https://github.com/memakura/s2listen/raw/master/images/ScratchSpeechRecog.png" width="10%">](https://github.com/memakura/s2listen/wiki) [<img alt="顔検出 s2face" src="https://github.com/memakura/s2face/raw/master/images/ScratchFace.png" width="10%">](https://github.com/memakura/s2face) [<img alt="Arduino s2aio" src="https://github.com/memakura/s2aio/raw/msi_installer/icons/ScratchArduino.png" width="10%">](https://github.com/memakura/s2aio/wiki) [<img alt="micro:bit s2microbit-ble" src="https://github.com/memakura/s2microbit-ble/raw/master/images/s2microbit-ble.png" width="10%">](https://memakura.github.io/s2microbit-ble/) 

（クリックするとそれぞれの解説ページへ）

必要な機能に応じて，必要な拡張ブロックを選んで追加します．それぞれインストーラを準備しています．対話ロボットや対話システムの[全体設計についてはこちらのページ](design.md)で詳しく説明します．

micro:bitの拡張ブロック s2microbit-ble は Windows10 や Mac OS X でも使えますが，他は今のところ Windowsのみです．（ただしそこまでOS依存性は強くないので，必要に応じてMac/Linux版などを用意する予定です．）


## 用意するもの

- [Scratch 2 (Offline)](https://scratch.mit.edu/download)
- 必要に応じて
    - マイク（音声認識をする場合．PC内臓のもので可）
    - カメラ（顔追跡をする場合．PC内臓のもので可）
    - Arduino や BBC micro:bit

## 各拡張ブロックの説明

### **s2speak (OpenJTalk)**

[<img src="https://github.com/memakura/s2speak/raw/master/images/ScratchSpeechSynth.png" width="128" align="top">](https://github.com/memakura/s2speak/wiki) [<img width="480" src="https://github.com/memakura/s2speak/raw/master/images/block_and_sample_JA.png" align="top">](https://github.com/memakura/s2speak/raw/master/images/block_and_sample_JA.png)

テキストを入力すると音声を合成します．
- [インストール方法と使用方法（アイコンからでも移動できます）](https://github.com/memakura/s2speak/wiki)
- OpejJtalkという音声合成を使っています．
- [デモプロジェクト(s2speak_demo.sb2)](https://github.com/memakura/s2speak/raw/master/00scratch/s2speak_demo.sb2)

### **s2listen (Julius)**

[<img src="https://github.com/memakura/s2listen/raw/master/images/ScratchSpeechRecog.png" width="128" align="top">](https://github.com/memakura/s2listen/wiki) [<img width="480" src="https://github.com/memakura/s2listen/raw/master/images/block_and_sample_JA.png" align="top">](https://github.com/memakura/s2listen/raw/master/images/block_and_sample_JA.png)

音声をテキストに変換します．
- [インストール方法と使用方法（アイコンからでも移動できます）](https://github.com/memakura/s2listen/wiki)
- Juliusという音声認識を使っています．
- 音声認識ではマイクの設定が重要になるため，[音声入力デバイス（マイク）の設定](https://github.com/memakura/s2listen/wiki/SetInputDevice) も参考にしてください．
- 簡単なブロックの説明
    - `聞こえた言葉` のブロックには，`聞こえるまで最大(...)秒待つ` のブロックが実行されて数秒間の認識結果が入ります．
    - `耳に入った言葉` には常に（連続的に）認識結果が入るので，「起きて」などのキーワードで何か始めるプログラムができます．
    - 品詞（名詞，動詞・・）への分解もおこないます．
- [デモプロジェクト(s2listen_demo.sb2)](https://github.com/memakura/s2listen/raw/master/00scratch/s2listen_demo.sb2)

### **s2face (OpenCV)**

[<img src="https://github.com/memakura/s2face/raw/master/images/ScratchFace.png" width="128" align="top">](https://github.com/memakura/s2face/wiki) [<img width="480" src="https://github.com/memakura/s2face/raw/master/images/block_and_sample_JA.png" align="top">](https://github.com/memakura/s2face/raw/master/images/block_and_sample_JA.png)

顔の位置と大きさを検出します．
- [インストール方法と使用方法（アイコンからでも移動できます）](https://github.com/memakura/s2face/wiki)
- 必要なディスクスペースが大きい(560-570MB)ので注意してください．
- [デモプロジェクト(s2face_demo.sb2)](https://github.com/memakura/s2listen/raw/master/00scratch/s2face_demo.sb2)

### **s2aio (Arduino)**

[<img src="https://github.com/memakura/s2aio/raw/msi_installer/icons/ScratchArduino.png" width="128" algin="top">](https://github.com/memakura/s2aio/wiki) [<img src="https://github.com/memakura/s2aio/wiki/block_and_sample_JA.png" align="top">](https://github.com/memakura/s2aio/wiki/block_and_sample_JA.png)

ArduinoをScratchから使うための[s2aio(MrYsLab)](https://github.com/MrYsLab/s2aio)をインストーラ版にしました．
- ブロックの日本語化も行っています．
- [インストール方法と使用方法（アイコンからでも移動できます）](https://github.com/memakura/s2aio/wiki)
- [デモプロジェクト(s2aio_demo.sb2)](https://github.com/memakura/s2aio/raw/msi_installer/00scratch/s2aio_demo.sb2)

### **s2microbit-ble**

[<img src="https://memakura.github.io/s2microbit-ble/images/s2microbit-ble.png" width="128" align="top">](https://memakura.github.io/s2microbit-ble/) [<img width="480" src="https://memakura.github.io/s2microbit-ble/images/blocks_v2.png" align="top">](https://memakura.github.io/s2microbit-ble/images/blocks_v2.png)

BBC micro:bit を Bluetooth (Low Energy) で使うことができます．（Windows10とMac OS Xに対応しています．）

電子回路だけでなくゲームコントローラなどいろいろなものを作成することができます．
- [インストール方法と使用方法（アイコンからでも移動できます）](https://memakura.github.io/s2microbit-ble/)
- [ブロックの使い方の詳細はこちら](https://github.com/memakura/s2microbit-ble/wiki/)です．
- [デモプロジェクト(fly.sb2など)](https://memakura.github.io/s2microbit-ble/00scratch/)
