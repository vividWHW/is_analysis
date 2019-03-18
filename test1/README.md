实验1：业务流程建模
=======
    
学号|班级|姓名|我的照片
:-:|:-:|:-:|:-:
201610414323|软件(本)16-3|23.王涵玮|<img src="https://github.com/WangHanWei19971211/is_analysis/blob/master/test1/myself.jpg" witdth="50"/>


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

![UML1](https://github.com/WangHanWei19971211/is_analysis/blob/master/test1/UML-p107-6.1.png)
   
   
流程说明：
    考试前教务处负责安排全校课程的考试时间和地点，下发“考试安排表”。各科老师准备好A、B两份试卷，填写“试卷打印审批表”，再将表交给系主任审批签字并打印“审批表”。将“审批表”和A、B试卷送到教务处打印试卷。学生参加考试，交上答卷。教师对答卷进行阅卷出成绩，答卷装订存档，教务处通过“成绩单”判断是否有不及格，有不及格则安排补考，生成“补考安排表”。


流程图2： 客户维修服务流程
-----------
PlantUML源码如下：
~~~sql
@startuml
|客户|
start
:申请服务;
|#AntiqueWhite|业务经理|
if (你是新客户吗？) then (是)
  :登记客户信息;
else (不是)
endif
:上门勘察;
:制定方案;
|客户|
if (满意吗？) then (是)
   :签订服务合同;
   |#AntiqueWhite|业务经理|
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
   |#AntiqueWhite|业务经理|
   :交回派工单;
|#AntiqueWhite|财务人员|
   :结算收款;
   stop
   |客户|
else (不是)
   stop
@enduml
~~~

业务流程图如下：

![UML2](https://github.com/WangHanWei19971211/is_analysis/blob/master/test1/UML-p108-6.2.png)


流程说明：
流程从客户申请服务开始，如果是新客户，业务经理将该客户的基本信息记录下来，接下来业务经理将上门进行勘查，并制定具体“维修方案”，业务经理和客户就方案进行沟通，如果达成一致则签订正式“服务合同”，否则终止流程。业务经理根据合同方案安排工人、安排材料，并派发“派工单”。工人拿到派工单后领取材料上门实施服务。服务完成后客户进行验收并在派工单上填写反馈意见。业务经理收回派工单后通知财务人员进行结算并收款，流程结束。

