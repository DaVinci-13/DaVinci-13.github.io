---
title: Artificial Intelligence
layout: test
permalink: /ai/
---

# AI

## python

### jupyter

## ml

### Machine Learning

- 黑马

	- 数据集

		- 学习用

			- scikit-learn

				- 工具

			- kaggle
			- UCI

		- sklearn

			- 获取

				- from sklearn.datasets
				- 小数据集

					- sklearn.datasets.load_*()

				- 大规模数据集

					- sklearn.datasets.fetch_*(data_home=None, subset="train")

						- subset

							- train
							- all
							- test

			- 返回

				- datasets.base.Bunch

					- 继承于dict

			- 测试集划分

				- from sklearn.model_selection
				- x_train, x_test, y_train, y_test=train.test.split(iris.data, iris.target, test_size=0.2,   random_state=22) 

					- 输入

						- iris.data

							- ·特征值

						- iris.target

							- 目标值

						- test_size

							- 测试集大小
							- float

						- random_state

							- 随机数种子

					- 返回

						- 训练集特征值
						- 训练集目标值
						- 测试集特征值
						- 测试集目标值

		- 数据集

			- 特征值
			- 目标值

	- 特征工程

		- 工具

			- sklearn

				- 特征工具

			- pandas

				- 数据清洗
				- 数据处理

		- 文本特征提取

			- DictVectorizer 特征提取

				- 转换json数据为字典

					- 特征提取字典

				- from sklearn.feature_extraction import DictVectorizer
				- transfer=DictVectorizer(sparse=True)

					- sparse:系数矩阵

				- data_new=transfer.fit_transform(data)
				- feature=transfer.get_feature_names()

					- 得到特征名

			- CountVectorizer 统计特征字符（英文）

				- from sklearn.feature_extraction.text import CountVectorizer
				- transfer=CountVectorizer(stopword=[])
				- data_new=transfer.fit_transform(data)
				- data_new.toarray()
				- feature=transfer.get_feature_names()

					- 得到特征名

				- 需要分词/加空格

					- 常用于英文

			- jieba 中文

				- a=jieba.cut(str)
				- return " ".join(a)
				- CountVectorizer……

			- Tf-idf文本特征提取

				- tfidf=tf*idf

					- tf

						- 给定词/文章所有词

					- idf

						- lg(总文件数目/包含该词文件数目)

					- 词频-逆向文档频率

				- 重要程度

					- 某个词在一篇文章出现过高，在其他文章出现低

				- TfidfVectorizer

					- from sklearn.feature_extraction.text import TfidfVectorizer
					- transfer=TfidfVectorizer(stopword=[])
					- data_new=transfer.fit_transform(data)
					- data_new=transfer.inverse_transform(data)
					- feature=transfer.get_feature_names()

		- 特征预处理

			- 原因

				- 欧氏距离

					- 平方和开根
					- 

				- 取决于

			- 无量纲化

				- 归一化

					- 把数据缩放映射到[0,1]
					- 方法

						- sklearn.processing.MinMaxScaler(feature_range=[0,1])
						- MinMaxScaler.fit_transform(data)

							- data

					- 缺点

						- 异常值

							- 最大最小值距离整体数值区域远

						- 鲁棒性差

							- 只适合精确小场景

				- 标准化

					- 把原始数据变换到均值为0方差为1的区间
					- 
					- 方法

						- sklearn.processing.StandScaler()
						- standScaler.fit_transform(data)

					- 适用于样本数据足够多、比较稳定、现代嘈杂大数据场景

		- 降维

			- 维数：特征个数
			- 结果

				- 不相干的主要特征

			- 方法

				- 特征选择

					- 原有数据中去除冗余或相关变量，找出主要特征
					- 方法

						- Fliter 过滤式

							- 方差选择法：过滤低方差特征

								- sklearn.feature_selection.VarianceThreshold(threshold=0.0)

									- threshold=0.0

										- 保留所有非方差特征
										- 删除所有具有相同值的特征

								- varilance.fit_transform(data)

							- 相关系数

								- from scipy.stats import pearsonr
								- 结果

									- [-1,1]
									- >0：正相关
									- <0：负相关
									- =0：不相关

								- 处理

									- 两个特征相关系数很高

										- 选取其一
										- 加权求和
										- 主成分分析

						- Embedded

							- 嵌入式

				- 主成分分析PCA

					- 高维特征转化为低维特征

						- 数据维数压缩
						- 舍弃原有数据，创造新的变量
						- 尽可能降低数据维数
						- 损失少量数据信息

					- 应用

						- 回归分析
						- 聚类分析

					- 方法

						- sklearn.decomposition.PCA(n_components=None)

							- n_components

								- 小数：保留百分之多少
								- 整数：减少到多少特征

						- PCA.fit_transform(data)

