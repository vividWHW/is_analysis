实验3：图书管理系统领域对象建模
=======
    
学号|班级|姓名|我的照片
:-:|:-:|:-:|:-:
201610414323|软件(本)16-3|23.王涵玮|<img src="https://github.com/WangHanWei19971211/is_analysis/blob/master/test1/myself.jpg" width="66"/>

1.图书管理系统的类图
---------
#### 1.1 类图PlantUML源码如下：
~~~sql
@startuml
馆藏资源品种 <|- 碟片品种
馆藏资源品种 <|- 图书品种
资源项 *- 馆藏资源品种 : 拥有
馆藏资源品种"1" -- "*"预定记录 : 被预定
读者 "*" - "1"预定记录
借书记录"*" - "1"读者
资源项"1" -- "0..1"借书记录
图书管理员"1"  - "       *"借书记录: 登记
借书记录"1" -- "0..1"逾期记录
逾期记录"*" - "0..1"罚款细则 : 使用
馆藏目录"1" -- "  1..*"馆藏资源品种
class 馆藏资源品种{
    资源名称
    国际出版号
    价格
    简介
    馆藏数量
    可借数量
    书架名称
    显示所有品种()
    查询品种()
}
class 馆藏目录{
    新增()
    修改()
    删除()
    查询()
}
class 碟片品种{
    碟片名
    碟片类型
    碟片数
    制作公司
    可借天数
    添加新品种()
    修改品种()
    删除品种()
}
class 图书品种{
    书名
    编号
    作者
    出版社
    出版日期
    可借天数
    添加新品种()
    修改品种()
    删除品种()
}
class 资源项{
    馆藏流水号
    状态
    查找()
    显示全部资源()
    新增资源()
    删除资源()
    修改资源()
}
class 预定记录{
    预定日期
    预定时间
    预定编号
    预定()
    删除预定记录()
    修改预定记录()
    查询预订记录()
}
class 读者 {
   姓名
   性别
   身份证号
   借书卡号
   图书限额
   已借图书数
   碟片限额
   已借碟片数
   新增读者()
   修改读者信息()
   注销读者信息()
   查询读者信息()
}
class 借书记录{
    借书日期
    应还日期
    归还日期
    经办人
    借书()
    还书()
}
class 图书管理员{
    职工号
    姓名
    登录密码
}
class 逾期记录{
    逾期天数
}
class 罚款细则{
    应缴罚款
    计算应缴罚款()
}
@enduml
~~~
#### 1.2. 类图如下：

![UML1](https://github.com/WangHanWei19971211/is_analysis/blob/master/test3/uml3-p170-8.17.png)

#### 1.3. 类图说明：
   馆藏资源品种的属性有资源名称、国际出版号、价格、简介、馆藏数量、可借数量，图书品种、碟片品种为馆藏资源品种的子类。图书品种的属性有书名、编号
、作者、出版社、出版日期、可借天数。

2.图书管理系统的对象图
---------
#### 2.1 类ResourceTitle的对象图
###### 源码如下：
~~~sql
@startuml
aResourceTitle馆藏资源品种 <|-- aDiscTitle碟片品种
aResourceTitle馆藏资源品种 <|- aBookTitle图书品种
aResource资源项 *- aResourceTitle馆藏资源品种
object aResourceTitle馆藏资源品种{
    资源名称=图书
    国际出版号=9787040126624
    价格=￥25.0
    简介=……
    馆藏数量=50
    可借数量=40
    书架名称=古典文学
}
object aDiscTitle碟片品种{
    碟片类型=音乐
    碟片数=10
    制作公司=某某公司
    可借天数=15
}
object aBookTitle图书品种{
    书名=数据库基础
    编号=9787040126624
    作者=崔巍
    出版社=清华大学出版社
    出版日期=20100201
    可借天数=35
}
object aResource资源项{
    馆藏流水号=201103001
    状态=借出
}
@enduml
~~~
###### 对象图如下：

![UML1](https://github.com/WangHanWei19971211/is_analysis/blob/master/test3/uml3-1.png)

#### 2.2 类Readere的对象图
###### 源码如下：
~~~sql
@startuml
aReader读者"*" - "      1" aReserve预定记录
aLoan借书记录"*" - "    1"aReader读者
aLoan借书记录"1" -- "0..1"aOverdue逾期记录
aOverdue逾期记录"*" - "0..1"aPenalty罚款细则
object aReader读者 {
   姓名=张三
   性别=男
   身份证号=510601199912116666
   借书卡号=123456789
   图书限额=15
   已借图书数=5
   碟片限额=5
   已借碟片数=1
}
object aLoan借书记录{
    借书日期=20190401
    应还日期=20190420
    归还日期=20190425
    经办人=李四
}
object aOverdue逾期记录{
    逾期天数=5
}
object aPenalty罚款细则{
    应缴罚款=25
}
object aReserve预定记录{
    预定日期=20190408
    预定时间=20190409
    预定编号=20190408155
}
@enduml
~~~
###### 对象图如下：

![UML1](https://github.com/WangHanWei19971211/is_analysis/blob/master/test3/uml3-2.png)

#### 2.3 类Manager的对象图
###### 源码如下：
~~~sql
@startuml
aManager图书管理员"1"  - "  *"aLoan借书记录
object aManager图书管理员{
    职工号=123456789
    姓名=李四
    登录密码=abc123
}
object aLoan借书记录{
    借书日期=20190401
    应还日期=20190420
    归还日期=20190425
}
@enduml
~~~
###### 对象图如下：

![UML1](https://github.com/WangHanWei19971211/is_analysis/blob/master/test3/uml3-3.png)

#### 2.4 类Loan的对象图
###### 源码如下：
~~~sql
@startuml
aLoan借书记录"*" - "1"aReader读者
aResource资源项"1" -- "0..1"aLoan借书记录
aManager图书管理员"1"  - "   *"aLoan借书记录
aLoan借书记录"1" -- "0..1"aOverdue逾期记录
object aLoan借书记录{
    借书日期=20190401
    应还日期=20190420
    归还日期=20190425
}
object aReader读者 {
   姓名=张三
   性别=男
   身份证号=510601199912116666
   借书卡号=123456789
   图书限额=15
   已借图书数=5
   碟片限额=5
   已借碟片数=1
}
object aOverdue逾期记录{
    逾期天数=5
}
object aManager图书管理员{
    职工号=123456789
    姓名=李四
    登录密码=abc123
}
object aResource资源项{
    馆藏流水号=201103001
    状态=借出
}
@enduml
~~~
###### 对象图如下：

![UML1](https://github.com/WangHanWei19971211/is_analysis/blob/master/test3/uml3-4.png)
