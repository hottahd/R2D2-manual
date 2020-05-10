f2pyを用いたPythonコード
=================================================

いくつかのPythonで行うと遅くなってしまう作業について、fortranコードを書いた上で、f2pyを用いてPythonから使うことができるようにしている。

新しくfortranコードを書いた時
-------------------------------------------------
:code:`R2D2_py/R2D2` 下にfortranコードを配置。ファイル名とモジュール名は同じにする。その場で :code:`make` とした後、:code:`__init__.py` に

.. code:: python

    import R2D2.regrid

などと書き加える。こうすると

.. code:: python

    import R2D2

のみで、f2pyの関数を使うことができる。f2pyについては `こちらの記事 <https://qiita.com/hotta_hideyuki/items/ae5762d3f4885de29420>`_ を参照。

R2D2で用意されているf2pyのモジュール・関数
-------------------------------------------------

.. py:function:: R2D2.regrid

.. py:function:: R2D2.derv
    