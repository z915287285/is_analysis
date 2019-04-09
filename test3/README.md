实验3 图书管理系统领域对象建模
=========================
| 学号         | 班级         | 姓名 | 图片 |
|--------------|--------------|------|------|
| 201610414330 | 软件(本)16-3 | 朱泓超 |![image](https://github.com/z915287285/is_analysis/blob/master/test1/zz.jpg)    |
## 实验目的
+ 目的是掌握领域对象建模中类图的作用，并能用PlantUML工具绘制类图。
+ 仔细阅读并理解第8章领域对象建模。
+ 根据实验2：图书管理系统用例建模，分析并找出用例及流程中需要的类。
+ 绘制出图书管理系统的主要类图(class diagram)以及一些类的对象图(object diagram)
+ 用PlantUML标准工具画出图书管理系统的类图（如教材Page170的图8.17），对象图（如教材Page173的图8.21）
+ 整个文档要汇总到REMADE.md文本文件中进行说明，说明文件用Markdown格式编写。
##  图书管理系统的类图
-------------------------
### 1.1 类图plantUML源码如下：
```
@startuml
class 图书管理员{
姓名
员工号
}
class 添加图书{
账单
书籍种类
}
class 图书编目{
资源名称
国际出版号
所在书架编号
}
class 维护图书
class 淘汰旧书
class 登记赔偿
class 借出图书{
借书日期
归还日期
}
class 读者{
姓名
学号
联系方式
已借图书数
}
class 登录
class 维护读者信息
class 预定图书
class 信息管理
class 借书记录
class 个人基本信息管理

图书管理员 -- 维护读者信息

图书管理员 -- 登记赔偿:1
图书管理员 - 维护图书:1           1...*
图书管理员 -- 借出图书
维护图书 <|-- 添加图书
维护图书 <|-- 图书编目
维护图书 <|- 淘汰旧书
借出图书 *-- 预定图书
信息管理- 预定图书:1             *
信息管理 -- 登录
登录 *-- 读者:1
信息管理 o-- 借书记录
信息管理 o-- 个人基本信息管理
@enduml
```
### 1.2.类图如下
![image](https://github.com/201610414311/is_analysis/blob/master/test3/class.png)
### 1.3.类图说明
<h4>该类图列出了图书馆系统的主要类，及其类之间的依赖关系、聚合关系、组合关系等。从类图中可以很
清楚的看出维护图书、登记赔偿、借出图书、维护读者信息等类都是依赖于图书管理员这个类来实现的。还有
读者类与登录类之间的组合关系，读者通过登录图书管理系统之后才能继续预定书、信息管理等类的操作。

2：图书馆系统的对象图
-------------------------
### 2.1 类图书管理员的对象图
<h4>源码如下：
```
@startuml


object 图书管理员 {
  姓名
  员工号
}
@enduml
```
<h4>对象图如下:
![image](https://github.com/201610414311/is_analysis/blob/master/test3/object1.png)
### 2.2 类读者的对象图
<h4>源码如下:
```
@startuml

object 读者 {
  姓名
  学号
  联系方式
}
@enduml
```
<h4>类图如下:
![image](https://github.com/201610414311/is_analysis/blob/master/test3/object2.png)
### 2.3 类添加图书的对象图
<h4>源码如下:
```
@startuml
object 添加图书{
种类
价格
出版社
}
@enduml
```
<h4>类图如下:
![image](https://github.com/201610414311/is_analysis/blob/master/test3/object3.png)
### 2.4  借出图书类的对象图
<h4>源码如下:
```
@startuml
object 借出图书{
借书日期
归还日期
书号
借书人姓名
借书人学号
借书人联系方式
}
@enduml
```
<h4>对象图如下:
![image](https://github.com/201610414311/is_analysis/blob/master/test3/object4.png)
### 2.5 信息管理类的对象图
<h4>源码如下：
```
@startuml
object 信息管理{
用户姓名
用户学号
用户联系方式
借书记录
还书记录
}
@enduml
```
<h4>对象图如下:
![image](https://github.com/201610414311/is_analysis/blob/master/test3/object5.png)
