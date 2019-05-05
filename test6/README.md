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

[界面设计参见](https://github.com/z915287285/is_analysis/test6/ui/index.html)

# 3.用例图设计 [源码](https://github.com/z915287285/is_analysis/blob/master/test6/src/Usecase.puml)

![image](https://github.com/z915287285/is_analysis/blob/master/test6/Usecase.png)

# 4.类图设计[源码](https://github.com/z915287285/is_analysis/blob/master/test6/src/class.puml)

![image](https://github.com/z915287285/is_analysis/blob/master/test6/class.png)

# 5.数据库设计[首页](./README.md)

- ### [﻿数据库设计](https://github.com/z915287285/is_analysis/blob/master/test6/Database.md)

# 6.用例及界面详细设计

- ### [“学生列表”用例](./用例/stu_list.md),[界面](https://zwdbox.github.io/is_analysis/test6/ui/index.html)
- ### [“评定成绩”用例](./用例/evaluate_grades.md),[界面](https://zwdbox.github.io/is_analysis/test6/ui/评定成绩.html)
- ### [“查看成绩”用例](./用例/inquiry.md),[界面](https://zwdbox.github.io/is_analysis/test6/ui/查看成绩.html)
- ### [“修改密码”用例](./用例/modify_userpasswd.md),[界面](https://zwdbox.github.io/is_analysis/test6/ui/顶部菜单.html)
- ### [“修改用户信息”用例](./用例/modify_userInfor.md),[界面](https://zwdbox.github.io/is_analysis/test6/ui/顶部菜单.html)
- ### [“查看用户信息”用例](./用例/inquiry_user.md),[界面](https://zwdbox.github.io/is_analysis/test6/ui/顶部菜单.html)
- ### [“登出”用例](./用例/Login_out.md),[界面](https://zwdbox.github.io/is_analysis/test6/ui/顶部菜单.html)
- ### [“登录”用例](./用例/Login_in.md),[界面](https://zwdbox.github.io/is_analysis/test6/ui/登录.html)
- ### [“课程列表”用例](./用例/Course_list.md),[界面](https://zwdbox.github.io/is_analysis/test6/ui/登录.html)
- ### [“评分标准设置”用例](./用例/evaluate_principle.md),[界面](https://zwdbox.github.io/is_analysis/test6/ui/登录.html)
- ### [“学期选择”用例](./用例/Term_select.md),[界面](https://zwdbox.github.io/is_analysis/test6/ui/登录.html)
