# week 4 Transformation Cont.

* 旋转 $\theta$​ 的矩阵等于旋转 $-\theta$ 的矩阵的逆
* 在旋转里，旋转的逆等于旋转矩阵的转置
* 在数学上，如果一个矩阵的逆等于他的转置，称之为正交矩阵





### 3D变化

* 3D point = (x, y, z, 1) ^T 
* 3D vector = (x, y, z, 0) ^T
* <img src="C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210721210846315.png" alt="image-20210721210846315" style="zoom: 80%;" />
* 是先应用线性变换，再加一个平移量（与二维一样）
* 缩放
  * <img src="C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210721210940690.png" alt="image-20210721210940690" style="zoom:67%;" />
* 平移
  * <img src="C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210721211000701.png" alt="image-20210721211000701" style="zoom: 80%;" />
* 旋转
  * 绕x
    * ![image-20210721211048297](C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210721211048297.png)
  * 绕y
    * ![image-20210721211100541](C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210721211100541.png)
      因为是z 叉乘 x 才能的到y，所以$sin\alpha$符号反了
  * 绕z
    * ![image-20210721211112265](C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210721211112265.png)
  * 欧拉角旋转
    * $R_{xyz}(\alpha, \beta,\gamma) = R_x(\alpha)R_y(\beta)R_z(\gamma)$
    * 绕x, y, z轴的旋转变成pitch, yaw, roll
    * 罗德里格斯旋转公式
      * n是旋转轴，$\alpha$ 是旋转角
      * $R(n,\alpha) = cos(\alpha)I + (1 - cos(\alpha))nn^T + sin(\alpha)\left[ \begin{matrix} 0 & -n_z & n_y \\ n_z & 0 & -n_x \\ -n_y & n_x & 0 \end{matrix} \right]$ 
  * 四元数
    * 解决旋转与旋转之间的差值



### Viewing（观测）Transformation

#### view 视图变换 / 相机变换

把3维中的物体变成二维的一张图

* 拍照过程
  * 搭建模型 （modeling）
  * 找一个好的角度来放置相机（视图变换）（view）
  * 投影变换 （projection）简称MVP变换

* 什么是视图变换
  * 先得定义相机
    * Position $\vec{e}$
    * 相机朝向 $\hat{g}$
    * 向上的方向 $\hat{t}$​ 
    * <img src="C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210721215054021.png" alt="image-20210721215054021" style="zoom: 80%;" />
  * 如何进行视图变换
    * 假定相机永远在原点，永远看向-z
    * 先把 $\vec{e}$平移到原点
    * 再把$\hat{g}$ 移向-z方向
    * 所以是得先乘平移矩阵再考虑旋转
    * 将旋转轴移向坐标轴不好直接求，可以考虑将坐标轴移向旋转轴并用他的逆变换
      * ![image-20210721223336111](C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210721223336111.png)
    * $M_{view} = R_{view}T_{view}$​
  * 总结
    * 用相机移动来变换物体
    * 相机移到原点后，向上移到Y，看向方向移到-Z
    * 这同时也叫做模型视图变换

#### Projection （投影）Transformation

![image-20210721223950099](C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210721223950099.png)

![image-20210721224151218](C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210721224151218.png)

* Orthographic（正交） projection 投影
  * 相当于相机无限远（成像效果）
  * 将相机放到原点，看向-Z，向上方向为Y
  * 将Z坐标扔掉、
  * 将所有东西缩放到 [-1,1] 的正方形上
  * 正式一点的做法
  * <img src="C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210721224918052.png" alt="image-20210721224918052" style="zoom:80%;" />
    * 构建[l,r] * [b,t] * [f,n]的立方体
    * 将立方体中心平移到原点
    * 缩放成[-1,1] ** 3
    * <img src="C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210721224854765.png" alt="image-20210721224854765" style="zoom: 80%;" />
    * (此时物体被拉伸，在之后进行视口变换后就能够恢复原有比例)



* Perspective （透视） projection 投影

  * 简单来说，平行线不再平行

  * ![image-20210721225611817](C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210721225611817.png)

  * 将远平面往里挤，挤成和近平面一样大小，再做一次正交投影

    * 近平面不变
    * 远平面z值不变
    * 中心点连线不变

  * 于是问题转换成了怎么去将Frustum挤压成cuboid

  * 通过相似三角形计算

    * ![image-20210721231236424](C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210721231236424.png)

    * 可以得到x'和x 与 y和y'的关系

    * <img src="C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210721231531685.png" alt="image-20210721231531685" style="zoom:67%;" />

    * 那么可以知道，原始点乘完变换矩阵之后能够得到中间那个向量，再给他们乘个z

    * ![image-20210721231704839](C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210721231704839.png)

    * 于是可以得到一个猜测矩阵

      * ![image-20210721231904907](C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210721231904907.png)

      

    * 有两点已知现象
      * 任何一个点在近平面运算完都不会发生变换
      * 远的平面z不会发生变化
    * 那么有
      * 任何一个点在近平面运算完都不会发生变换
        * ![image-20210721232137483](C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210721232137483.png)
        * 所以第三行只能是（0  0  A  B）这种形式
          * ![image-20210721232601719](C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210721232601719.png)
      * 远的平面z不会发生变化
        * <img src="C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210721232655263.png" alt="image-20210721232655263" style="zoom:80%;" />
        * 远平面中心点不会发生变化
          * <img src="C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210721232744422.png" alt="image-20210721232744422" style="zoom:80%;" />
      * 所以最终可以得到
        * ![image-20210721232838907](C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210721232838907.png)

