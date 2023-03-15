# BigData

## Hadoop

## crawler

### 爬虫

- 采集数据
- 与浏览器不同

	- 浏览器 渲染 数据
	- 爬虫 采集元数据

### 技术

- python

	- requests库

		- HTTP请求库
		- 发送请求
		- 获取响应数据

	- tqdm

- json

### requests

- 步骤

	- 导入

		- import

	- 发送请求

		- requests.get

	- 获得响应

		- response

- response

	- encoding
	- text
	- content

		- 二进制数据
		- decode()

### 正则表达式

- import re
- re.findall()

### Beautiful Soup

- 介绍

	- 从HTML和XML中提取数据

- 安装

	- bs4
	- lxml

- bs对象

	- 介绍

		- 待解析的整个文档树
		- 支持遍历与搜索文档树

	- 步骤

		- 创建

			- 导入模块

				- from bs4 import BeautifulSoup

			- 创建对象

				- soup=BeautifulSoup("<html>data</html>","lxml")

					- {1}
					- {2}

						- 指定解析器

- find

	- find(name="",attrs={},recursive=Trus,text=None,**kwargs)
	- findAll()

- Tag

	- name
	- attrs
	- text

### tqdm

- 进度条
- from tqdm import tqdm
- 使用

	- for i in tqdm(range(1000)):
    print("process::")
    pass
	- pbar=tqdm(range(1000))  
for i in pbar:
    pbar.set_description("Processing %s" % i)

