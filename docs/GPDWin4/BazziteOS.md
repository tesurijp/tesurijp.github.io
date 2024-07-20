# [BazziteOS](https://bazzite.gg/)

GPD Win4は、Windows Homeがインストールされているが、普通のPCなのでLinuxなどの他のOSも入る。  
この形状なので、汎用的なPCとして使うよりゲーム専用機として使うほうが自然であろう。  

SteamDeckのランチャー部分を、そのまま利用し操作感触としても SteamDeck相当になるOSがいくつかある。  

- [HoloISO](https://github.com/HoloISO)
- [ChimeraOS](https://chimeraos.org/)
- [Nobara Project](https://nobaraproject.org/)
- [BazziteOS](https://bazzite.gg/)

Bazzite OSは、機種固有の設定なども自動認識するなど扱いがよい。  

この情報は、GPD Win4 8840uで確認したものなので、7640uや 6800uと差異があるかもしれない。

## dual boot

GPD Win4 は、BIOSのアップデートなどもUSBブートするイメージで公開されるため、Windowsでしか動かないゲームをするのでもないかぎり、dual bootにする必要もない。

dual bootにしたい場合、Bazzite OSのインストーラは、適当な空きパーティションを指定してインストールすると、GRUBに Windowsの起動設定も含めた dual boot環境を自動で作成するので悩む要素はない。

## インストール後の設定

インストール直後は、デスクトップモードで起動し、いわゆる初期セットアップを行なう。  
ネットワーク接続は必須。  

この時の画面解像度(倍率)がクソで、操作がまともに出来ない。  
まずは、設定などの要求を無視して左下のスタートメニューから、設定を選び画面解像度を 300% から任意のサイズに変更する。100から150%ぐらいにすると、まともな画面になる。

追加インストールの項目などは、必要なものを入れればいい。ここで入れなくても、あとで追加できるので、あまり深く考える必要はない。  

Steamへのログインは必須

初期セットアップ後、再起動が行なわれる。
1回目の再起動では、暗転したまま固まる確率が高い。  
10分ぐらい反応が無ければ、電源ボタンを長押しして強制終了し、再度起動する。  
2回目も待ち時間は長いが、画面に何か表示されるはずなので、我慢して待つ。

一度ゲームモードで起動したあとは、再起動しても、ほとんど待たずに動作する。

## sshdの有効化

デスクトップモードで起動する。  
ssh の鍵を作成する。既存のものをコピーしてきてもいい。  
systemd で sshを有効に切替える。

Bazzite OSは、気軽に使えるようになっているが、悪い意味でLinuxである部分を色濃く残している。  
ここで手間取るようなら BazziteOS は向いてない。Windowsに戻すか、SteamDeckを使おう。

## 関連ツールのインストール・設定

ターミナルを起動すると見せられる ujust コマンドでDecky やHHDなどいろいろインストールできるらしい。

自分は、Bazziteで用意されたものではなく、各ツールを個別に入れた。

### [HHD](https://github.com/hhd-dev/hhd)

コントローラ関連の処理をいろいろやってくれるデーモン

### [Decky Loader](https://github.com/SteamDeckHomebrew/decky-loader)

SteamDeckでカスタムツールを入れるための基本フレームワークの一つ  
SteamDeckと異なり、BazziteOSでは startボタンでは開かない。  
デフォルトでは 背面ボタンで起動する。

### [GPD-WinControl](https://github.com/honjow/GPD-WinControl)

背面の二つのキー割当て、マウスモードでの各ボタンの割当ての変更を行なう Decky Plugin  
見栄えはともかく、Windows 用のものとほぼ同等のことが出来る。
RGB ライトの変更も行える。

ボタン割当ての変更は出来るのだが、HHDのホットキーとして利用する場合、背面ボタンはSysReqと PAUSE(それぞれ工場出荷状態) でなければならないので、実質変更できない。

### [HHD-Decky](https://github.com/hhd-dev/hhd-decky)

Decky Plugin として、HHDの設定変更を行なうUI


## その他

### Gyroの向きが変

HHDで コントローラをDualSense か Dualsense Edgeにすると、GPD Win4のジャイロが使えるようになるのだが、軸があっていない。
Motion Axis の overrideを使って、Axis X を Zに、Axis Y を Xに、AxisZ を Yに変更する。
上下を逆転したければ、Invertなども設定しておく。

### Resume後にコントローラがきかない

正確には ゲームモードのUIがコントローラの操作を受け取っており、ゲームを操作できない。  
背面ボタンの2度押しで、HHDを起動し、なんでもいいので設定を変更して保存。(そのあと元に戻してもいい)  

どうも初期値が適切でないようで、resume後に割当てがおかしくなるようだ。
UI側で更新されたものを保存すると、以後は問題なくなる。

### Resume後に Gyroが使えない。

 [Gyro-fix](https://github.com/aarron-lee/gpd-win-tricks/blob/main/win4-gyro-suspend-fix/README.md)  
Suspend /Resume 後に Gyroが死ぬ場合に必要。
Bazziteの不具合が修正されたら不要になるかもしれないが、2024/7 時点では必要
