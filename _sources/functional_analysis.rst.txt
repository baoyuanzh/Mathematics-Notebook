==============================
Functional analysis (泛函分析)
==============================

------------------------------
Linear Spaces
------------------------------

.. admonition:: Lemma
   :name: young-inequality
   
   
   [:index:`Young's inequality`] 对于任意的 :math:`\alpha, \beta \ge 0` , 且 :math:`p, q > 1, \dfrac{1}{p}+\dfrac{1}{q}=1` , 有如下不等式成立，

   .. math:: 
      :label: eq:young-inequality

      \alpha \beta \le \frac{\alpha^{p}}{p} + \frac{\beta^{q}}{q}

.. admonition:: Proof

   思路基本上是用导数算出极值，用二次导数表明该极值是极小值。可以直接计算 :math:`f(\alpha) = \dfrac{\alpha^{p}}{p} + \dfrac{\beta^{q}}{q} - \alpha \beta` 的导数，也可以在做一定变换后求 :math:`f(x) = x^{1-p} + (p-1)x - p` 的导数，后者的推导如下，
   
   .. math:: 
   
      \alpha \beta \le \frac{\alpha^{p}}{p} + \frac{\beta^{q}}{q} \Leftrightarrow 1 \le \frac{\alpha^{p-1}\beta^{-1}}{p} + \frac{\beta^{q-1}\alpha^{-1}}{q} \Leftrightarrow 1 \le \frac{\alpha^{\frac{p}{q}}\beta^{-1}}{p} + \frac{\beta^{\frac{q}{p}}\alpha^{-1}}{q}
      
   最妙的地方在于注意到 :math:`\alpha^{\frac{p}{q}}\beta^{-1} = (\beta^{\frac{q}{p}}\alpha^{-1})^{-\frac{p}{q}}` , 令 :math:`x = \beta^{\frac{q}{p}}\alpha^{-1}` , 那么就有 :math:`x > 0` , 且
   
   .. math:: 
   
      \alpha \beta \le \frac{\alpha^{p}}{p} + \frac{\beta^{q}}{q} \Leftrightarrow 1 \le \frac{x^{-\frac{p}{q}}}{p} + \frac{x}{q} \Leftrightarrow 1 \le \frac{x^{1-p}}{p} + \frac{(p-1)x}{p} \Leftrightarrow 0 \le x^{1-p} + (p-1)x - p

   由 :math:`f'(x) = 0` 可推出 :math:`x = 1` , 于是有 :math:`f(1) = 0` 且 :math:`f''(1) = p(p-1) > 0` , 从而得证
   
.. admonition:: Theorem
   :name: holder-inequality
   
   [:index:`Hölder's inequality`] 对于任意的 :math:`p` 次，:math:`q` 次绝对收敛的序列 :math:`(x_{n}) \in \mathscr{l}_{p}, (y_n) \in \mathscr{l}_{q}` , 且 :math:`p, q > 1, \dfrac{1}{p}+\dfrac{1}{q}=1` , 有如下不等式成立，

   .. math:: 
      :label: eq:holder-inequality

      \sum_{k=1}^{\infty}|x_{k}y_{k}| \le \left(\sum_{k=1}^{\infty} |x_{k}|^{p}\right)^{\frac{1}{p}} \left(\sum_{k=1}^{\infty} |y_{k}|^{q}\right)^{\frac{1}{q}}

   这个不等式可以认为是柯西不等式的推广，方便记忆的方法 -- **两个向量的內积不大于它们的模的积** ，注意这两个向量的模是共轭的

.. admonition:: Proof
   
   思路是利用 :ref:`Young's inequality <young-inequality>` 来证明，但其中有个很有意思的变换，如果不做这个变换则正好得不到想要的不等号方向，
   
   .. math:: 
   
      \frac{|x_{k}|}{\left(\sum_{k=1}^{\infty}|x_{k}|^{p}\right)^{\frac{1}{p}}} \frac{|y_{k}|}{\left(\sum_{k=1}^{\infty}|y_{k}|^{q}\right)^{\frac{1}{q}}} \le \frac{1}{p}\frac{|x_{k}|^{p}}{\sum_{k=1}^{\infty}|x_{k}|^{p}} + \frac{1}{q}\frac{|y_{k}|^{q}}{\sum_{k=1}^{\infty}|y_{k}|^{q}}
      
   接下去的部分就显然了，得证
   
   
.. admonition:: Theorem
   :name: minkowski-inequality
   
   [:index:`Minkowski's inequality`] 对于任意 :math:`p` 次绝对收敛的序列 :math:`(x_{n}), (y_{n}) \in \mathscr{l}_{p}` , 且 :math:`p > 1` , 有如下不等式成立，

   .. math:: 
      :label: eq:minkowski-inequality

      \left(\sum_{k=1}^{\infty}|x_{k} + y_{k}|^{p}\right)^{\frac{1}{p}} \le \left(\sum_{k=1}^{\infty} |x_{k}|^{p}\right)^{\frac{1}{p}}+ \left(\sum_{k=1}^{\infty} |y_{k}|^{p}\right)^{\frac{1}{p}}

   这个不等式可以认为就是三角不等式： :math:`||x+y||_{p} \le ||x||_{p} + ||y||_{p}`

.. admonition:: Proof
   
   思路是利用 :ref:`Hölder's inequality <holder-inequality>` 来证明，但首先要创造出 :math:`p` 的共轭数 :math:`q`，令 :math:`\frac{1}{p} = 1 - \frac{1}{q}` , 代入不等式左侧得到 :math:`\left(\sum_{k=1}^{\infty}|x_{k} + y_{k}|^{p}\right)^{1 - \frac{1}{q}}` , 考虑到不等式左侧和的绝对值不适合拆开，于是在不等式两侧同乘以 :math:`\left(\sum_{k=1}^{\infty}|x_{k} + y_{k}|^{p}\right)^{\frac{1}{q}}` 就得到
   
   .. math::
      :nowrap:
      
      \begin{align*}
      &\left(\sum_{k=1}^{\infty} |x_{k}|^{p}\right)^{\frac{1}{p}}\left(\Big(\sum_{k=1}^{\infty}|x_{k} + y_{k}|^{\frac{p}{q}}\Big)^{q}\right)^{\frac{1}{q}} + \left(\sum_{k=1}^{\infty} |y_{k}|^{p}\right)^{\frac{1}{p}} \left(\Big(\sum_{k=1}^{\infty}|x_{k} + y_{k}|^{\frac{p}{q}}\Big)^{q}\right)^{\frac{1}{q}}\\
      &\ge \sum_{k=1}^{\infty}|x_{k}||x_{k} + y_{k}|^{\frac{p}{q}} + \sum_{k=1}^{\infty}|y_{k}||x_{k} + y_{k}|^{\frac{p}{q}} \ge \sum_{k=1}^{\infty}|x_{k} + y_{k}|^{\frac{p}{q} + 1} = \sum_{k=1}^{\infty}|x_{k} + y_{k}|^{p}
      \end{align*}
      
   得证

------------------------------
Normed Linear Spaces
------------------------------