# ChromeBookのCrostiniのログインシェルをZSHにする

Chrostiniでzshは普通にインストール可能だが、chshでログインシェルを変更しても起動時はbashになってしまう。  
bash起動時に zshにexecさせることで、擬似的にログインシェルをzshに変更する。

具体的には、~/.profileの最後に以下の記述を追加する。

```
if [ $SHLVL -eq 1 ] ; then
    exec /bin/zsh -l
fi
```