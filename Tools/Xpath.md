### 1. 什么是 Xpath

维基百科定义：XPath即为XML路径语言（XML Path Language），它是一种用来确定XML文档中某部分位置（定位）的计算机语言。

### 2. Xpath 工具

Firefox 火狐浏览器：使用 ChroPath 插件，可以协助我们对网页元素进行快速定位。

### 3. Xpath 定位方法
#### 3.1 绝对路径定位方法
在Xptah定位技术中，我们把从根节点一层一层地定位到需要被定位的页面元素的方法称为绝对路径定位法。实际工作中绝对路径定位法使用不多。

1) 从一段 HTML 代码开始：
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>自定义超链接标签</title>
</head>
<body>
我的第一个网页
<br>
<input id="u2" maxlength="8" type="text">
<br>
<a href="http://www.ptpress.com.cn/">人民邮电出版社</a>
</body>
</html>
```

2）以上代码通过 Firefox 浏览器打开之后，展示效果如下图所示：
![image](https://user-images.githubusercontent.com/29120566/145138506-37ff0bd5-7f9b-48c8-aba0-ae538476fc05.png)

3）选定上图中的输入框，单击鼠标右键选择“查看元素”，可以看到输入框对应的 HTML 代码为 input 节点
![image](https://user-images.githubusercontent.com/29120566/145153596-54455fa9-7003-4d27-9bb1-44df30282daf.png)

4）input 上一级为 body 节点，再上一级为 html 根节点，节点与节点之间用 / 进行分隔。在 ChroPath - Selectors 选项中中输入路径表达式 /html/body/input，按下 Enter 键后发现输入框被绿色的虚线框起来了，说明输入框被成功定位到了。下方文字提示为：1 element matching.
![image](https://user-images.githubusercontent.com/29120566/145153883-2a1d7ea2-32b2-4582-9d68-1e1b64447e92.png)

#### 3.2 相对路径定位方法

实际工作中比较常用的是相对路径定位方法，相对路径定位方法有以下几种：

**一、相对路径加 id 属性**

如果一个节点中含有 id 属性，因为 id 值是唯一的，应优先使用 id 属性进行定位。

它的基本格式：//任意节点[@id='属性值']。
- 表达式 1：//a[@id='login_home']
- 表达式 2：//*[@id='login_home']

以百度右上角的“登录”按钮为例：它对应的 HTML 代码为 a 节点，id 为 s-top-loginbtn，所以可以用表达式 //a[@id='s-top-loginbtn'] 进行定位
![image](https://user-images.githubusercontent.com/29120566/145156590-9dcf70d4-dff9-4776-8b81-71166caa8689.png)

**二、相对路径加非 id 属性**

如果节点中不包含 id 属性，但是存在其他唯一性的属性，也可以用于元素定位。

它的基本格式：//任意节点[@非id的任意属性='属性值']，如表达式：//input[@name='username']

百度页面，“辅助模式”按钮的 class 属性值“aging-entry-inner”具有唯一性，可以使用表达式 //div[@class='aging-entry-inner'] 进行定位

![image](https://user-images.githubusercontent.com/29120566/145157453-892bf81e-6a4f-4cf9-9d12-25a301fe97d1.png)

**三、相对路径加 contains() 函数进行元素定位**

如果节点既不包含 id 属性，其他属性也不是唯一，但是包含文本信息，且该文本信息具有唯一性，则可以使用文本信息进行定位。

它的基本格式：//包括有文本信息的节点[contains(text (),'文本信息')]，如表达式：//a[contains(text(),'新闻活动')]
其他格式：//a[contains(.,'新闻活动')]；//a[test()='新闻活动')] 同样可以定位到该元素（注：2021.12.08 日尝试这两种表达式，前者在 ChroPath 可以定位到元素；后者不可以）

百度页面，“使用百度前必读”为唯一性的文本信息，可以使用表达式 //a[contains(text(),'使用百度前必读')] 进行定位
![image](https://user-images.githubusercontent.com/29120566/145157993-6cfc3d7e-9420-4b9b-b87e-101beebe0e67.png)

**四、相对路径加非 id 属性加 contains() 函数进行元素定位**

如果一个节点既没有id属性，其他属性和属性值也不唯一，而且contains(text (),'')函数中包括的文本信息也不唯一，那么还可以使用相对路径加非id属性加contains(text (),'')函数的方式进行联合定位，因为三者联合在一起时可能就具有唯一性了。

它的基本格式：//包含有文本信息的节点[@非id的任意属性='属性值'] [contains(text(),'文本信息')]，如表达式：//a[@href='https://www.epubit.com'][contains(text(),'异步社区’)]

百度页面，“贴吧”菜单，可以使用表达式 //a[@class='mnav c-font-normal c-color-t'][contains(text(),'贴吧')] 进行定位

**五、通过 ChroPath 工具自动生成相对路径表达式**

上面的方法需要自己去写表达式，实施较为繁琐。其实只要在 Firefox 上安装 ChroPath 工具，它可以自动生成相对路径表达式，如下图所示：

![image](https://user-images.githubusercontent.com/29120566/145159620-d3bb453e-5c95-4210-8281-94a6d40bb2c1.png)

### 4. Reference
https://weread.qq.com/web/reader/3373200071cc7fa03373f1ekd8232f00235d82c8d161fb2
