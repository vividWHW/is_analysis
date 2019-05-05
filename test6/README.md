# 基于GitHub的实验管理平台的分析与设计
学号|班级|姓名|我的照片
:-:|:-:|:-:|:-:
201610414323|软件(本)16-3|23.王涵玮|<img src="https://github.com/WangHanWei19971211/is_analysis/blob/master/test1/myself.jpg" width="66"/>

## 1. 概述
* 基于GitHub的实验管理平台的作用是在线管理实验成绩的Web应用系统。学生和老师的实验内容均存放在GitHUB 页面上。
* 学生的功能主要有：1.选择不同的课程，进行对应课程的实验；2.是设置自己的GitHub用户名和修改平台密码；3.是查询自己的实验成绩。
* 老师的功能主要有：1.是登入后发布一门或多门课程，并为没门课程设置一个或多个实验；2.是批改每个学生的成绩；3.是查看每个学生的成绩。
* 老师和学生都能通过本系统的链接方便地跳转到学生的每个GitHUB实验目录，以便批改实验或者查看实验情况。
* 学生的GitHub用户名是公开的，但成绩不公开。
* 平台可供多名老师多门课程多个学生使用。
* 实验成绩按数字分数计算，每项实验的满分为100分，最低为0分。
* 系统自动计算每个学生的所有实验的平均分。

## 2. 系统总体结构
![UML1](https://github.com/WangHanWei19971211/is_analysis/blob/master/test6/test6.png)

## 3. 用例图设计 <a href="https://github.com/WangHanWei19971211/is_analysis/blob/master/test6/src/uml3.all.puml" target="_blank">源码</a>
![UML1](https://github.com/WangHanWei19971211/is_analysis/blob/master/test6/uml3.all.png)

## 4. 类图设计 <a href="https://github.com/WangHanWei19971211/is_analysis/blob/master/test6/src/uml4.puml" target="_blank">源码</a>
![UML1](https://github.com/WangHanWei19971211/is_analysis/blob/master/test6/uml4.png)

## 5. 数据库设计 
