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
actor InfoManager
}
rectangle {
actor Reader
}
rectangle 图书管理系统用例关系图分析{
rectangle {
Library_Admin ->(Lend Book):借书登记
Library_Admin -->(Return Book):归还书籍登记
Library_Admin -->(Manage Book):书籍信息管理
Library_Admin -->(Select ReaderState):查询读者借阅状态
}
rectangle {
InfoManager -->(Manage ReaderInfo):读者信息管理
InfoManager -->(Manage Library_AdminInfo):图书管理员信息管理
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

@enduml
````


[PUML代码链接](https://github.com/z915287285/is_analysis/blob/master/test2/usercase.puml)


关系用例图:

![image](https://github.com/z915287285/is_analysis/blob/master/test2/usercase.png)

## 参与者说明
### 1. Library_Admin(图书管理员)

主要职责是对图书基本信息的管理，对读者借阅状态的查看并做好借阅与归还书籍的登记。

### 2. InfoManager(信息管理员)

主要职责是对图书管理员个人信息，以及读者个人信息做相关管理维护。

### 3. Reader(读者)

主要职责是拥有查阅书籍并借阅，归还书籍的权利，但在借阅书籍前得先查看个人的借阅状态，无征信问题便可借阅。同时还有归还图书逾期申请。
当书籍损坏或者丢，将按照当前规定进行赔偿。

## 用例规约表
## **Library_Admin(图书管理员)**
### 1. “借书登记”用例
“借书登记”用例规约

“借书登记”用例流程图[源码](https://github.com/z915287285/is_analysis/blob/master/test2/usercase1-1_flow.puml)如下:

````
@startuml
start
:Library_Admin;
if (Select ReaderState) then(已借阅)
end
else(未借阅)
:Lend Book;
stop
@enduml
````

“借书登记”用例流程图

![image](https://github.com/z915287285/is_analysis/blob/master/test2/usercase1-1_flow.png)

### 2. “归还书籍登记”用例

“归还书籍登记”用例规约

“归还书籍登记”用例流程图[源码](https://github.com/z915287285/is_analysis/blob/master/test2/usercase1-2_flow.puml)如下:
````
@startuml
start
:Library_Admin;
if (Select ReaderState) then(未借阅)
end
else(已借阅)
:Return Book;
stop
@enduml
````
“归还书籍登记”用例图

![image](https://github.com/z915287285/is_analysis/blob/master/test2/usercase1-2_flow.png)


### 3. “书籍信息管理”用例
主要职责是
### 4. “查阅读者借阅状态”用例

## **InfoManager(信息管理员)**
### 1. “读者信息管理”用例

### 2. “图书管理员信息管理”用例

## **Reader(读者)**
### 1. “读者查阅书籍信息”用例

### 2. “读者查看当前借阅状态”用例

### 3. “借阅书籍”用例

### 4. “归还书籍”用例

### 5. “逾期申请”用例

### 6. “赔偿书籍”用例