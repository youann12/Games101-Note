# week1-2 Linear Algebra

###图形学基础知识

#### 基础数学

* 先行代数，计算，统计学

#### 基础物理

* 光学、力学

#### 其他杂项

* 信号处理
* 数值分析

#### 一点点美学





### 线性代数

* 向量 Vector

  * 是一个方向

  * 向量的长度（可以给我们提供单位向量）

  * 向量加法

    * 平行四边形法则
    * 三角形法则
    * （图形学中向量缺省是个列向量）

  * 向量计算

    * 点乘

      * $$\vec{a} · \vec{b} = ||\vec{a}||||\vec{b}||cos\theta  $$
      * $$cos\theta = \frac{\vec{a} · \vec{b}} {||\vec{a}||||\vec{b}||} $$
      * **是一个数字，主要应用是从两个向量得到他们的夹角**
      * 计算方式
        * 2d空间中
          * $$\vec{a} · \vec{b} = \bigg(\begin{matrix} x_a \\ y_a  \end{matrix} \bigg) · \bigg(\begin{matrix} x_b \\ y_b  \end{matrix} \bigg) = x_ax_b + y_ay_b$$
        * 3d空间中
          * $$\vec{a} · \vec{b} = \bigg(\begin{matrix} x_a \\ y_a \\ z_a  \end{matrix} \bigg) · \bigg(\begin{matrix} x_b \\ y_b \\ z_b \end{matrix} \bigg) = x_ax_b + y_ay_b + z_az_b$$
      * 应用
        * 算投影
        * 判断前与后的信息
        * 从点乘结果的正负判断两个向量在方向上是否接近

    * 叉积

      * $$ a \times b = -b \times a \\ ||a \times b|| = ||a|| \times||b|| sin \phi$$

      * 会得到一个新向量，这个新向量垂直与向量a和向量b

      * 新向量方向由右手螺旋定则确定

      * 计算方式

        * $$\vec{a} \times \vec{b} = \bigg(\begin{matrix} y_az_b - y_bz_a \\ z_ax_b - x_az_b \\ x_ay_b - y_ax_b  \end{matrix} \bigg) $$
        * 矩阵形式
          * $$\vec{a} \times \vec{b} = A * b = \bigg(\begin{matrix} 0&-z_a&y\\ z_a & 0 & -x_a \\ - y_a & x_a & 0  \end{matrix} \bigg) \bigg(\begin{matrix} x_b\\ y_b \\ z_b \end{matrix} \bigg) $$

      * 矩阵形式

      * 应用

        * 可以用它建立直角坐标系的三根轴
        * 判断左和右
        * 判断内与外

        

* 矩阵 Matrix

  * 矩阵乘积
    * 什么是能乘的矩阵
      * 第一个矩阵列数等一第二个矩阵的行数
      * $$(M \times N) (N \times P) = (M \times P)$$
    * 没有交换率
    * 结合律分配律都有
    * 矩阵和向量相乘
    * 矩阵转置
    * 单位矩阵
    * 如果两个矩阵不管顺序相乘都能得到单位矩阵，则称他们为互逆矩阵

