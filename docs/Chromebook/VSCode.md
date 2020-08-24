# ChromeBook でVisual Studio Codeを使う

## 選択肢

Chromebook で利用できる Visual Studio Codeはいくつかある

- Visual Studio Code本物  
  amd64 版 は、Microsoftの公式バイナリ(deb)がある。arm64版は提供されていない
- オープンソースビルド  
  ビルドしている人が違う程度で、どちらも基本的な差はない。VSCodiumのほうが更新頻度は高め
  - VSCodium  
  - code-oss
- code-server
  Visual Studio Codeをオンラインで提供している coder のオープンソース/オンプレ版  
  crostiniでサーバー起動し、PWAとして動作させる

code-serverは、本体のChrome上で動作するので、標準のIMEによる日本語入力が可能  
他は、crostini上で動かすことになるため crostini上の IME(fcitx)の設定が必要
動作も、code-serverが若干軽量

## はまるところ

### VSCodium

~~1.47以降、プリビルドされている arm64版は動作しない。(chrombookのみに問題ではなく、他の環境でも動いていない)  
そのため、1.46.1を使う必要がある。~~

1.47.xx はarm64環境では動作しないので、1.46.1 か、1.48.1以降を利用する。

1.46.1 以降、拡張のマーケットプレイスが[外部](https://open-vsx.org/)のものに変更されている(マーケットプレイスのライセンスの問題)  
公開されている拡張がかなり少ないので、このまま使うのは厳しい
本家のマーケットプレイスを使うには /usr/share/codium/resources/app/product.json を書き換える必要がある。

```json
  "extensionsGallery": {
    "serviceUrl": "https://open-vsx.org/vscode/gallery",
    "itemUrl": "https://open-vsx.org/vscode/item"
  },
```

↓

```json
  "extensionsGallery": {
    "serviceUrl": "https://marketplace.visualstudio.com/_apis/public/gallery",
    "cacheUrl": "https://vscode.blob.core.windows.net/gallery/index",
    "itemUrl": "https://marketplace.visualstudio.com/items"
  },
```

### code-server

WiFi に接続していないとcrostini でサーバーを起動しても、本体のChromeから開けないことがある。  
