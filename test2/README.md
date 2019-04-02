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
 
用例名称|借书登记
--------|-------
参与者|图书管理员 读者
前置条件|图书管理员被授权
后置条件|存储借书记录，更新库存
主事件流|验证读者有无未归还书籍<br>图书管理员将读者借阅信息录入系统
备注|图书馆开架借阅，读者找到书后办理借阅书手续

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



用例名称|归还借书登记
--------|-------
参与者|图书管理员 读者
前置条件|图书管理员被授权
后置条件|存储归还记录，更新库存
主事件流|验证读者有无未归还书籍<br>图书管理员将读者归还信息录入系统
备注|需要在读者有未归还书籍，才可归还

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

“书籍信息管理”用例规约

用例名称|书籍信息管理
--------|-------
参与者|图书管理员
前置条件|图书管理员得到上级批准
后置条件|商家有图书馆所需书籍
主事件流|1.图书管理员将新图书信息录入系统<br>2.图书管理员将删除特定图书信息<br>3.图书管理员将查看图书信息<br>4.图书管理员将更新图书信息
备注|信息管理员给予权限之后，图书管理员可直接添加，修改，删除以及更新图书信息

“书籍信息管理”用例流程图[源码](https://github.com/z915287285/is_analysis/blob/master/test2/usercase1-3_flow.puml)如下:
````
@startuml
start
:Library_Admin;
fork
:查阅书籍;
fork again
:增加书籍;
fork again
:删除书籍;
fork again
:替换书籍;
end fork
stop

@enduml
````
“书籍信息管理”用例图

![image](https://github.com/z915287285/is_analysis/blob/master/test2/usercase1-3_flow.png)




### 4. “查阅读者借阅状态”用例

“查阅读者借阅状态”用例规约

用例名称|查阅读者借阅状态
--------|-------
参与者|图书管理员
前置条件|图书管理员得到上级批准
后置条件|可更新当前读者借阅状态
主事件流|图书管理员将验证读者当前的借阅图书状态
备注|信息管理员给予权限之后，图书管理员可直接验证读者借阅状态

“查阅读者借阅状态”用例流程图[源码](https://github.com/z915287285/is_analysis/blob/master/test2/usercase1-4_flow.puml)如下:
````
@startuml
start
:Library_Admin;
:Select ReaderState;
stop
@enduml
````
“查阅读者借阅状态”用例图

![image](https://github.com/z915287285/is_analysis/blob/master/test2/usercase1-4_flow.png)


## **InfoManager(信息管理员)**
### 1. “读者信息管理”用例

“读者信息管理”用例规约

用例名称|读者信息管理
--------|-------
参与者|信息管理员
前置条件|无
后置条件|可更新读者信息
主事件流|1.信息管理员将新读者信息录入系统<br>2.信息管理员将删除特定读者信息<br>3.信息管理员将查看读者信息<br>4.信息管理员将更新读者信息
备注|信息管理员可直接更新验证读者信息

“读者信息管理”用例流程图[源码](https://github.com/z915287285/is_analysis/blob/master/test2/usercase2-1_flow.puml)如下:
````
@startuml
start
:Library_Admin;
:Select ReaderState;
stop
@enduml
````
“读者信息管理”用例图

![image](https://github.com/z915287285/is_analysis/blob/master/test2/usercase2-1_flow.png)


### 2. “图书管理员信息管理”用例

“图书管理员信息管理”用例规约

用例名称|读者信息管理
--------|-------
参与者|信息管理员
前置条件|无
后置条件|可更新图书管理员信息
主事件流|1.信息管理员将新图书管理员信息录入系统<br>2.信息管理员将删除特定图书管理员信息<br>3.信息管理员将查看图书管理员信息<br>4.信息管理员将更新图书管理员信息
备注|信息管理员可直接更新验证图书管理员信息

“图书管理员信息管理”用例流程图[源码](https://github.com/z915287285/is_analysis/blob/master/test2/usercase2-2_flow.puml)如下:
````
@startuml
start
:Library_Admin;
:Select ReaderState;
stop
@enduml
````
“图书管理员信息管理”用例图

![image](https://github.com/z915287285/is_analysis/blob/master/test2/usercase2-2_flow.png)

以上两个用例图合并[源码](https://github.com/z915287285/is_analysis/blob/master/test2/usercase2_flow.puml)

````
@startuml
start
:InfoManager;
if()then(读者信息管理)
fork
:增加读者信息;
fork again
:删除读者信息;
fork again
:查询读者信息;
fork again
:修改读者信息;
end fork
else(图书管理员信息管理)
fork
:增加图书管理员信息;
fork again
:删除图书管理员信息;
fork again
:查询图书图书管理员信息;
fork again
:修改图书图书管理员信息;
end fork
endif
stop

@enduml
````

以上两个用例图合并

![image](https://github.com/z915287285/is_analysis/blob/master/test2/usercase2_flow.png)

## **Reader(读者)**
### 1. “读者查阅书籍信息”用例

“读者查阅书籍信息”用例规约

用例名称|读者查阅书籍信息
--------|-------
参与者|读者
前置条件|读者得到信息管理员授权
后置条件|可查看图书信息
主事件流|读者可查看当前书籍信息
备注|信息管理员给予权限之后，读者可直接查看图书信息

“读者查阅书籍信息”用例流程图[源码](https://github.com/z915287285/is_analysis/blob/master/test2/usercase3-1_flow.puml)如下:
````
@startuml
start
:Reader;
:Select Book;
stop
@enduml
````
“读者查阅书籍信息”用例图

![image](https://github.com/z915287285/is_analysis/blob/master/test2/usercase3-1_flow.png)


### 2. “读者查看当前借阅状态”用例

“读者查看当前借阅状态”用例规约

用例名称|读者查看当前借阅状态
--------|-------
参与者|读者
前置条件|读者得到信息管理员授权
后置条件|可查看借阅信息
主事件流|读者可查看当前借阅状态<br>图书管理员可验证当前借阅状态
备注|信息管理员给予权限之后，读者可直接查看当前借阅信息

“读者查看当前借阅状态”用例流程图[源码](https://github.com/z915287285/is_analysis/blob/master/test2/usercase3-2_flow.puml)如下:
````
@startuml
start
:Reader;
if (Select ReaderState) then(未借阅)
:可借阅书籍;
else(已借阅)
:需归还书籍;
endif
stop
@enduml
````
“读者查看当前借阅状态”用例图

![image](https://github.com/z915287285/is_analysis/blob/master/test2/usercase3-2_flow.png)


### 3. “借阅书籍”用例

“借阅书籍””用例规约

用例名称|借阅书籍
--------|-------
参与者|读者 图书管理员
前置条件|读者得到信息管理员授权，图书管理员获得授权
后置条件|借阅书籍，更新库存
主事件流|>图书管理员可验证当前借阅状态,并将信息录入系统<br>读者可借阅书籍
备注|信息管理员给予权限之后，读者可直接办理借阅手续

“借阅书籍””用例流程图[源码](https://github.com/z915287285/is_analysis/blob/master/test2/usercase3-3_flow.puml)如下:
````
@startuml
start
:Reader;
if (Select ReaderState) then(未借阅)
:Borrow Book;
else(已借阅)
:需归还书籍后才可借阅;
endif
stop
@enduml
````
“借阅书籍””用例图

![image](https://github.com/z915287285/is_analysis/blob/master/test2/usercase3-3_flow.png)


### 4. “归还书籍”用例

“归还书籍”用例规约

用例名称|归还书籍
--------|-------
参与者|读者 图书管理员
前置条件|读者得到信息管理员授权，图书管理员获得授权
后置条件|归还书籍，更新库存
主事件流|>图书管理员可验证当前借阅状态,并将更新读者信息<br>读者可归还书籍书籍
备注|信息管理员给予权限之后，读者可直接办理书籍归还手续

“归还书籍”用例流程图[源码](https://github.com/z915287285/is_analysis/blob/master/test2/usercase3-4_flow.puml)如下:
````
@startuml
start
:Reader;
if (Select ReaderState) then(未借阅)
else(已借阅)
:Back Book;
endif
stop
@enduml
````
“归还书籍”用例图

![image](https://github.com/z915287285/is_analysis/blob/master/test2/usercase3-4_flow.png)


### 5. “逾期申请”用例

“逾期申请”用例规约

用例名称|逾期申请
--------|-------
参与者|读者 图书管理员
前置条件|读者得到信息管理员授权，图书管理员获得授权
后置条件|更新读者信息
主事件流|>读者查阅当前借阅信息并<br>读者提交逾期申请<br>图书管理员可验证当前借阅状态,并将更新读者信息<br>读者可延期归还书籍
备注|信息管理员给予权限之后，读者可办理逾期归还书籍手续

“逾期申请”用例流程图[源码](https://github.com/z915287285/is_analysis/blob/master/test2/usercase3-5_flow.puml)如下:
````
@startuml
start
:Reader;
if (Select ReaderState) then(未借阅)
else(已借阅)
if(无法按时归还)then(Yes)
:Late application;
else(No)
:Back Book;
endif
endif
stop
@enduml
````
“逾期申请”用例图

![image](https://github.com/z915287285/is_analysis/blob/master/test2/usercase3-5_flow.png)


### 6. “赔偿书籍”用例

“赔偿书籍”用例规约

用例名称|逾期申请
--------|-------
参与者|读者 图书管理员
前置条件|读者得到信息管理员授权，图书管理员获得授权
后置条件|更新读者信息，并更新系统库存
主事件流|>读者查阅当前借阅信息并<br>读者提交赔偿申请<br>图书管理员可验证当前借阅状态，核实情况，以及更新读者信息<br>读者赔偿书籍
备注|当读者弄丢书籍，或者损坏书籍将赔偿书籍

“赔偿书籍”用例流程图[源码](https://github.com/z915287285/is_analysis/blob/master/test2/usercase3-6_flow.puml)如下:
````
@startuml
start
:Reader;
if (Select ReaderState) then(未借阅)
else(已借阅)
if(无法按时归还)then(Yes)
if(书籍损坏或者丢失)then(No)
:Late application;
else(Yes)
:Compensation book;
endif
else(No)
:Back Book;
endif
endif
stop
@enduml
````
“赔偿书籍”用例图

![image](https://github.com/z915287285/is_analysis/blob/master/test2/usercase3-6_flow.png)
