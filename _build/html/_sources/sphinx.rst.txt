Sphinx使用の覚書
================================

はじめに
--------------------------------
Sphinxは、reStructuredTextからHTMLやLatexなどの
文章を生成するソフトウェアである。
`Sphinxの公式サイト <https://www.sphinx-doc.org/ja/master/index.html>`_
最近ではMarkdownでも記述できるが、結局最後のところはreStructuredTextで記述することに
なるので、現状では、Markdownは使用していない。
このウェブサイトもSphinxで生成しているので、覚書をここに記す。


インストール
--------------------------------

ここではAnacondaがすでにインストールしてあるMac
にSphinxをインストールすることを考える。
基本的には以下のコマンドを実行するのみである。

.. sourcecode:: shell
		
   pip install sphinx 

Markdownを使いたい時は以下のようにする。

.. sourcecode:: shell
		
   pip install commonmark recommonmark


HTMLファイルの生成
--------------------------------

適当なディレクトリを作成(ここでは ``test`` )とする。
そこで、 ``sphinx-quickstart`` コマンドによりSphinxで作るドキュメントの
初期設定を行う。

.. sourcecode:: shell

   mkdir test # ディレクトリ作成
   cd test    # ディレクトリに移動
   sphinx-quickstart

いくつか質問をされる。基本的には読めばわかる質問であるが
少し戸惑う質問を以下にあげる。

* プロジェクトのリリース: 1.0などとversionを答える。後に ``conf.py`` を編集すれば変更可能
* プロジェクトの言語: デフォルトは英語の ``en`` であるが、日本語を使いたい時は ``ja`` とする
		
VS codeの利用
--------------------------------

環境設定
--------------------------------
``conf.py`` を設定

記法
--------------------------------
