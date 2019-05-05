﻿<!-- markdownlint-disable MD033-->
<!-- 禁止MD033类型的警告 https://www.npmjs.com/package/markdownlint -->

# 接口：getCourses  [返回](../README.md)
用例： [课程列表](../用例/Course_list.md)

- 权限：
    学生：不能看到RESULT_SUM，WEB_SUM
    老师：可以看到RESULT_SUM，WEB_SUM。

- 功能：
    返回所有学生的列表。

- API请求地址：
   接口基本地址/v1/api/getCourses

- 请求方式 ：
    GET

- 请求参数说明:
    无

- 返回实例：

        {
            "status": true,
            "info": null,
            "total": 21,
            "data": [
                {"COURSE_ID": "0000001",
                "COURSE_NAME": "离散数学",
                "TEACHER_ID": "100064",
                "TERM": "2018-2019学年下",
                "DEPARTMENT": "教务处",},
                {
                ...其他课程信息
                }
            ]
        }

- 返回参数说明：

  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|
  |status|bool类型，true表示正确的返回，false表示有错误|
  |info|返回结果说明信息|
  |total|返回学生人数|
  |data|所有课程的数组|
  |TEACHER_ID|教师工号|
  |COURSE_ID|课程编号|
  |COURSE_NAME|课程名称|
  |TERM|开课学期|
  |DEPARTMENT|授课部门|