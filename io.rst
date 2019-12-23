入力・出力
=================

出力
----------------------

Fortranコード
::::::::::::::::::::::

読込
----------------------
読み込みについては、PythonコードとIDLコードを用意しているが、開発の頻度が高いPythonコードの利用を推奨している。

Pythonコード
::::::::::::::::::::::

PythonでR2D2で定義された関数を使うには

.. code:: python

    import R2D2

として、ライブラリを読み込む。R2D2にはグローバル変数、関数が定義してある。

以下にそれぞれの関数を示すが、

.. code:: python

    R2D2.help()

とすると実行環境で簡単な説明を見ることができる。

グローバル変数
^^^^^^^^^^^^^^^^^^^^^^
Pythonでは一般に推奨されないが、R2D2ではメモリ節約の目的のためにいくつかのグローバル変数を用意している。R2D2をインポートした後は、``R2D2.*`` とすることで変数にアクセスできる。

.. py:data:: p

    基本的なパラメタ。格子点数 ``ix`` や領域サイズ ``xmax`` など。 ``read_init`` で読み込んだ結果。
.. py:data:: q2

    2次元のnumpy array。ある高さのデータ。``read_qq_select`` で読み込んだ結果。
.. py:data:: q3
    
    3次元のnumpy array。計算領域全体のデータ。``read_qq`` で読み込んだ結果。
.. py:data:: qi

    2次元のnumpy array。ある光学的厚さの面でのデータ。現在は光学的厚さ1, 0.1, 0.01でのデータを出力している。 ``read_qq`` で読み込んだ結果。
.. py:data:: vc

    Fortranの計算の中で解析した結果。 ``read_vc`` で読み込んだ結果。
.. py:data:: qc

    3次元のnumpy array。計算領域全体のデータ。Fortranの計算でチェックポイントのために出力しているデータを読み込む。主に解像度をあげたいときのために使う ``read_qq_check`` で読み込んだ結果。

``p`` については、``init.py`` などで

.. code:: python

    for key in R2D2.p:
        exec('%s = %s%s%s' % (key, 'R2D2.p["',key,'"]'))

としているために、辞書型の ``key`` を名前にする変数に値が代入されている。例えば、 ``R2D2.p['ix']`` と ``ix`` には同じ値が入っている。

関数
^^^^^^^^^^^^^^^^^^^^^^

関数で指定する ``dir`` はデータの場所を示す変数。R2D2の計算を実行すると ``data`` ディレクトリが生成されて、その中にデータが保存される。この場所を指定すれば良い。

.. py:function:: read_init(dir,dimension)
    
    R2D2でデータを解析するときに、一番はじめに実行すべき関数。計算設定などのパラメタが読み込まれる。 ``R2D2.p`` にデータが保存される。
    
    :argument str dir: データの場所
    :param str dimension: 2Dか3Dを示す
    :return: None
.. py:function:: read_qq_select(dir,xs,n)
    
    ある高さのデータのスライスを読み込む。戻り値を返さない時も ``R2D2.q2`` にデータが保存される。

    :argument str dir: データの場所
    :param float xs: 読み込みたいデータの高さ
    :param int n: 読み込みたい時間ステップ
    :return: ``out=True`` が指定されているとデータが返される。
.. py:function:: read_qq(dir,n)
    
    3次元のデータを読み込む。戻り値を返さない時も ``R2D2.q3`` にデータが保存される。

    :argument str dir: データの場所
    :param float xs: 読み込みたいデータの高さ
    :param int n: 読み込みたい時間ステップ
    :return: ``out=True`` が指定されているとデータが返される。
.. py:function:: read_time(dir,n)
    
    時間を読み込む

    :argument str dir: データの場所
    :param int n: 読み込みたい時間ステップ
    :return: 時間ステップでの時間が返される
.. py:function:: read_vc(dir,n)
    
    Fortranコードの中で解析した計算結果を読み込む。戻り値を返さない時も ``R2D2.vc`` にデータが保存される。

    :argument str dir: データの場所
    :param int n: 読み込みたい時間ステップ
    :return: ``out=True`` が指定されているとデータが返される。


IDLコード
::::::::::::::::::::::


バージョン履歴
----------------------

* ver. 1.0: バージョン制を導入
* ver. 1.1: 光学的厚さが0.1, 0.01の部分も出力することにした。qq_in, vcをconfigのグローバル変数として取扱うことにした。