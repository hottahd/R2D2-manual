方程式
=================

R2D2で解く方程式は以下である

MHD
-----------------

.. math::

    \frac{\partial \rho_1}{\partial t} &= - \frac{1}{\xi^2}\nabla\cdot
    \left(\rho \boldsymbol{v}\right) \\
    \frac{\partial}{\partial t}\left(\rho \boldsymbol{v}\right) &=
    -\nabla\cdot\left(\rho\boldsymbol{vv}\right)
    - \nabla p_1 - \rho_1 g\boldsymbol{e}_x
    +\frac{1}{4\pi}\left(\nabla\times\boldsymbol{B}\right)
    \times\boldsymbol{B} \\
    \frac{\partial \boldsymbol{B}}{\partial t} &= 
    \nabla\times\left(\boldsymbol{v\times B}\right)
    + \eta_\mathrm{d}\nabla\left(\nabla\cdot\boldsymbol{B}\right)\\
    \rho T \frac{\partial s_1}{\partial t} &= -\rho T 
    \left(\boldsymbol{v}\cdot\nabla\right) s + Q_\mathrm{rad} \\
    p_1 &= p_1(\rho_1,s_1,x)

輻射輸送
-----------------