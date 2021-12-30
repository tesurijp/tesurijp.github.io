# WolframEngineの活用

Mathematicaのカーネル/コアである [Wolfram Engine](https://www.wolfram.com/engine/)は、ユーザー登録するだけでライセンスが得られ無償で利用することが出来る。  

リッチなフロントエンドであるMathematicaは含まれていないため、基本的な利用方法として以下のものが想定されている。
- [WolframScript](https://www.wolfram.com/wolframscript/)によってスクリプト言語として利用する
- テキストベースの[REPL](https://ja.wikipedia.org/wiki/REPL)
- [Jupyter](https://jupyter.org)によるWEBフロントエンドを使った Jupyterノート

## MathematicaとJupyter

コードとドキュメント、データと計算結果、計算過程などを一つにまとめるノートブックを作成するツールという点は同じ  
WolframEngineのフロントエンドとして利用して、計算した結果を数式や行列形式で表示したりグラフで表示するといった基本的な操作はそのまま行なえる。  

Jupyterは、もともとPythonのためのフロントエンドであったが、現在では多くの言語に対応している。  
MathematicaはWolframLanguageのためのフロントエンドであり、そのための機能が豊富。  
Jupyterは外部のツールやプラグインによる機能の拡張が積極的に行なわれているが、WolframLanguageのための拡張というわけではないので、専用の機能などは利用できない。  
[Manipulate](https://reference.wolfram.com/language/ref/Manipulate.html)のようなものは、Jupyterでは利用できず、スライダーの絵が表示された画像のアウトプットだけになる。
また、コンセプトの違いとしてMathematicaのノートは階層的なセル構造を持つが、Jupyterは完全にフラットであり階層構造を作ることは出来ない。  
ファイル形式の互換性もないため、相互に開くことも出来ない。

## Visual Studio Code 

[Visual Studio Code、VSCode](https://code.visualstudio.com/)は、Microsoft のオープンソースのテキストエディタで、GUIのテキストエディタとしてはWindows、Linux、macOS通してデファクトスタンダードの地位を揺ぎないものにしている。  
Visual Studio Codeは、初期の段階から Jupyterのフロントエンドとなることが出来たが、現在はJupyterのコア機能を Visual Studio Codeに取り込むことで、Python以外のJupyterカーネルも効率的に利用できるようになっている。  

VSCode上、WolframLanguageは、WolframScriptの開発環境として文法のサポートやデバッグなどのシンプルなものから、Jupyterを利用したノートブック形式での活用など様々な方法でサポートされている。

本来のJupyterは、WEBベースで実行するシステムのため、リモートからも操作できるなどの利点があるが、ローカルマシン上で実行するだけであれば環境の作成など手間がかかる点がデメリットになる。  
VSCodeでJupyterを利用する場合、利用時にのみ起動させノートブックの管理も通常のファイル管理と同様に行なうことが出来るようになる。  

## Visual Studio Codeで WolframEngineを使う

利用手順は以下のとおり

1. VSCodeのインストール
1. WolframEngineのインストール
1. WolframEngineのライセンス設定
1. WolframEngine用拡張機能のインストール

### VSCodeのインストール

[公式サイト](https://code.visualstudio.com/)から、Stableをダウンロードしてインストールする。  
Windows 11であれば、Microsoft Storeからもインストールできる。

### WolframEngineのインストール

[公式サイト](https://www.wolfram.com/engine)から、ダウンロードしインストールする。  
WolframEngineのテキストベースのREPLとして、WolframScriptも合わせてインストールされる。  

### WolframEngineのライセンス設定

WolframEngineをダウンロードすると、[ライセンス取得のページ](https://www.wolfram.com/engine/free-download-thank-you)に遷移する。  
Wolfram IDの作成と合わせて、ライセンスの取得が行なえる。  

WolrramScript/WolframEngineを起動すると初回に、Wolfram IDの入力を求められる。  
ここで、ライセンス取得したIDを入力すれば、WolframEngineのライセンス認証が完了する  

### WolframEngine用拡張機能のインストール

VSCodeを起動し、拡張機能のインストールを行なう  
拡張機能を検索するさいに、Wolframなどのキーワードを入れると絞り込める。  
いくつか種類はあるが、[Wolfram Language Notebook](https://marketplace.visualstudio.com/items?itemName=njpipeorgan.wolfram-language-notebook)という名前のものが、Jupyterもサポートした拡張機能になっている。