- cs229 Andrew.Ng

	- What is

		- Supervised Learning

			- Linear Regression

				- e.g.

					- House price prediction

			- Classification

				- e.g.

					- Breast cancer detection

				- pre defined

		- Upsupervised Learning

			- Clustering

				- e.g.

					- finding the articles and grouping
					- grouping customers

				- group

					- not pre-define
					- auto finding

			- Anomaly detection

				- find unusal data points
				- e.g.

					- fraud detection in financial system

			- Dimensionality reduction

				- Cocktail

	- logic

		- training set

			- features
			- targets

		- learning algorithm
		- f:function

			- f

				- model

			- x

				- input

			- \hat{y}

				- output
				- prediction
				- estimated y

			- y

				- target

	- Linear Regression with One Variable

		- f(x)=wx+b

	- Cost Function

### Deep Learning

- 介绍

	- 与ml的不同

		- 兼顾特征抽取（feature extradiction）与分类（classicification）
		- 通过神经网络自动进行特征提取

			- feature不需要人工参与

		- 因此可用于不好进行特征提取的方向

			- 图像
			- 语音
			- 自然语言处理

	- 数据量与计算性

		- 需要大量的训练数据集
		- 需要大量的算力

			- 可能花费数天及数周时间得到神经网络模型

- TensorFlow

	- API

		- import tensorflow as tf
		- 常量

			- t=tf.constant(2)

		- 会话

			- 默认图

				- with tf.session() as sess:
     value=sess.run(t+t)
     print(value)

		- 日志

			- import os
os.environ['TF_CPP_MIN_LOG_LEVEL']=2

	- 结构

		- 构建图

			- 张量 Tensor
			- 操作 OP

		- 执行图

	- 介绍

		- 采用数据流图

	- 图

		- 默认图

			- 查看

				- 调用方法：tf.get_default_graph
				- 查看属性：op/sess.graph

		- 创建图

			- new_g=tf.graph()
with new_g.as_default():
     print(value)
with tf.session(graph=new_g) as sess:
     value=sess.run(t+t)
     print(value)

		- 可视化

			- 数据序列化-生成events文件

				- tf.summary.FileWriter(path,graph)

			- 启动tensorboard

				- tensorboard --logdir=path

	- OP 操作

		- 指令名称

			- 每个图有一个独立的命名空间

		- 重命名

			- name属性

	- Sess 会话

		- 开启

			- tf.Session
			- tf.interactiveSession

		- init

			- 上下文管理器

				- with 语句
				- session.close()

			- target

				- 远程服务器
				- 默认留空

			- graph

				- 默认图

			- config

				- tf.ConfigProto
				- 打印设备信息
				- 控制会话行为

		- run

			- fetches

				- session.run(c)
				- c.eval

			- feed_dict

				- placeholder 占位符

		- error

			- RuntimeError
			- TypeError
			- ValueError

	- Tensor 张量

		- 属性

			- type 类型
			- shape 形状/阶

				- 

			- 概念

				- ndarray

		- 创建

			- tf.zeros()
			- tf.ones()
			- tf.constant()

		- 变换

			- 类型改变

				- tf.cast()

			- 形状改变

				- 静态形状

					- 初始创建张量时的形状
					- tf.set_shape(shape)
					- 形状没有完全固定

				- 动态形状

					- tf.reshape(tensor,shape)
					- 返回新张量
					- 保证shape中元素的数量前后一致

		- 数学运算

			- tf.matmul(x,w)
			- tf.square(error)
			- tf.reduce_mean(error)

	- 变量OP

		- 作用

			- 存储持久化
			- 可修改值
			- 可指定被训练

		- 创建

			- tf.Variable()

				- trainable

					- 是否能被训练

		- 初始化

			- tf.global_variables_initializer()
			- 作用于全局变量

		- 命名空间

			- with tf.variabble_scope(NAME):
			- 使结构清晰

	- API

		- 基础

			- app

				- 入口，main函数

			- image
			- gfile

				- 文件操作

			- summary

				- 生成日志

			- python_io

				- 读写TFRecords文件

			- train
			- nn

		- 高级

			- keras

				- 快速构建模型

			- layers

				- 高级概念层定义模型

			- contrilb

				- 构建计算图的高级操作

			- estimator

				- Model+Training+Evaluate

	- 训练

		- 训练次数，学习率

			- 梯度爆炸

		- 模型存储

			- saver=tf.train.Saver(var_list,max_to_keep)

				- var_list

					- 保存变量列表

				- max_to_keep

					- 保存最近几个检查点

			- server.save(sess,path)
			- server.restore(sess,path)

	- TensorBoard显示

		- 创建事件文件

			- tf.summary.FileWriter(path,graph)

		- 收集变量

			- tf.summary.

				- scalar

					- 标量
					- 如损失度，准确率等

				- histogram

					- 直方图与

				- image

		- 合并变量

			- merged=tf.summary.merge_all()
			- summary=sess.run(merged)

		- 迭代运行写入事件

			- FileWriter.add(summary,iter)

	- 命令行

		- tf.app

			- flags
			- run()

				- 自动运行python文件中的main函数

	- 面向对象

