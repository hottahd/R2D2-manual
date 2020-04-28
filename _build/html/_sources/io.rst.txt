出力と読込
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

.. py:module:: R2D2

PythonでR2D2で定義された関数を使うには

.. code:: python

    import R2D2

として、モジュールを読み込む。R2D2には :py:class:`R2D2_data` クラスが定義してあり、これをオブジェクト指向的に用いてデータを取り扱う。

以下にそれぞれの関数を示すが、docstringは記入してあるので

.. code:: python

    help(R2D2)
    help(R2D2.R2D2_data)

などとすると実行環境で、モジュール全体や各関数の簡単な説明を見ることができる。

クラス
^^^^^^^^^^^^^^^^^^^^^^^
.. py:class:: R2D2_data(datadir)

データの読み込みには ``R2D2`` モジュールの中で定義されている ``R2D2_data`` クラスを使う必要がある。

.. code:: python

    import R2D2
    datadir = '../run/d002/data'
    d = R2D2.R2D2_data(datadir)

などとしてインスタンスを生成する。

Attribute
^^^^^^^^^^^^^^^^^^^^^^^

.. py:attribute:: R2D2_data.p

    基本的なパラメタ。格子点数 ``ix`` や領域サイズ ``xmax`` など。
    インスタンス生成時に同時に読み込まれる。

.. py:attribute:: R2D2_data.qs

    ある高さの2次元のndarrayが含まれる辞書型。 :py:meth:`R2D2_data.read_qq_select` で読み込んだ結果。

.. py:attribute:: R2D2_data.qq
    
    3次元のnumpy array。計算領域全体のデータ。:py:meth:`R2D2_data.read_qq` で読み込んだ結果。

.. py:attribute:: R2D2_data.qt

    2次元のnumpy array。ある光学的厚さの面でのデータ。現在は光学的厚さ1, 0.1, 0.01でのデータを出力している。 :py:meth:`R2D2_data.read_qq_tau` で読み込んだ結果。

.. py:attribute:: R2D2_data.vc

    Fortranの計算の中で解析した結果。 :py:meth:`R2D2_data.read_vc` で読み込んだ結果。
.. py:attribute:: R2D2_data.qc

    3次元のnumpy array。計算領域全体のデータ。Fortranの計算でチェックポイントのために出力しているデータを読み込む。主に解像度をあげたいときのために使う :py:meth:`R2D2_data.read_qq_check` で読み込んだ結果。

:py:attr:`R2D2_data.p` については、``init.py`` などで

.. code:: python

    import R2D2
    d = R2D2.R2D2_data(datadir)
    for key in R2D2.p:
        exec('%s = %s%s%s' % (key, 'R2D2.p["',key,'"]'))

などとしているために、辞書型の ``key`` を名前にする変数に値が代入されている。例えば、 ``R2D2_data.p['ix']`` と ``ix`` には同じ値が入っている。

Method
^^^^^^^^^^^^^^^^^^^^^^

メソッドで指定する ``datadir`` はデータの場所を示す変数。R2D2の計算を実行すると ``data`` ディレクトリが生成されて、その中にデータが保存される。この場所を指定すれば良い。

.. py:method:: R2D2_data.__init__(datadir)
    
    インスタンス生成時に実行されるメソッド。計算設定などのパラメタが読み込まれる。 :py:attr:`R2D2_data.p` にデータが保存される。
    
    :argument str datadir: データの場所

.. py:method:: R2D2_data.read_qq_select(xs,n,silent)
    
    ある高さのデータのスライスを読み込む。戻り値を返さない時も :py:attr:`R2D2_data.qs` にデータが保存される。

    :param float xs: 読み込みたいデータの高さ
    :param int n: 読み込みたい時間ステップ

.. py:method:: R2D2_data.read_qq(n)
    
    3次元のデータを読み込む。戻り値を返さない時も :py:attr:`R2D2_data.qq` にデータが保存される。

    :param int n: 読み込みたい時間ステップ

.. py:method:: R2D2_data.read_qq_tau(n)
    
    光学的厚さが一定の2次元のデータを読み込む。:py:attr:`R2D2_data.qt` にデータが保存される。

    :param int n: 読み込みたい時間ステップ

.. py:method:: R2D2_data.read_time(n)
    
    時間を読み込む。

    :param int n: 読み込みたい時間ステップ
    :return: 時間ステップでの時間

.. py:method:: R2D2_data.read_vc(n)
    
    Fortranコードの中で解析した計算結果を読み込む。戻り値を返さない時も :py:attr:`R2D2_data.vc` にデータが保存される。

    :param int n: 読み込みたい時間ステップ

.. py:method:: R2D2_data.read_qq_check(n)
    
    チェックポイントのためのデータを読み込む :py:attr:`R2D2_data.qc` にデータが保存される。

    :param int n: 読み込みたい時間ステップ

IDLコード
::::::::::::::::::::::

`GitHubの公開レポジトリ <https://github.com/hottahd/R2D2_idl>`_ に簡単な説明あり

Paraview 使用
::::::::::::::::::::::

Paraviewを使用するためにデータ出力の関数が用意してある。

.. py:function:: R2D2.vtk.write_3D()

バージョン履歴
----------------------

* ver. 1.0: バージョン制を導入
* ver. 1.1: 光学的厚さが0.1, 0.01の部分も出力することにした。qq_in, vcをconfigのグローバル変数として取扱うことにした。
* ver. 1.2: データ構造を変更。

