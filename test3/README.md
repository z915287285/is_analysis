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
### 类图plantUML源码如下：
```
@startuml
class Person {
  String Name
  String Sex
  int Age
  String Number
  String address
  String Email
}
class Library_Admin {
  String Library_Admin_ID
  Boolean Library_Admin_AddBookInfo()
  Boolean Library_Admin_DeleteBookInfo()
  Boolean Library_Admin_UpdateBookInfo()
  Boolean Library_Admin_SelectBookInfo()
  Boolean Library_Admin_LendBook()Boolean
  Boolean Library_Admin_ReturnBook()
  Boolean Library_Admin_SelectReaderState()
}
class InfoManager {
  String InfoManager_ID
  Boolean InfoManager_AddReaderInfo()
  Boolean InfoManager_DeleteReaderInfo()
  Boolean InfoManager_UpdateReaderInfo()
  Boolean InfoManager_SelectReaderInfo()
  Boolean InfoManager_AddLibrary_AdminInfo()
  Boolean InfoManager_DeleteLibrary_AdminInfo()
  Boolean InfoManager_UpdateLibrary_AdminInfo()
  Boolean InfoManager_SelectLibrary_AdminInfo()
}
class Reader {
  String Reader_ID
  String State
  String SelectState()
  Book SelectBook()
  Boolean BorrowBook()
  Boolean BackBook()
  Boolean LateApplication()
  Boolean CompensationBook()
}
class Book {
  String ISBA
  String Name
  String Category
  String Publisher
  String Published-Date
}
Person <|-- Library_Admin
Person <|-- InfoManager
Person <|-- Reader


Book - "*"预定记录:被预定
Library_Admin"*" - "1"InfoManager:授权
Reader"*" - "1"Library_Admin:注册
Reader"1" - "*"预定记录
Reader--借书记录
Reader--还书记录
借书记录"1" -- "0.1"逾期记录
借书记录"*" - "1"Library_Admin:登记

逾期记录"*" - "0.1"罚款细则:使用

class 预定记录{
预定日期
}
class 借书记录{
借书日期
归还日期
}
class 还书记录{
归还日期
}
class 逾期记录{
逾期天数
}

class 罚款细则{
}


@enduml
```
### 类图如下
![image](https://github.com/z915287285/is_analysis/blob/master/test3/class.png)
### 类图说明
+ 该类图列出了图书馆系统的主要类，及其类之间的依赖关系、聚合关系、组合关系等。
+ 从类图中可以很清楚的看出维护图书、登记赔偿、借出图书、维护读者信息等类都是依赖于图书管理员这个类来实现的。
+ 还有读者类与登录类之间的组合关系，读者通过登录图书管理系统之后才能继续预定书、信息管理等类的操作。

## 图书馆系统的对象图
-------------------------
### 图书管理员的对象图
### 源码如下：
```
@startuml
object Library_Admin {
  Library_Admin_ID="L001"
  Name="李轻柔"
  Sex="女"
  Age=25
  Number="13699675688"
  address="四川省成都市龙泉驿"
  Email="zz@163.com"
}
@enduml
```
### 对象图如下:
![image](https://github.com/z915287285/is_analysis/blob/master/test3/object4.png)
### 读者的对象图
### 源码如下:
```
@startuml
object Reader {
  Reader_ID="000021"
  Name="陈光"
  Sex="男
  Age=20
  Number="13678654955"
  address="四川省成都市龙泉驿"
  Email="7895@163.com"
  State="No"
}
@enduml
```
### 对象图如下:
![image](https://github.com/z915287285/is_analysis/blob/master/test3/object3.png)
### 图书的对象图
### 源码如下:
```
@startuml
object Book {
  ISBA=" 978-7-111-60046-6"
  Name="PaddlePaddle深度学习实战 "
  Category="计算机技术"
  Publisher=" 北京：机械工业出版社"
  Published-Date="2018.06"
}
@enduml
```
### 对象图如下:
![image](https://github.com/z915287285/is_analysis/blob/master/test3/object1.png)
### 信息管理员的对象图
### 源码如下:
```
@startuml
object InfoManager {
  InfoManager_ID="001"
  Name="刘辉"
  Sex="男"
  Age=30
  Number="17699654688"
  address="成都市青白江区"
  Email="ppq@163.com"
}
@enduml
```
### 对象图如下:
![image](https://github.com/z915287285/is_analysis/blob/master/test3/object2.png)
