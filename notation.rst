R2D2 pythonでのキーワードの説明
================================

.. py:data:: R2D2.p

    * datadir (str) -- データの保存場所
    * nd (int) -- 現在までのアウトプット時間ステップ数(3次元データ)
    * ni (int) -- 現在までのアウトプット時間ステップ数(光学的厚さ一定のデータ)
    * xdcheck (int) -- x軸方向に解いているか。解いていたら2、解いていなかったら1
    * ydcheck (int) -- y軸方向に解いているか。解いていたら2、解いていなかったら1
    * zdcheck (int) -- z軸方向に解いているか。解いていたら2、解いていなかったら1    
    * margin (int) -- 
    * nx (int) --
    * ny (int) -- 
    * nz (int) -- 
    * npe (int) -- 
    * ix0 (int) --
    * jx0 (int) --
    * kx0 (int) --
    * mtype (int) --
    * xmax (float) --
    * xmin (float) --
    * ymax (float) --
    * ymin (float) --
    * zmax (float) --
    * zmin (float) --
    * dtout (float) --
    * tend (float) --
    * swap (int) --
    * ix_e (int) --
    * jx_e (int) --
    * ixr (int) --
    * jxr (int) --
    * m_in (int) --
    * m_tu (int) --
    * dtoui (float) --
    * ifac (int) --
    * jc (int) --
    * kc (int) --
    * deep_top_flag (int) --
    * ib_excluded_top (int) --
    * endian (char) --
    * ix (int) --
    * jx (int) --
    * kx (int) --
    * x (float) [ix] --
    * y (float) [jx] --
    * z (float) [kx] --
    * pr0 (float) [ix] -- 
    * te0 (float) [ix] --
    * ro0 (float) [ix] --
    * se0 (float) [ix] --
    * en0 (float) [ix]
    * op0 (float) [ix]
    * tu0 (float) [ix]
    * dsedr0 (float) [ix]
    * dtedr0 (float) [ix]
    * dprdro (float) [ix] -- 背景場の :math:`(\partial p/\partial \rho)_s` 
    * dprdse (float) [ix] -- 背景場の :math:`(\partial p/\partial \rho)_s` 
    * dtedro (float) [ix] -- 背景場の :math:`(\partial p/\partial \rho)_s` 
    * dtedse (float) [ix] -- 背景場の :math:`(\partial p/\partial \rho)_s`
    * dendro (float) [ix] -- 背景場の :math:`(\partial p/\partial \rho)_s` 
    * dendse (float) [ix] -- 背景場の :math:`(\partial p/\partial \rho)_s` 
    * gx (float) [ix] -- 
    * kp (float) [ix] -- 
    * cp (float) [ix] -- 
    * fa (float) [ix] --
    * sa (float) [ix] --
    * xi (float) [ix] --
    * rsun (float) [ix] -- 
    * xr (float) [ix] -- x/rsun
    * xn (float) [ix] -- (x-rsun)*1.e-8
    * m2da (int) -- 
    * cl (char) [m2da] --
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

.. py:data:: a

    aaa
