SteamDeckはバス性能の問題で、SSDでもmicroSDでもストレージ性能が変わらない。  
そのため 64GB、256GB、512GBモデルとあるが、64GBに大容量のmicroSDというのが安くつく。

自分も64GBモデルにしたが、ソフト本体はmicroSDに入るのだが、 compatdataとシェーダーキャッシュは、本体のストレージを使われてしまうらしく、これが容量を食う。
なので、これをmicroSDに移動してしまう。

```
mv /home/deck/.steam/steam/steamapps/compatdata /run/media/mmcblk0p1/steamapps/compatdata
mv /home/deck/.steam/steam/steamapps/shadercache /run/media/mmcblk0p1/steamapps/shadercache
ln -sf  /run/media/mmcblk0p1/steamapps/compatdata /home/deck/.steam/steam/steamapps/compatdata
ln -sf  /run/media/mmcblk0p1/steamapps /shadercache /home/deck/.steam/steam/steamapps/shadercache
```

これをやると本体にインストールしたソフトもmicroSDが差さってなければエラーになるし、インストールなども途中でエラーが出たりする。   
compatdataも、shadercacheのどちらも、さらに下階層にソフトごとのフォルダがあるので、容量を食っている個別アプリごとにmicroSDに逃してリンクを貼るほうが安全だろう。