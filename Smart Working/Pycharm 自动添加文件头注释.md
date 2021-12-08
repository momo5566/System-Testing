## 1. 环境

硬件环境：ThinkPad Intel(R) Core(TM) i5-6200U CPU @ 2.30GHz 2.40 GHz

软件环境：Windows 10 专业版；Pycharm 2021.1.2(Community Edition)

## 2. 效果

创建 .py 文件时，自动添加文件头部信息，包括指定 UTF-8 编码格式、文件创建时间、创建人、文件名、软件环境。效果图展示如下：
![image](https://user-images.githubusercontent.com/29120566/145180729-c3e5d137-656c-48ab-b6c7-4df3192a39f1.png)

## 3. 步骤
1）按路径选择：Pycharm ->> File ->> Settings ->> Editor ->> File and Code Templates ->> Python Script
![image](https://user-images.githubusercontent.com/29120566/145181038-2d2b3250-3e60-4826-9b68-025b7ad8cbba.png)

2）选择 Python Script 后，在右方输入以下代码，点击 OK
```
# -*-coding=utf-8-*-
# @Time: ${DATE} ${TIME}
# @Author: ${USER}
# @File: ${NAME}.py
# @Software: ${PRODUCT_NAME}
```

3）创建 .py 文件之后，就会自动添加文件头信息了。
