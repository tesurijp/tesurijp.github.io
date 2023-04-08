# ReaderStore

Androidアプリのソニーの書籍ストアは、インストール可能で書籍を読むことに関しては問題なく動作する。  
しかしアカウント認証や書籍購入が、AndroidのChromeアプリが必要になっているうえ、AndoridのChromeは、Chromebookにインストールできない。  
そのため、素のままでは ReaderStoreを利用することが出来ない


## 回避方法

1. AndoridのChromeアプリをインストール
1. 認証情報をアプリに保存
1. Chromeアプリをアンインストールする。

AndoridのChromeアプリをインストールしたままにすると、ウェブのリンクをChromebook本体のChromeアプリと取り合って、両方のChromeが正常に動かない。  
ReaderStoreの最初の認証だけ行なって、削除しておく必要がある。

## 注意点

この方法で、端末はデベロッパーモードになってしまう。  
解除するには端末の初期化が必要になる。

## 手順

1. Android 用の Chromeアプリの apk を取得する。  
   すでにある端末から適当に抜き出すか、適当にダウンロードしてくる
1. Chromebook のCrostiniでADBデバッグを有効にする。  
    **この方法で、端末はデベロッパーモードになってしまう。**  
    **解除するには端末の初期化が必要になる。**
1. crostini 上で、adb をインストール  

    ```bash
    sudo apt install android-tools-adb
    ```

1. adb でAndroid用Chromeのインストール

    ```bash
    adb install [Chrome for android.apk]
    ```

1. RederStoreアプリでログイン

1. Android用Chromeをアンインストール

## 本の購入

ReaderStoreアプリから Chromeがないのでストアは開けない。  
PC用のサイトで開いて購入するか、他の端末で購入する。

購入済み書籍のダウンロードには、Chromeアプリは必要ない