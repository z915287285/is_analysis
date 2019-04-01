实验2 图书管理系统用例建模
=========================
| 学号         | 班级         | 姓名 | 图片 |
|--------------|--------------|------|------|
| 201610414330 | 软件(本)16-3 | 朱泓超 |![image](https://github.com/z915287285/is_analysis/blob/master/test1/zz.jpg)    |
## 实验目的
+ 理解用例(Use Case)的意义和作用，并能用PlantUML工具绘制用例图。
+ 仔细阅读并理解第7章用例建模。
+ 以教材中图书管理系统的用例为基础，根据自己的理解，再增加或者修改一些参与者(actor)和用例(usecase)，设计一套比较完整的图书管理系统的全部用例。
+ 用PlantUML标准工具画出图书管理系统整体的用例关系图(如图7.6)，并写出每个用例的规约表（见表7.5）。
+ 整个文档要汇总到REMADE.md文本文件中进行说明，说明文件用Markdown格式编写。

## 图书管理的用例关系
### Puml代码如下:
````
@startuml
left to right direction
skinparam packageStyle rectangle
rectangle {
actor Library_Admin
}
rectangle {
actor Reader
}
rectangle 图书管理系统用例关系图分析{
rectangle {
Library_Admin ->(Lend Book):借书登记
Library_Admin -->(Return Book):归还书籍登记
Library_Admin -->(Manage Book):书籍信息管理
Library_Admin -->(Manage ReaderInfo):读者信息管理
}
rectangle {
(Select Book)<-- Reader:读者查询书籍信息
(Select State)<-- Reader:读者查看当前借阅状态
(Borrow Book)<-- Reader:借阅书籍
(Back Book)<-- Reader:归还书籍
(Late application)<-- Reader:逾期申请
(Compensation book)<--Reader:赔偿书籍
}
}

@enduml
````


[代码链接](https://github.com/z915287285/is_analysis/blob/master/test2/usercase.puml)
关系用例图:
![image](https://github.com/z915287285/is_analysis/blob/master/test2/usercase.png)

## 参与者说明