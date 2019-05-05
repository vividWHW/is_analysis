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
#### 5.1.  users表
<table>
  <tr>
    <th>字段</th>
    <th>类型</th>
    <th>主键、外键</th>
    <th>可以为空</th>
    <th>默认值</th>
    <th>约束</th>
    <th>说明</th>
  </tr>
  <tr>
    <td>user_id</td>
    <td>varchar2(30)</td>
    <td>主键</td>
    <td>否</td>
    <td>null</td>
    <td>无重复</td>
    <td>用户ID</td>
  </tr>
  <tr>
    <td>name</td>
    <td>varchar2(30)</td>
    <td></td>
    <td>否</td>
    <td>null</td>
    <td></td>
    <td>用户真实姓名</td>
  </tr>
  <tr>
    <td>github_username</td>
    <td>varchar2(30)</td>
    <td></td>
    <td>否</td>
    <td>null</td>
    <td></td>
    <td>用户GitHub账号</td>
  </tr>
  <tr>
    <td>update_date</td>
    <td>varchar2(30)</td>
    <td></td>
    <td>否</td>
    <td>null</td>
    <td></td>
    <td>用户GitHub账号修改日期</td>
  </tr>
  <tr>
    <td>password</td>
    <td>varchar2(30)</td>
    <td></td>
    <td>否</td>
    <td>null</td>
    <td></td>
    <td>用户密码</td>
  </tr>
  <tr>
    <td>disable</td>
    <td>varchar2(30)</td>
    <td></td>
    <td>否</td>
    <td></td>
    <td></td>
    <td>用户是否禁用</td>
  </tr>
</table>

#### 5.2.  grades表
<table>
  <tr>
    <th>字段</th>
    <th>类型</th>
    <th>主键、外键</th>
    <th>可以为空</th>
    <th>默认值</th>
    <th>约束</th>
    <th>说明</th>
  </tr>
  <tr>
    <td>student_id</td>
    <td>varchar2(30)</td>
    <td>主键</td>
    <td>否</td>
    <td>null</td>
    <td>无重复</td>
    <td>学号</td>
  </tr>
  <tr>
    <td>course_id</td>
    <td>varchar2(30)</td>
    <td>外键</td>
    <td>否</td>
    <td>null</td>
    <td>无重复</td>
    <td>课程编号</td>
  </tr>
  <tr>
    <td>test_id</td>
    <td>varchar2(30)</td>
    <td>外键</td>
    <td>否</td>
    <td>null</td>
    <td>无重复</td>
    <td>实验编号</td>
  </tr>
  <tr>
    <td>result</td>
    <td>varchar2(30)</td>
    <td></td>
    <td>否</td>
    <td>null</td>
    <td></td>
    <td>分数</td>
  </tr>
  <tr>
    <td>memo</td>
    <td>varchar2(30)</td>
    <td></td>
    <td>否</td>
    <td>null</td>
    <td></td>
    <td>评价</td>
  </tr>
  <tr>
    <td>update_date</td>
    <td>varchar2(30)</td>
    <td></td>
    <td>否</td>
    <td>null</td>
    <td></td>
    <td>评改日期</td>
  </tr>
</table>

#### 5.3. students表
<table>
  <tr>
    <th>字段</th>
    <th>类型</th>
    <th>主键、外键</th>
    <th>可以为空</th>
    <th>默认值</th>
    <th>约束</th>
    <th>说明</th>
  </tr>
  <tr>
    <td>student_id</td>
    <td>varchar2(30)</td>
    <td>主键</td>
    <td>否</td>
    <td>null</td>
    <td>无重复</td>
    <td>学号</td>
  </tr>
  <tr>
    <td>class<br></td>
    <td>varchar2(30)</td>
    <td></td>
    <td>否</td>
    <td>null</td>
    <td></td>
    <td>班级</td>
  </tr>
  <tr>
    <td>result_sum</td>
    <td>varchar2(30)</td>
    <td></td>
    <td>否</td>
    <td>null</td>
    <td></td>
    <td>成绩汇总</td>
  </tr>
  <tr>
    <td>web_sum</td>
    <td>varchar2(30)</td>
    <td></td>
    <td>否</td>
    <td>null</td>
    <td></td>
    <td>网站正确与否汇总</td>
  </tr>
  
#### 5.4. tests表
  <table>
    <tr>
      <th>字段</th>
      <th>类型</th>
      <th>主键、外键</th>
      <th>可以为空</th>
      <th>默认值</th>
      <th>约束</th>
      <th>说明</th>
    </tr>
    <tr>
      <td>test_id</td>
      <td>varchar2(30)</td>
      <td>主键</td>
      <td>否</td>
      <td>null</td>
      <td>无重复</td>
      <td>实验编号</td>
    </tr>
    <tr>
      <td>course_id<br></td>
      <td>varchar2(30)</td>
      <td>外键</td>
      <td>否</td>
      <td>null</td>
      <td>无重复</td>
      <td>所属课程编号</td>
    </tr>
    <tr>
      <td>test_title</td>
      <td>varchar2(30)</td>
      <td></td>
      <td>否</td>
      <td>null</td>
      <td></td>
      <td>实验名称</td>
    </tr>
  </table>
  
####5.5. course表
 <table>
   <tr>
     <th>字段</th>
     <th>类型</th>
     <th>主键、外键</th>
     <th>可以为空</th>
     <th>默认值</th>
     <th>约束</th>
     <th>说明</th>
   </tr>
   <tr>
     <td>course_id</td>
     <td>varchar2(30)</td>
     <td>主键</td>
     <td>否</td>
     <td>null</td>
     <td>无重复</td>
     <td>课程编号</td>
   </tr>
   <tr>
     <td>course_name<br></td>
     <td>varchar2(30)</td>
     <td></td>
     <td>否</td>
     <td>null</td>
     <td></td>
     <td>课程名称</td>
   </tr>
 </table> 
  
####5.6. teachers表
<table>
  <tr>
    <th>字段</th>
    <th>类型</th>
    <th>主键、外键</th>
    <th>可以为空</th>
    <th>默认值</th>
    <th>约束</th>
    <th>说明</th>
  </tr>
  <tr>
    <td>teacher_id</td>
    <td>varchar2(30)</td>
    <td>主键</td>
    <td>否</td>
    <td>null</td>
    <td>无重复</td>
    <td>老师工号</td>
  </tr>
  <tr>
    <td>department<br></td>
    <td>varchar2(30)</td>
    <td></td>
    <td>否</td>
    <td>null</td>
    <td></td>
    <td>老师所属部门</td>
  </tr>
</table>

