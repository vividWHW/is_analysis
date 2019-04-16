# 实验4：图书管理系统顺序图绘制
学号|班级|姓名|我的照片
:-:|:-:|:-:|:-:
201610414323|软件(本)16-3|23.王涵玮|<img src="https://github.com/WangHanWei19971211/is_analysis/blob/master/test1/myself.jpg" width="66"/>

## 1. “借出资源”用例
#### 1.1. “借出资源”用例PlantUML源码
~~~sql
@startuml
skinparam sequenceParticipant underline
actor ": 图书管理员" as A
participant ": 读者" as B
participant ": 资源项" as C
participant ": 馆藏资源品种" as D
participant ": 借书记录" as E
participant ": 预定记录" as J

A -> B: 验证读者
activate A
activate B
deactivate B

A -> B: 取读者限额
activate B
deactivate B

loop

A -> C: 获取资源项
activate C
    C -> D:查找资源品种
    activate D
    deactivate D
deactivate C

A -> J:查询预定记录
activate J
deactivate J

A -> E: 创建借书记录
activate E
deactivate E

A -> C: 借出资源
activate C
    C -> D:减少可借数量
    activate D
    deactivate D
deactivate C

A -> B: 减少可用限额
activate B
deactivate B
A -> J:删除预定记录
activate J
deactivate J

end

A -> E: 打印借书清单
activate E
deactivate E

