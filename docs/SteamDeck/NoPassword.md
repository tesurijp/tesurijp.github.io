SteamDeck のデスクトップモードでの作業は、通常のLinuxであり sudo などを利用するケースも出てくる。  
標準アカウント deck にはパスワードが設定されておらず、パスワードを設定しないと sudo は利用できない。  
パスワードが設定されていない状態が標準にもかかわらずパスワードを設定するのは、いろいろと問題が生じる可能性が高い。  

sudo をパスワード無しで使える状態にする。

1. 一時的に適当なパスワードを設定する
1. /etc/sudoers.d/wheel を書換える  
 ``%wheel ALL=(ALL) ALL``  → ``%wheel ALL=(ALL) NOPASSWD:ALL`` 
 1. パスワードを削除する  
``sudo passwd -d deck``