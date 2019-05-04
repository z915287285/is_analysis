基于GitHub的实验管理平台的分析与设计
=========================
| 学号         | 班级         | 姓名 | 图片 |
|--------------|--------------|------|------|
| 201610414330 | 软件(本)16-3 | 朱泓超 |![image](https://github.com/z915287285/is_analysis/blob/master/test1/zz.jpg)
# 1.概述

- 基于GitHub的实验管理平台的作用是在线管理实验成绩的Web应用系统。学生和老师的实验内容均存放在GitHUB 页面上。
- 学生的功能主要有：一是设置自己的GitHub用户名，二是可查看各个学期与已开课程的实验成绩。学生的GitHub用户名是公开的，但成绩不公开。
- 老师的功能主要有：一是批改每个学生的成绩(设置有批改项，以及对应权重比)，二是查看每个学生不同学期相关实验的成绩。
- 老师和学生都能通过本系统的链接方便地跳转到学生的每个GitHUB实验目录，以便批改实验或者查看实验情况。
- 实验成绩按数字分数计算，每项实验的满分为100分，最低为0分。
- 系统自动计算每个学生的所有实验的平均分

# 2.系统总体结构

![image](https://github.com/z915287285/is_analysis/blob/master/test6/sys.png)

# 3.用例图设计 [源码](https://github.com/z915287285/is_analysis/blob/master/test6/Usecase.puml)

![image](https://github.com/z915287285/is_analysis/blob/master/test6/Usecase.png)

# 4.类图设计[源码](https://github.com/z915287285/is_analysis/blob/master/test6/class.puml)

![image](https://github.com/z915287285/is_analysis/blob/master/test6/class.png)

# 5.数据库设计

# 6.用例及界面详细设计