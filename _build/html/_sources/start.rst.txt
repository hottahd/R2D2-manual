R2D2を使い始めるには
================================

ディレクトリ構造の準備
--------------------------------

R2D2は現在公開していないので、R2D2のzipファイルを堀田から受け取ったと仮定する。コードをしっかり読めば従う必要はないが、基本的には以下のようなディレクトリ構造で計算することを想定している。

.. code::

    project_name/
               ├─ run/
               │    ├─ d001/
               │    ├─ d002/
               │    ├─ d003/
               │    ├─ ...
               │
               ├─ py/
               └─ idl/


pyには `R2D2_py <https://github.com/hottahd/R2D2_py>`_ をクローンしてきたもの、idlには `R2D2_idl <https://github.com/hottahd/R2D2_idl>`_ をクローンしてきたものを配置する。ここは名前が変わっても問題ない。python(py)とidlのどちらかを使えば解析は可能である(両方ダウンロードする必要はない)。

堀田から受け取ったR2D2.zipファイルをそれぞれrunディレクトリのd001などと名前を変えて配置することで色々な計算ケースを実行するのが良いだろう。

R2D2ディレクトリの中は以下のようなディレクトリ構造になっている。

.. code::

   R2D2/
      ├─ F90_deps.py
      ├─ Makefile
      ├─ README.md
      ├─ gen_time.py
      ├─ data/
      │     ├─ back.dac
      │     ├─ param/
      │     │      ├─ nd.dac
      │     │      ├─ params.dac
      │     │      └─ xyz.dac
      │     │
      │     ├─ qq/
      │     │   ├─ qq.dac.e
      │     │   ├─ qq.dac.o
      │     │   ├─ qq.dac.00000000
      │     │   ├─ qq.dac.00000001
      │     │   ├─ ...        
      │     │
      │     ├─ remap/
      │     └─ time/
      │      
      ├─ input_data/
      ├─ make/
      ├─ retired_src/
      ├─ sh/
      └─ src/
           ├─ all/
           └─ include/

それぞれのファイル、ディレクトリの簡単な説明は以下である。

* F90_deps.py
    make/Makefile生成のためのpythonスクリプト。fortranコードの依存性を調べて、make/R2D2.depsに出力する。新しいプログラムを作成したときは

    .. code-block:: shell

        python F90_deps.py

    としてmake/R2D2.depsを更新する。
* Makefile
    makeをするときにmakeディクレクトリに移動する為のファイル。編集する必要はない。編集すべきMakefileはmake/Makefileに配置してある。
* README.md
    GitHubに表示する為の表示する為の説明ファイル。情報が古くなっている可能性があるので、README.mdを見るよりは、このウェブページの情報を参照されたい。
* gen_time.py
    他のモデルから計算結果をもらったときにdataディレクトリや時間のファイルを生成する為のpythonスクリプト
* data/
    fortranプログラムを実行した後に、データが保存されるディレクトリ。fortranプログラムを実行すると自動的に生成される。

    * data/back.dac
        背景場の物理量を出力するファイル
    * data/param/
        基本的な計算設定パラメタを出力する為のディレクトリ
    * data/qq/
        チェックポイントのための３次元データを出力するためのディレクトリ
    * data/remap
        解析のための
    * data/time/

コンパイル
--------------------------------


基本的なパラメータ
--------------------------------

初期条件データを受け取った場合
--------------------------------


最終更新日：|today|