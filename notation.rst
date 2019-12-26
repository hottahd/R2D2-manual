R2D2 pythonでのキーワードの説明
=========================================

以下では、R2D2 pythonで使われている辞書型に含まれるキーの説明を行う

* キーの名前 (型) -- 説明 [単位]

というフォーマットを採用する。

R2D2.p
--------------------------------

出力・時間に関する量
::::::::::::::::::::::::::::::::

* datadir (str) -- データの保存場所
* nd (int) -- 現在までのアウトプット時間ステップ数(3次元データ)
* ni (int) -- 現在までのアウトプット時間ステップ数(光学的厚さ一定のデータ)
* dtout (float) --　出力ケーデンス [s]
* dtoui (float) --　光学的厚さ一定のデータの出力ケーデンス [s]
* ifac (int) -- dtout/dtoui
* tend (float) -- 計算終了時間。大きく取ってあるためにこの時間まで計算することはあまりない [s]
* swap (int) --　エンディアン指定。big endianは、little endianは
* endian (char) -- エンディアン指定。big endianは、little endianは
* m_in (int) -- 光学的厚さ一定のデータを出力する変数の数
* m_tu (int) -- 光学的厚さ一定のデータの層の数


座標に関する量
::::::::::::::::::::::::::::::::
* xdcheck (int) -- x軸方向に解いているか。解いていたら2、解いていなかったら1
* ydcheck (int) -- y軸方向に解いているか。解いていたら2、解いていなかったら1
* zdcheck (int) -- z軸方向に解いているか。解いていたら2、解いていなかったら1    
* margin (int) -- マージン(ゴーストセル)の数
* nx (int) -- 1 MPIスレッドあたりのx方向の格子点の数
* ny (int) -- 1 MPIスレッドあたりのy方向の格子点の数
* nz (int) -- 1 MPIスレッドあたりのz方向の格子点の数
* ix0 (int) -- x方向のMPI領域分割の数
* jx0 (int) -- y方向のMPI領域分割の数
* kx0 (int) -- z方向のMPI領域分割の数
* ix (int) -- x方向の格子点数 ix0*nx
* jx (int) -- y方向の格子点数 jx0*ny
* kx (int) -- z方向の格子点数 kx0*nz
* npe (int) -- 全MPIスレッドの数 ``npe = ix0*jx0*kx0``
* mtype (int) -- 変数の数
* xmax (float) -- x方向境界の位置(上限値)　[cm]
* xmin (float) -- x方向境界の位置(下限値)　[cm]
* ymax (float) -- y方向境界の位置(上限値)　[cm]
* ymin (float) -- y方向境界の位置(下限値)　[cm]
* zmax (float) -- z方向境界の位置(上限値)　[cm]
* zmin (float) -- z方向境界の位置(下限値)　[cm]
* x (float) [ix] -- x方向の座標 [cm]
* y (float) [jx] -- y方向の座標 [cm]
* z (float) [kx] -- z方向の座標 [cm]
* xr (float) [ix] -- x/rsun
* xn (float) [ix] -- ``(x-rsun)*1.e-8``
* deep_top_flag (int) --
* ib_excluded_top (int) --
* rsun (float) [ix] -- 太陽半径 [cm]

背景場に関する量
::::::::::::::::::::::::::::::::
* pr0 (float) [ix] -- 背景場の圧力 [dyn cm `-2`:sup:]
* te0 (float) [ix] -- 背景場の温度 [K]
* ro0 (float) [ix] -- 背景場の密度 [g cm `-3`:sup:]
* se0 (float) [ix] -- 背景場のエントロピー [erg g `-1`:sup: K `-1`:sup:]
* en0 (float) [ix] -- 背景場の内部エネルギー [erg cm `-3`:sup:]
* op0 (float) [ix] -- 背景場のオパシティー []
* tu0 (float) [ix] -- 背景場の光学的厚さ
* dsedr0 (float) [ix] -- 背景場の鉛直エントロピー勾配 [erg g `-1`:sup: K `-1`:sup: cm `-1`:sup:]
* dtedr0 (float) [ix] -- 背景場の鉛直温度勾配 [K cm `-1`:sup:]
* dprdro (float) [ix] -- 背景場の :math:`(\partial p/\partial \rho)_s` 
* dprdse (float) [ix] -- 背景場の :math:`(\partial p/\partial s)_\rho` 
* dtedro (float) [ix] -- 背景場の :math:`(\partial T/\partial \rho)_s` 
* dtedse (float) [ix] -- 背景場の :math:`(\partial T/\partial s)_\rho`
* dendro (float) [ix] -- 背景場の :math:`(\partial e/\partial \rho)_s` 
* dendse (float) [ix] -- 背景場の :math:`(\partial e/\partial s)_\rho` 
* gx (float) [ix] -- 重力加速度 [cm s `-2`:sup:]
* kp (float) [ix] -- 放射拡散係数 [cm `2`:sup: s `-1`:sup:]
* cp (float) [ix] -- 定圧比熱　[erg g `-1`:sup: K `-1`:sup:]
* fa (float) [ix] -- 対流層の底付近の輻射によるエネルギーフラックス。光球付近では輻射輸送を直に解くために含まれないが、上部境界が光球にない場合は、上部境界付近の人工的なエネルギーフラックス(冷却が含まれる) [erg cm `-2`:sup:]
* sa (float) [ix] -- 上記faによる加熱率 [erg cm `-3`:sup:]
* xi (float) [ix] -- 音速抑制率
* ix_e (int) -- 状態方程式の密度の格子点数
* jx_e (int) -- 状態方程式のエントロピーの格子点数

解析のためのデータ再配置(remap)に関する量
::::::::::::::::::::::::::::::::::::::::::::

* m2da (int) -- remapで出力した解析量の数
* cl (char) [m2da] --　remapで出力した解析量の名前
* jc (int) -- ``R2D2.vc['vxp']`` などで出力するスライスのy方向の位置
* kc (int) -- 浮上磁場の中心と思っている場所を出力(あまり使わない)
* ixr (int) -- remap後のx方向分割の数
* jxr (int) -- remap後のy方向分割の数
* iss (int) [npe] --
* iee (int) [npe] --
* jss (int) [npe] --
* jee (int) [npe] --
* iixl (int) [npe] --
* jjxl (int) [npe] --
* np_ijr (int) [npe] --
* ir (int) [npe] --
* jr (int) [npe] --
* i2ir (int) [ix] --
* j2jr (int) [jx] --

R2D2.q2
--------------------------------

* aaa

R2D2.q3
--------------------------------

R2D2.q2と同様

R2D2.qi
--------------------------------

ほぼR2D2.q2と同様だが、以下の追加量が保存してある。

R2D2.vc
--------------------------------

最終更新日：|today|