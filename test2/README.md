实验2：图书管理系统用例建模
=======
    
学号|班级|姓名|我的照片
:-:|:-:|:-:|:-:
201610414323|软件(本)16-3|23.王涵玮|<img src="https://github.com/WangHanWei19971211/is_analysis/blob/master/test1/myself.jpg" width="66"/>


## 1. 图书管理系统的用例关系图

#### 1.1 用例图PlantUML源码如下：
~~~sql
@startuml
图书管理员 ---> (借出图书)
图书管理员 ---> (归还图书)
图书管理员 ---> (维护书目)
图书管理员 ---> (维护读者信息)
图书管理员 ---> (购入图书)
@enduml
~~~
~~~sql
@startuml
:读者: ---> (查询书目)
:读者: ---> (查询借阅情况)
:读者: ---> (预定图书)
:读者: ---> (取消预订)
:读者: ---> (借阅图书)
@enduml
~~~

#### 1.2. 用例图如下：

<img src="https://github.com/WangHanWei19971211/is_analysis/blob/master/test2/UML3.png" width="666"/>
<img src="https://github.com/WangHanWei19971211/is_analysis/blob/master/test2/UML3.1.png" width="666"/>


## 2. 参与者说明：

#### 2.1 图书管理员

主要职责是：图书管理员通过系统记录图书的借出和归还，进行书目的维护、读者信息和借书卡的维护。

#### 2.2 读者

主要职责是：读者可以查询到馆藏目录和本人在借的图书，对目前已借出无馆藏的图书可以进行预订，也可以取消预订。

#### 2.3 其他类型用户：系统

主要职责是：记录借出归还图书信息，存储馆藏图书信息



## 3. 用例规约表

#### 3.1 “借出图书”用例

<table class="tg">
  <tr>
    <th class="tg-0lax" colspan="5"></th>
  </tr>
  <tr>
    <td class="tg-0pky" colspan="2">用例名称</td>
    <td class="tg-0pky" colspan="3">借出图书</td>
  </tr>
  <tr>
    <td class="tg-0lax" colspan="2">参与者</td>
    <td class="tg-0lax" colspan="3">图书管理员（主要参与者）、读者（次要参与者）</td>
  </tr>
  <tr>
    <td class="tg-0lax" colspan="2">前置条件</td>
    <td class="tg-0lax" colspan="3">图书管理员已被识别和授权</td>
  </tr>
  <tr>
    <td class="tg-0lax" colspan="2">后置条件</td>
    <td class="tg-0lax" colspan="3">存储借书记录、更新库存数量、所借图书状态为借出</td>
  </tr>
    <tr>
    <td class="tg-0pky" colspan="2">主事件流</td>
    <td class="tg-0pky" colspan="3">1.图书管理员将读者借书卡提供给系统；<br>2.系统验证读者身份和借书条件<br>3.图书管理员将读者所借图书输入系统<br>4.系统记录借书信息，并且修改图书的状态和此种书的可借数量<br>5.系统累加读者的借书数量<br>6.重复3~5，直到图书管理员确认全部图书登记完毕<br>7.系统打印借书清单，交易成功完成</td>
  </tr>
     <tr>
    <td class="tg-0lax" colspan="2">备选事件流</td>
    <td class="tg-0lax" colspan="3">2a.非法读者<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1.系统提示错误并拒绝接受输入<br>2b.读者借书数已经达到限额<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1.系统提示并拒绝接受输入<br>5a.读者借书数已达限额<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1.系统提示，并要求结束输入<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2.管理员确认借书完成<br>5b.读者有该书的预定记录<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1.删除该条预定信息</td>
  </tr>
      <tr>
    <td class="tg-0lax" colspan="2">备注</td>
    <td class="tg-0lax" colspan="3">图书馆开架借阅，读者找到书后办理借阅手续，因此借书不需要验证库存，而且每本书都是可识别的</td>
  </tr>
</table>

###### “借出图书”用例流程图源码如下：
~~~sql
@startuml
|读者|
start
while (读者所借图书是否录入完毕?)is(否)
    :读者提供借书卡;
|#AntiqueWhite|图书管理员|
    :将借书卡提供给系统;
|系统|
    :验证读者身份和借书条件;
|#AntiqueWhite|图书管理员|
    :所借图书输入系统;
|系统|
    :记录借书信息;
    :修改图书状态和可借阅数量;
    :累加读者借书数量;
end while (是)
    :打印借书清单，交易成功完成;
stop
@enduml
~~~

###### “借出图书”用例流程图：

<img src="https://github.com/WangHanWei19971211/is_analysis/blob/master/test2/UML-p145-7.1.png" width="530"/>

#### 3.2 “购入图书”用例

