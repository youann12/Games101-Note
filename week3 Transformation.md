# week 3 Transformation

### 为什么学变换

* 模型变换（Modeling）
  * Scaling
  * ...
* 视图变换（Viewing）
  * 投影
  * ...





### 2D变换

* Scale（缩放变换）
  * <img src="C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210718113625789.png" alt="image-20210718113625789" style="zoom: 50%;" />
  * <img src="C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210718113819620.png" alt="image-20210718113819620" style="zoom:50%;" />
* 反射矩阵
  * <img src="C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210718114017983.png" alt="image-20210718114017983" style="zoom:50%;" />
  * <img src="C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210718114052578.png" alt="image-20210718114052578" style="zoom: 67%;" />
* Shear Matrix 切变
  * <img src="C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210718113955296.png" alt="image-20210718113955296" style="zoom:50%;" />
  * <img src="C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210718114400983.png" alt="image-20210718114400983" style="zoom: 80%;" />
* 旋转（Rotate）
  * 任何时候不说其他信息，默认图像是绕原点转
  * 不说方向，默认是逆时针旋转写作R45（逆时针转45度）
  * <img src="C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210718114551389.png" alt="image-20210718114551389" style="zoom:67%;" />
  * ![image-20210718114607963](C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210718114607963.png)

任意变换如果能够写成矩阵的形式，则称这种变换为线性变换



### 齐次坐标

* 特殊的变换------平移
  * <img src="C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210718195816673.png" alt="image-20210718195816673" style="zoom:67%;" />
  * ![image-20210718195835667](C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210718195835667.png)
  * 不能像之前一样用一个矩阵表示变换，只能这样表示<img src="C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210718195912407.png" alt="image-20210718195912407" style="zoom: 80%;" />
  * 所以平移变换不是线性变换（不能表示成单矩阵的形式）、
* 解决办法------引入齐次坐标
  * 引入一个新维度之后
  * ![image-20210718200558151](C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210718200558151.png)
  * 由最后一个数字可以标识这个坐标是向量（最后一位为0），还是点（最后一位为1）
  * 一个点加另一个点表示的是这两点连线的中点



### 逆变换

![image-20210718201637653](C:\Users\z\AppData\Roaming\Typora\typora-user-images\image-20210718201637653.png)

就是乘以这个变换的逆矩阵



### 变换的组合（Composing Transforms）

* 多种变换的组合（旋转、平移等）
* 矩阵相乘
  * 应用最先的变换在离列向量（点坐标）越近
  * 不满足交换律，但是满足结合律
* 应用
  * 围绕任意一点旋转
    * 本来旋转默认是以原点为中心
    * 现在可以先把旋转中心点平移到原点
    * 再旋转旋转角 alpha
    * 在将旋转中心点平移到之前的位置





#### 3D变换

* 与2d变换类似，利用齐次坐标表示点







*仿射变换中，是先线性变换再平移还是先平移再线性变换呢？*

先线性变换再平移





