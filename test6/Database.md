# 数据库设计
﻿<!-- markdownlint-disable MD033-->
<!-- 禁止MD033类型的警告 https://www.npmjs.com/package/markdownlint -->
    
<div id="USERS"></div>

- ## USERS表（用户表）

    |字段|类型|主键，外键|可以为空|默认值|约束|说明|
    |:-------:|:-------------:|:------:|:----:|:---:|:----:|:----------|
    |USER_ID|NUMBER(8,0)|主键|否| | | 用户ID|
    |NAME|VARCHAR2(50 BYTE)| |否| | | 用户真实姓名|
    |GITHUB_USERNAME|VARCHAR2(50 BYTE)| |是|空| | GitHUB用户名|
    |UPDATE_DATE|DATE| |是|空| | GitHUB用户名修改日期|
    |PASSWORD|VARCHAR2(512 BYTE)| |是|空| | 加密存储密码，为空表示密码就是学号|
    |DISABLE|VARCHAR2(20 BYTE)| |否| | |是否禁用,值为是表示禁用,其他表示正常.|

<div id="TEACHERS"></div>

- ## TEACHERS表（老师表）

    |字段|类型|主键，外键|可以为空|默认值|约束|说明|
    |:-------:|:-------------:|:------:|:----:|:---:|:----:|:----------|
    |TEACHER_ID|VARCHAR2(50 BYTE)|主键|否| | | 老师的编号|
    |USER_ID|NUMBER(8,0)|外键|是| | | 老师的用户ID，USERS表的外键|
    |DEPARTMENT|VARCHAR2(400 BYTE)| |否| | | 老师属于的部门|

<div id="STUDENTS"></div>

- ## STUDENTS表（学生表）

    |字段|类型|主键，外键|可以为空|默认值|约束|说明|
    |:-------:|:-------------:|:------:|:----:|:---:|:----:|:----------|
    |STUDENT_ID|VARCHAR2(50 BYTE)|主键|否| | | 学生的学号|
    |USER_ID|NUMBER(8,0)|外键|是| |空| 学生的用户ID，USERS表的外键，为空表示还没有建立用户| 
    |MAJOR|VARCHAR2(20 BYTE)| |否| | |学生的专业|   
    |CLASSNUM|VARCHAR2(20 BYTE)| |否| | |学生的班级号|
    |RESULT_SUM|VARCHAR2(400 BYTE)|外键|是|空| | 成绩汇总（来自GRADES表），以逗号分开，第一个成绩是平均成绩,后面是每次实验的成绩，N表示未批改，平均分只计算已批改的。比如：“81.25,70,80,85,90,N”表示一共批改了4次，第5次未批改，4次的成绩分别是81.25,70,80,85,90,N，4次的平均分是81.25|
    |WEB_SUM|VARCHAR2(400 BYTE)| |是|空| | GitHub网址是否正确，用逗号分开，Y代表正确，N代表不正确。第1位代表总的GitHUB地址是否正确，第2位表示第1次实验的地址，第3位表示第2位实验地址，依此类推。比如：“Y,Y,Y,Y,Y,N”表示第5次实验地址不正确，其他地址正确|
 
<div id="GRADES"></div>

- ## GRADES表（学生实验成绩表）

    |字段|类型|主键，外键|可以为空|默认值|约束|说明|
    |:-------:|:-------------:|:------:|:----:|:---:|:----:|:----------|
    |STUDENT_ID|VARCHAR2(50 BYTE)|联合主键1，外键|否| | | 学生的学号，STUDENTS表外键|
    |TEST_ID|NUMBER(6,0)|联合主键2，外键|否| | | 实验编号，TESTS表的外键|
    |COURSE_ID|VARCHAR2(50 BYTE)|联合主键3，外键|否| | | 课程编号，COURSE表的外键|
    |PROGRAM1/RATE1|VARCHAR2(50 BYTE)| |是|空| | 评分标准1以及对应项占比1，这个值为空表示未设置评分项|
    |PROGRAM2/RATE2|VARCHAR2(50 BYTE)| |是|空| | 评分标准2以及对应项占比2，这个值为空表示未设置评分项|
    |PROGRAM3/RATE3|VARCHAR2(50 BYTE)| |是|空| | 评分标准3以及对应项占比3，这个值为空表示未设置评分项|
    |RESULT|NUMBER|主键|是|空| 取值0-100| 分数，这个值为空表示没有批改|
    |MEMO|VARCHAR2(400 BYTE)| |是|空| | 老师对实验的评语|
    |UPDATE_DATE|DATE| |是|空| |老师批改实验的日期，为空表示未批改|

<div id="TESTS"></div>

- ## TESTS表（实验项目表）

    |字段|类型|主键，外键|可以为空|默认值|约束|说明|
    |:-------:|:-------------:|:------:|:----:|:---:|:----:|:----------|
    |TEST_ID|NUMBER(6,0)|主键|否| | | 实验编号|
    |TITLE|VARCHAR2(100 BYTE)| |否| | | 实验名称|

<div id="COURSES"></div>

- ## COURSE表（课程表）

    |字段|类型|主键，外键|可以为空|默认值|约束|说明|
    |:-------:|:-------------:|:------:|:----:|:---:|:----:|:----------|
    |COURSE_ID|VARCHAR2(50 BYTE)|主键|否| | | 课程的编号|
    |TEACHER_ID|VARCHAR2(50 BYTE)|联合主键1，外键|否| | | 老师的编号，TEACHER表的外键|
    |COURSE_NAME|VARCHAR2(50 BYTE)| |否| | | 课程名称|
    |TERM|VARCHAR2(50 BYTE)| |否| | | 开课学期|
    |DEPARTMENT|VARCHAR2(400 BYTE)| |否| | | 开课学院|
    
<div id="SELECT_COURSE"></div>

- ## SELECT_COURSE表（选课表）

    |字段|类型|主键，外键|可以为空|默认值|约束|说明|
    |:-------:|:-------------:|:------:|:----:|:---:|:----:|:----------|
    |COURSE_ID|VARCHAR2(50 BYTE)|主键|否| | | 课程的编号|
    |STUDENT_ID|VARCHAR2(50 BYTE)|联合主键1，外键|否| | | 学生的编号，STUDENT表的外键|
    |TERM|VARCHAR2(50 BYTE)| |否| | | 开课学期|
    