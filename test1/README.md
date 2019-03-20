# 实验1：业务流程建模

===================
| 学号         | 班级         | 姓名 | 图片 |
|--------------|--------------|------|------|
| 201610414330 | 软件(本)16-3 | 朱泓超 |![image](https://github.com/z915287285/is_analysis/blob/master/test1/zz.jpg)    |

## 流程图1：考试及成绩管理流程
-------------------------
### plantUML源码如下：
```javascript
@startuml
|教务处|
:安排考试;
:考试安排表;
|教师|
:出卷;
fork
:A、B试卷;
fork again
|教师|
:打印审批表;
|系主任|
:审批签字;
:打印审批表;
end fork
|教务处|
:打印试卷;
:试卷;
|学生|
:参加考试;
:答卷;
|教师|
:阅卷出成绩;
fork
:答卷;
:装订存档;
fork again
:成绩单;
|教务处|
if(有不及格？) then(有)
:安排补考;
fork
:补考安排表;
fork again
end fork
else
end
endif
end fork
|教师|
:期末流程结束;
stop
@enduml

```

#### 也可直接参考test1中的[flow1.puml](https://github.com/z915287285/is_analysis/blob/master/test1/flow1.puml)
#### 业务流程图：
![image](https://github.com/z915287285/is_analysis/blob/master/test1/flow1.png)
#### 流程说明：
```
期末考试前三周，教务处负责安排全校课程的考试时间和地点，下发“考试安排表”。考试前一周，各任课教师准备好A、B两份试卷，  
填写“试卷打印审批表”一并交与系主任评审签字，将选中的期末试卷和已签字的“试卷打印评审表”送到教务处印刷部门进行印刷。  
学生按时到达指定考场参加考试，考试完毕任课教师进行阅卷，产出成绩单，并对学生答卷装订存档。如果课程有不及格情况，教务  
处负责安排补考时间和地点，产出“补考安排表”，流程结束。  
```
## 流程图2：客户维修服务流程
-----------------------
### plantUML源码如下：
```javascript
@startuml
|客户|
start
:申请服务;
|业务经理|
if(是新客户吗？)then(是)
:登记客户信息;
else(不是)
endif
:上门勘察;
:制订方案;
|客户|
if(满意吗？)then(否)
stop
else(是)
:签订服务合同;
|业务经理|
fork
:安排工人;
fork again
:安排材料;
end fork
:填写派工单;
|工人|
:领取材料;
:上门服务;
|客户|
:验收并填写反馈意见;
|业务经理|
:交回派工单;
|财务人员|
:结算收款;
stop
@enduml
```
#### 也可直接参考test1中的[flow2.puml](https://github.com/z915287285/is_analysis/blob/master/test1/flow2.puml)
### 业务流程图：
![image](https://github.com/z915287285/is_analysis/blob/master/test1/flow2.png)
#### 流程说明：
```

```