### 理论

- 机器学习

	- 特征工程

		- 数据集

			- 划分

				- 训练集
				- 验证集
				- 测试集

	- 监督学习和无监督学习

		- 监督学习

			- 有标签
			- 回归

				- e.g.

					- 线性回归

						- 拟合

							- 过拟合

								- 验证误差大，训练误差小
								- 引入更多特征
								- 多项式特征
								- 减弱正则化

							- 欠拟合

								- 训练误差和验证误差都很大
								- 增加样本
								- 去除非主要特征
								- 加强正则化

				- 指标

					- 平均绝对值误差MAE

						- 预测值与观测值误差均值

					- 均方误差MSE

						- 预测值与观测值的平方期望

					- 均方根误差RMSE

						- 样本标准差
						- 样本离散程度
						- 越小越好

			- 分类

				- e.g.

					- 逻辑回归

						- 寻找边界

					- 决策树
					- KNN
					- 朴素贝叶斯
					- SVM

						- 线性分类器
						- 支持向量

							- 离超平面最近的一些点

						- 超平面

							- 间隔最大化

								- 尽可能原理两边数据

							- 只与支持向量有关

						- 优化

							- 核函数

								- 映射到高维空间

				- 指标

					- 准确率
					- 精确率
					- 召回率/查全率
					- F1-score

		- 无监督学习

			- e.g.

				- K-meas

					- 牧师-村民问题
					- 步骤

						- 刚开始随机中心
						- 重新计算中心
						- 稳定

							- 停止条件

								- 迭代次数
								- 最小误差

					- 复杂度
					- 优缺

						- 聚类

							- 局部最优

						- 伸缩性
						- 算法复杂度低
						- 不适合多分类

							- 一个点被分成多类

						- 参数影响结果

							- k值
							- 初始中心

						- 异常值敏感

					- 优化

						- 数据预处理

							- 去除异常点
							- e.g

								- 标准化
								- 归一化

						- 合理选择k值
						- 核函数
						- 高维映射

				- PCA

			- 无标签

		- 半监督学习

			- 少量有标签大量无标签
			- 分类

				- 纯半监督学习
				- 直推学习

	- BP神经网络

		- 激活函数

			- e.g.

				- sigmod

					- 二分类

				- tanh
				- relu

			- 非线性

	- 集成算法

		- bagging

			- 并行

		- boosting

			- 下一次迭代用上一次结果

		- stacking

			- 测试集和验证集

- 深度学习

	- DNN
	- CNN

		- cv
		- e.g.

			- LeNet
			- AlexNet
			- VGGNet
			- Google Inception Net
			- Resnet

	- GAN
	- RNN

- 迁移学习
- 强化学习
- 人工智能

## dl

### CV

- cs231n
- Fei-Fei Li

### NLP