deactivate A
@enduml
~~~
#### 1.2. “借出资源”用例顺序图
![UML1](https://github.com/WangHanWei19971211/is_analysis/blob/master/test3/uml4-1.png)
#### 1.3. “借出资源”用例顺序图说明
&#160; &#160; &#160; &#160;图书管理员首先验证读者身份，获取读者限额，若限额已满则不能借书，
限额未满时可继续借书。获取资源项及资源品种，查询预定记录。创建借书记录，
并将该资源馆藏数量减少，读者的限额也减少。成功借出后，有预定记录则将该条预定记录删除。最后打印借书清单

## 2. “归还资源”用例
#### 2.1. “归还资源”用例PlantUML源码
~~~sql
@startuml
skinparam sequenceParticipant underline
actor ": 图书管理员" as A
participant ": 读者" as B
participant ": 资源项" as C
participant ": 馆藏资源品种" as D
participant ": 借书记录" as E
participant ": 逾期记录" as F


A -> B:获取借阅者信息
activate A
activate B
deactivate B

loop

A -> C: 读取资源信息
activate C
    C -> E: 取借书记录
    activate E
    deactivate E
    C -> D:取资源的品种
    activate D
    deactivate D
deactivate C

A -> C:归还资源
activate C
    C -> D:增加可借数量
    activate D
    deactivate D
deactivate C

A -> E:登记还书日期
activate E
deactivate E

A -> B:增加可用限额
activate B
deactivate B

opt
A -> F:登记逾期记录
activate F
deactivate F

deactivate A
end

end
@enduml
~~~
#### 2.2. “归还资源”用例顺序图
![UML1](https://github.com/WangHanWei19971211/is_analysis/blob/master/test3/uml4-2.png)
#### 2.3. “归还资源”用例顺序图说明
&#160; &#160; &#160; &#160;管理员获取通过借阅卡和读者归还的资源获得借阅者的信息和资源信息，再获得读者的借阅记录，
归还资源后，该资源的可借阅数量增加，登记该读者该资源的归还日期，增加读者的可用限额。若读者在归还资源是存在逾期记录，
则应在读者缴纳罚款后办理归还资源。

## 3. “购入资源”用例
#### 3.1. “购入资源”用例PlantUML源码
~~~sql
@startuml
skinparam sequenceParticipant underline
actor ": 图书管理员" as A
participant ": 资源项" as C
participant ": 馆藏资源品种" as D
participant ": 图书品种" as G
participant ": 碟片品种" as H
participant ": 馆藏目录" as I

loop
A -> C: 提供资源信息
activate A
activate C
    C -> D:提供资源的品种
    activate D
        alt
        D -> G:提供图书品种
        activate G
            G -> I:添加到馆藏目录
            activate I
        deactivate G
        else
        D -> H:提供碟片品种
        activate H
            H -> I:添加到馆藏目录
            deactivate I
        deactivate H
        end
    deactivate D
deactivate C

deactivate A
end
@enduml
~~~
#### 3.2. “购入资源”用例顺序图
![UML1](https://github.com/WangHanWei19971211/is_analysis/blob/master/test3/uml4-3.png)
#### 3.3. “购入资源”用例顺序图说明
&#160; &#160; &#160; &#160;由图书管理员提供资源的信息和品种，资源品种分为图书品种和碟片品种，再添加到馆藏目录中，
重复上述步骤知道新增资源全部录入系统中

## 4. “维护书目”用例
#### 4.1. “维护书目”用例PlantUML源码
~~~sql
@startuml
skinparam sequenceParticipant underline
actor ": 图书管理员" as A
participant ": 资源项" as C
participant ": 馆藏资源品种" as D
participant ": 馆藏目录" as I

loop
A -> C: 提供资源名称
activate A
activate C
    C -> A:返回资源信息
deactivate C

A -> C: 更新资源信息
activate C
    C -> D:更新馆藏资源品种信息
    activate D
        D -> I:更新馆藏目录
            activate I
            deactivate I
    deactivate D
deactivate C

deactivate A
end
@enduml
~~~
#### 4.2. “维护书目”用例顺序图
![UML1](https://github.com/WangHanWei19971211/is_analysis/blob/master/test3/uml4-4.png)
#### 4.3. “维护书目”用例顺序图说明
&#160; &#160; &#160; &#160;图书管理员提供资源名称获取到资源信息，管理员更新该资源信息，系统更新资源项、馆藏资源
品种、馆藏目录

## 5. “管理读者信息”用例
#### 5.1. “管理读者信息”用例PlantUML源码
~~~sql
@startuml
skinparam sequenceParticipant underline
actor ": 图书管理员" as A
participant ": 读者" as B

A -> B: 提供读者信息
activate A
activate B
    alt
    B -> B: 登记读者信息
    B -> A:返回借书卡信息
    else
    B -> B: 已有读者信息
    B -> A:提示读者已有借书卡
    end
deactivate B

opt
A -> B:注销读者信息
activate B
    B -> A:显示已注销
deactivate B
end

deactivate A
@enduml
~~~
#### 5.2. “管理读者信息”用例顺序图
![UML1](https://github.com/WangHanWei19971211/is_analysis/blob/master/test3/uml4-5.png)
#### 5.3. “管理读者信息”用例顺序图说明
&#160; &#160; &#160; &#160;为读者办理借书卡时，图书管理员提供读者信息给系统，若已有该读者信息则不能办理借书卡，并
提示已有借书卡，若没有该读者信息则办理借书卡并登记该读者信息。

&#160; &#160; &#160; &#160;为读者办理注销时，图书管理员提供读者信息给系统，删除该读者信息后返回已注销的信息。

## 6. “查询资源”用例
#### 6.1. “查询资源”用例PlantUML源码
~~~sql
@startuml
skinparam sequenceParticipant underline
actor ": 读者" as B1
participant ": 馆藏目录" as I
participant ": 资源项" as C
participant ": 馆藏资源品种" as D
participant ": 图书品种" as G
participant ": 碟片品种" as H

B1 -> I:查询馆藏目录
activate B1
activate I
    I -> C:查询资源项
    activate C
        C -> D:查询馆藏资源品种
        activate D
            alt
            D -> G:查询图书品种
            activate G
            G -> D:返回图书品种
            deactivate G
            else
            D -> H:查询碟片品种
            activate H
            H -> D:返回碟片品种
            deactivate H
            end
        D -> C:返回资源品种
        deactivate D
    C -> I:返回资源信息
    deactivate C
I -> B1:显示查询信息
deactivate I

deactivate B1
@enduml
~~~
#### 6.2. “查询资源”用例顺序图
![UML1](https://github.com/WangHanWei19971211/is_analysis/blob/master/test3/uml4-6.png)
#### 6.3. “查询资源”用例顺序图说明
&#160; &#160; &#160; &#160;读者通过查询馆藏目录能够查询到资源项、馆藏资源品种，系统将资源信息、碟片品种或图书品种返回给读者

## 7. “查询借阅情况”用例
#### 7.1. “维护读者信息”用例PlantUML源码
~~~sql
@startuml
actor ": 读者" as B1
participant ": 资源项" as C
participant ": 馆藏资源品种" as D
participant ": 图书品种" as G
participant ": 碟片品种" as H

activate B1
    B1 -> C:验证读者身份
    activate C
    deactivate C
    loop
    B1 -> C:查询资源
    activate C
        C -> D:查询资源品种
        activate D
             alt
             D -> G:查询图书品种
             activate G
             G -> D:返回图书品种
             deactivate G
             else
             D -> H:查询碟片品种
             activate H
             H -> D:返回碟片品种
             deactivate H
             end
        D -> C:返回资源品种
        deactivate D
        C -> B1:返回资源项及图书状态
    deactivate C
    end
deactivate B1
@enduml
~~~
#### 7.2. “查询借阅情况”用例顺序图
![UML1](https://github.com/WangHanWei19971211/is_analysis/blob/master/test3/uml4-7.png)
#### 7.3. “查询借阅情况”用例顺序图说明
&#160; &#160; &#160; &#160;读者验证身份登陆到图书管理系统后通过资源名可查询到资源项信息和品种信息，以及当前查询的
资源的状态，即借阅情况。读者登陆后可重复上述步骤多次查询图书馆资源的借阅情况。

## 8. “预定图书”用例
#### 5.1. “预定图书”用例PlantUML源码
~~~sql
@startuml
skinparam sequenceParticipant underline
actor ": 读者" as B1
participant ": 读者" as B
participant ": 资源项" as C
participant ": 馆藏资源品种" as D
participant ": 预定记录" as J


B1 -> B: 验证读者身份
activate B1
activate B
deactivate B

B1 -> B: 获取读者限额
activate B
deactivate B

loop
B1 -> C: 获取资源项
activate C
    C -> D:获取资源品种
    activate D
    deactivate D
deactivate C

B1 -> J: 创建预定记录
activate J
deactivate J

end

B1 -> J: 打印预定清单
activate J
deactivate J

deactivate B1
@enduml
~~~
#### 8.2. “预定图书”用例顺序图
![UML1](https://github.com/WangHanWei19971211/is_analysis/blob/master/test3/uml4-8.png)
#### 8.3. “预定图书”用例顺序图说明
&#160; &#160; &#160; &#160;读者验证身份登陆到图书管理系统后可得到自己的资源借阅限额，若限额为0则不能再预定，若资源
限额不为0则可以选择想要预定的资源，创建预定记录，可预定多个资源知道限额为0，结束预定后打印预定清单。

## 9. “取消预定”用例
#### 9.1. “取消预定”用例PlantUML源码
~~~sql
@startuml
skinparam sequenceParticipant underline
actor ": 读者" as B1
participant ": 读者" as B
participant ": 预定记录" as J

B1 -> B: 验证读者身份
activate B1
activate B
deactivate B
loop
B1 -> J: 获取预定记录
activate J
J --> B1: 存在预定记录
deactivate J

B1 -> J: 删除预定记录
activate J
deactivate J

deactivate B1
end
@enduml
~~~
#### 9.2. “取消预定”用例顺序图
![UML1](https://github.com/WangHanWei19971211/is_analysis/blob/master/test3/uml4-9.png)
#### 9.3. “取消预定”用例顺序图说明
&#160; &#160; &#160; &#160;读者验证身份登陆到图书管理系统后可查询到自己的预定记录，若不存在预定记录则无法取消预定，
存在的预定记录取消后，系统删除该预定记录。读者可取消多个预定直到预定记录为空。

## 10. “借阅资源”用例
#### 10.1. “借阅资源”用例PlantUML源码
~~~sql
@startuml
skinparam sequenceParticipant underline
actor ": 读者" as B1
participant ": 读者" as B
participant ": 资源项" as C
participant ": 馆藏资源品种" as D
participant ": 借书记录" as E
participant ": 预定记录" as J


B1 -> B: 验证读者身份
activate B1
activate B
deactivate B

B1 -> B: 获取读者限额
activate B
deactivate B

loop
B1 -> C: 获取资源项
activate C
    C -> D:获取资源品种
    activate D
    deactivate D
deactivate C

B1 -> J: 查询预定记录
activate J
deactivate J
opt
J -> J: 删除预定记录
activate J
deactivate J
end

B1 -> E: 创建借书记录
activate E
deactivate E

B1 -> B: 减少可用限额
activate B
deactivate B

end

B1 -> J: 打印借阅清单
activate J
deactivate J

deactivate B1
@enduml
~~~
#### 10.2. “借阅资源”用例顺序图
![UML1](https://github.com/WangHanWei19971211/is_analysis/blob/master/test3/uml4-10.png)
#### 10.3. “借阅资源”用例顺序图说明
&#160; &#160; &#160; &#160;读者身份验证身份登陆到图书管理系统，获取读者限额，若限额已满则不能借书，
限额未满时可继续借书。获取资源项及资源品种，查询预定记录，有预定记录则将该条预定记录删除。创建借书记录，
并将该资源馆藏数量减少，读者的限额也减少。最后打印借书清单。
