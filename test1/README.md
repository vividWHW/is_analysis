实验1：业务流程建模
=======
    
学号|班级|姓名
:-:|:-:|:-:
201610414323|软件(本)16-3|23.王涵玮

流程图1：考试及成绩管理流程
---------
    PlantUML源码如下：
    ~~~sql
    @startuml
|教务处|
start
:安排考试;
:考试安排表;
|#AntiqueWhite|教师|
:出卷;
-> You can put text on arrows;
fork
:A、B试卷;
  fork again
  :打印审批表;
  |系主任|
  :审批签字;
  :打印审批表;
  end fork
  |教务处|
:打印试卷;
:试卷;
|#AntiqueWhite|学生|
:参加考试;
:答卷;
|#AntiqueWhite|教师|
:阅卷出成绩;
  fork
   :成绩单;
   |教务处|
   if (有不及格？) then (有)
     :安排补考;
     :补考安排表;
     detach
     else(无)
   endif
   fork again
   |#AntiqueWhite|教师|
   :答卷;
   :装订存档;
   end fork
stop
@enduml
    ~~~
    业务流程图如下：
    ![查询1](https://github.com/WangHanWei19971211/is_analysis/blob/master/test1/UML-p107-6.1.png)
    流程说明：


流程图2： 客户维修服务流程
-----------
    PlantUML源码如下：
    业务流程图如下：
    流程说明：
