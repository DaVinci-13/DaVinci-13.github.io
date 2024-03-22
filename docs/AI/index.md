---
title: Artificial Intelligence
layout: doc
permalink: /ai/
---

# Machine Learning by Andrew.Ng
## 课程介绍
吴恩达机器学习课程：https://www.coursera.org/learn/machine-learning/  
第三方笔记：https://github.com/fengdu78/Coursera-ML-AndrewNg-Notes  
第三方作业：https://github.com/nsoojin/coursera-ml-py

**参考笔记**：https://mp.weixin.qq.com/s?__biz=MzIwOTc2MTUyMg==&mid=2247507430&idx=2&sn=5d1deb023b009c32cce3d37e37f2efac&chksm=976c787ba01bf16d15432a341cb0733e8012ebf5dc23d7914944d1c1e2731e7a2e4d9a1fb365&scene=21#wechat_redirect

##  第一周：监督学习和无监督学习
第三方笔记：https://mp.weixin.qq.com/s?__biz=MzIwOTc2MTUyMg==&mid=2247507430&idx=2&sn=5d1deb023b009c32cce3d37e37f2efac&chksm=976c787ba01bf16d15432a341cb0733e8012ebf5dc23d7914944d1c1e2731e7a2e4d9a1fb365&scene=21#wechat_redirect
### 1-1.监督学习 Supervised Learning
回归问题：人工智能根据数据集得出函数，该函数是连续函数，我们用真实数据用函数求值。  
分类问题：人工智能根据数据集得出函数，该函数是分段函数，我们用真实数据用函数求值，值结果会分为几类。  
应用：垃圾邮件、疾病分类。

### 1-2.无监督学习 Unsupervised Learning

与监督学习区别：监督学习的数据是有标签的。  

---
* 对于标签的理解：
对于监督学习来说，数据集是有正确答案的，函数y=f(x)，标签就是函数的解y。  
而无监督学习的数据集，只会输入X，它学习的结果是数据与数据间的关系。
---

聚类算法：  
应用：基因学的理解应用、社交网络分析、组织大型计算机集群、细分市场、新闻事件分类。

### 2.单变量线性回归 Linear Regression with One Variable
实质：学习得出的结果的函数是一元一次方程 $ h_\theta(x)=\theta_0+\theta_1x $。

### 3.代价函数
代价函数也称之为平方误差函数，平方误差代价函数。  
**实质**：算法预测结果与真实结果的平方误差求和后的平均值。  
公式：
$$ J(\theta_0, \theta_1)=\frac{1}{m}\sum_{i=1}^{m}(h_\theta(x^{(i)})-y^{(i)})^2 $$

---
* 虽然看到的有这么多参数，但实质上只有$ \theta_0 $、$ \theta_1 $两个参数。
* $ h_\theta(x^{(i)})=\theta_0+\theta_1x^{(i)} $： $ x^{(i)} $是常数数列，在数据集的X轴。$ h_\theta(x^{(i)}) $是预测值
* $ y^{(i)} $是常数数列， 在数据集的Y轴
---

目标：不断改变$ \theta_0, \theta_1 $，求$ min{J(\theta_0, \theta_1)} $  

代码函数直观解释1：设$ \theta_0=0 $，代价函数坍缩成二次曲线,此时$ h_\theta(x)=\theta_1x $,代价函数变为
$$
\begin{aligned}
    J(\theta_1)&=\frac{1}{m}\sum_{i=1}^{m}(\theta_1x^{(i)}-y^{(i)})^2 \\
    &=\frac{1}{m}\sum_{i=1}^{m}({x^{(i)}}^2\theta_1^2-2x^{(i)}y^{(i)}\theta_1+y^{{(i)}^2}) \\
    &=(\frac{1}{m}\sum_{i=1}^{m}{x^{(i)}}^2)\theta_1^2+(\frac{2}{m}\sum_{i=1}^{m}x^{(i)}y^{(i)})\theta_1+(\frac{1}{m}\sum_{i=1}^{m}{y^{(i)}}^2)
\end{aligned}
$$
代码函数直观解释2：代价函数是三维函数，绘制出等高线图。

### 4.梯度下降
求函数最小值的算法。  
**符号**：“：=”是更新赋值号，如$x:=x+1$代表新x值等于旧x值加1。