<table class="tg">
  <tr>
    <th class="tg-0pky" colspan="5"></th>
  </tr>
  <tr>
    <td class="tg-0pky" colspan="2">用例名称</td>
    <td class="tg-0pky" colspan="3">购入图书</td>
  </tr>
  <tr>
    <td class="tg-0pky" colspan="2">参与者</td>
    <td class="tg-0pky" colspan="3">系统（主要参与者）、图书管理员（次要参与者）</td>
  </tr>
  <tr>
    <td class="tg-0pky" colspan="2">前置条件</td>
    <td class="tg-0pky" colspan="3">图书管理员已被识别和授权</td>
  </tr>
  <tr>
    <td class="tg-0pky" colspan="2">后置条件</td>
    <td class="tg-0pky" colspan="3">存储图书记录、更新库存数量</td>
  </tr>
  <tr>
    <td class="tg-0pky" colspan="2">主事件流</td>
    <td class="tg-0pky" colspan="3">1.图书管理员将图书信息提供给系统；<br>2.系统存储图书信息更新图书数量<br>3.重复1~2，直到图书管理员确认全部图书登记完毕<br>4.系统打印新增图书清单</td>
  </tr>
  <tr>
    <td class="tg-0lax" colspan="2">备选事件流</td>
    <td class="tg-0lax" colspan="3">1a.该图书已有<br>&nbsp;&nbsp;&nbsp;&nbsp;1.只更新库存</td>
  </tr>
    <tr>
    <td class="tg-0lax" colspan="2">备注</td>
    <td class="tg-0lax" colspan="3">每本新增图书都会有编号，也会更新库存数量</td>
  </tr>
</table>

###### “购入图书”用例流程图源码如下：
~~~sql
@startuml
|图书管理员|
start
while (新增图书是否录入完毕?)is(否)
    :将图书信息提供给系统;
|系统|
    :存储图书信息;
    :更新图书数量;
end while (是)
    :打印新增图书清单;
stop
@enduml
~~~

###### “购入图书”用例流程图：

<img src="https://github.com/WangHanWei19971211/is_analysis/blob/master/test2/UML-p145-7.1-1.png" width="500"/>

#### 3.3 “维护书目”用例

<table class="tg">
  <tr>
    <th class="tg-0pky" colspan="5">1</th>
  </tr>
  <tr>
    <td class="tg-0pky" colspan="2">用例名称</td>
    <td class="tg-0pky" colspan="3">维护书目</td>
  </tr>
  <tr>
    <td class="tg-0pky" colspan="2">参与者</td>
    <td class="tg-0pky" colspan="3">图书管理员（主要参与者）、系统（次要参与者）</td>
  </tr>
  <tr>
    <td class="tg-0pky" colspan="2">前置条件</td>
    <td class="tg-0pky" colspan="3">图书管理员已被识别和授权</td>
  </tr>
  <tr>
    <td class="tg-0pky" colspan="2">后置条件</td>
    <td class="tg-0pky" colspan="3">核对图书库存数量</td>
  </tr>
  <tr>
    <td class="tg-0pky" colspan="2">主事件流</td>
    <td class="tg-0pky" colspan="3">1.图书管理员统计馆藏<br>2.图书管理员将图书信息提供给系统<br>3.系统将新的信息与数据库中的记录对比<br>4.重复1~3，直到图书管理员确认全部图书核对完毕<br></td>
  </tr>
  <tr>
    <td class="tg-0pky" colspan="2">备选事件流</td>
    <td class="tg-0pky" colspan="3">3a.与记录不一致<br>     1.系统更新记录并记录这次更改<br><br></td>
  </tr>
  <tr>
    <td class="tg-0pky" colspan="2">备注</td>
    <td class="tg-0pky" colspan="3">统计馆藏由管理员进行</td>
  </tr>
</table>

###### “维护书目”用例流程图源码如下：
~~~sql
@startuml
|管理员|
start
while (图书是否核对完毕?)is(否)
:统计馆藏;
:统计信息输入系统;
|#AntiqueWhite|系统|
:与数据库中的记录对比;
if (是否一致？) then (否)
     :更新记录并记录这次更改;
     detach
     else(是)
   endif
   |管理员|
end while (是)
stop
@enduml
~~~
###### “维护书目”用例流程图：

<img src="https://github.com/WangHanWei19971211/is_analysis/blob/master/test2/uml2-3.3.png" width="500"/>

#### 3.4 “维护读者信息”用例
用例表
###### “维护读者信息”用例流程图源码如下：
###### “维护读者信息”用例流程图：

<img src="https://github.com/WangHanWei19971211/is_analysis/blob/master/test2/uml2-3.4.png" width="500"/>

#### 3.5 “归还图书”用例
用例表
###### “归还图书”用例流程图源码如下：
###### “归还图书”用例流程图：

<img src="https://github.com/WangHanWei19971211/is_analysis/blob/master/test2/uml2-3.5.png" width="500"/>
