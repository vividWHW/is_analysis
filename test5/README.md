# 实验5：图书管理系统数据库设计与界面设计
学号|班级|姓名|我的照片
:-:|:-:|:-:|:-:
201610414323|软件(本)16-3|23.王涵玮|<img src="https://github.com/WangHanWei19971211/is_analysis/blob/master/test1/myself.jpg" width="66"/>

## 1.数据库表设计
#### 1.1. 资源项表

|      字段     |      类型     | 主键、外键 | 可以为空 | 默认值 |   约束   |    说明    |
|:-------------:|:-------------:|:----------:|:--------:|:------:|:--------:|:----------:|
|   resourceId  | varchar2(100) |    主键    |    否    |  null  | 无重复 | 资源流水号 |
| resourceState |  varchar2(10) |            |    否    | 未借出 |          |  资源状态  |
|  resourceName | varchar2(100) |    外键    |    否    |        |          |  资源名称  |

#### 1.2. 馆藏资源品种表
|      字段      |      类型     | 主键、外键 | 可以为空 | 默认值 | 约束 |      说明      |
|:--------------:|:-------------:|:----------:|:--------:|:------:|:----:|:--------------:|
|  resourceName  | varchar2(100) |    主键    |    否    |  null  |      |    资源名称    |
|   classNumber  | varchar2(100) |            |    是    |        |      |   国际出班号   |
|      price     | varchar2(100) |            |    是    |  null  |      |      价格      |
| resourceNumber |     int(5)    |            |    否    |    0   |      |    馆藏数量    |
|  borrowNumber  |     int(5)    |            |    否    |    0   |      |    可借数量    |
|     variety    |  varchar(100) |    外键    |    否    |        |      | 图书、碟片品种 |
|  bookcaseName  | varchar2(100) |            |    是    |  null  |      |    书架名称    |

#### 1.3. 图书品种表
|    字段    |      类型     | 主键、外键 | 可以为空 | 默认值 | 约束 |   说明   |
|:----------:|:-------------:|:----------:|:--------:|:------:|:----:|:--------:|
|    name    | varchar2(100) |    主键    |    否    |  null  |      |   书名   |
|     id     | varchar2(100) |            |    是    |        |  无重复  |   编号   |
|   author   | varchar2(100) |            |    是    |  null  |      |   作者   |
|    press   | varchar2(100) |            |    是    |  null  |      |  出版社  |
|  pressDate | varchar2(100) |            |    是    |  null  |      | 出版日期 |
| borrowDate | varchar2(100) |            |    否    |    0   |      | 可借天数 |

#### 1.4. 碟片品种表
|        字段       |      类型     | 主键、外键 | 可以为空 | 默认值 | 约束 |   说明   |
|:-----------------:|:-------------:|:----------:|:--------:|:------:|:----:|:--------:|
|        name       | varchar2(100) |    主键    |    否    |  null  |      |  碟片名  |
|     id     | varchar2(100) |            |    是    |        |  无重复  |   编号   |
|      discType     | varchar2(100) |            |    是    |        |      | 碟片类型 |
|       number      |     int(5)    |            |    否    |    0   |      |  碟片数  |
| productionCompany | varchar2(100) |            |    是    |  null  |      | 制作公司 |
|     borrowDate    | varchar2(100) |            |    否    |    0   |      | 可借天数 |

#### 1.5. 馆藏目录表
|        字段       |      类型     | 主键、外键 | 可以为空 | 默认值 | 约束 |   说明   |
|:-----------------:|:-------------:|:----------:|:--------:|:------:|:----:|:--------:|
|  resourceName | varchar2(100) |    外键    |    否    |        |          |  资源名称  |
#### 1.6. 读者表
|        字段       |     类型     | 主键、外键 | 可以为空 | 默认值 |   约束   |    说明    |
|:-----------------:|:------------:|:----------:|:--------:|:------:|:--------:|:----------:|
|      userName     | varchar2(20) |            |    否    |  null  |          |    姓名    |
|        sex        | varchar2(10) |            |    否    |        |          |    性别    |
|      idNumber     | varchar2(20) |            |    否    |        |          |  身份证号  |
| libraryCardNumber | varchar2(20) |    主键    |    否    |        | 主键约束 |  借书卡号  |
| limitationOfBooks |    int(5)    |            |    否    |    0   |          |  图书限额  |
|    borrowedBook   |    int(5)    |            |    否    |    0   |          | 已借图书数 |
|  limitationOfDisc |    int(5)    |            |    否    |    0   |          |  碟片限额  |
|    borrowedDisc   |    int(5)    |            |    否    |    0   |          | 已借碟片数 |

#### 1.7. 借书记录表
|        字段       |     类型     | 主键、外键 | 可以为空 | 默认值 |  约束  |    说明    |
|:-----------------:|:------------:|:----------:|:--------:|:------:|:------:|:----------:|
|      borrowId     | varchar2(50) |    主键    |    否    |        | 无重复 | 借书记录号 |
|     borrowDate    | varchar2(20) |            |    否    |  null  |        |  借书日期  |
|     returnDate    | varchar2(20) |            |    否    |  null  |        |  应还日期  |
|    returnedDate   | varchar2(20) |            |    否    |  null  |        |  归还日期  |
| libraryCardNumber | varchar2(20) |    外键    |    否    |        | 无重复 |  借书卡号  |
|   resourceId  | varchar2(100) |    外键    |    否    |  null  | 无重复 | 资源流水号 |
|  managerId  | varchar2(30) |    外键    |    否    |        | 无重复 |  职工号  |

#### 1.8. 预定记录表
|     字段    |     类型     | 主键、外键 | 可以为空 | 默认值 |  约束  |   说明   |
|:-----------:|:------------:|:----------:|:--------:|:------:|:------:|:--------:|
|  reserveId  | varchar2(50) |    主键    |    否    |        | 无重复 | 预定编号 |
| reserveDate | varchar2(20) |            |    否    |  null  |        | 预定日期 |
| reserveTime | varchar2(20) |            |    否    |  null  |        | 预定时间 |
| libraryCardNumber | varchar2(20) |    外键    |    否    |        | 主键约束 |  借书卡号  |
|  resourceName  | varchar2(100) |    外键    |    否    |  null  |      |    资源名称    |

#### 1.9. 图书管理员表
|     字段    |     类型     | 主键、外键 | 可以为空 | 默认值 |  约束  |   说明   |
|:-----------:|:------------:|:----------:|:--------:|:------:|:------:|:--------:|
|  managerId  | varchar2(30) |    主键    |    否    |        | 无重复 |  职工号  |
| managerName | varchar2(20) |            |    否    |  null  |        |   姓名   |
|   password  | varchar2(30) |            |    否    |  null  |        | 登录密码 |

#### 1.10. 逾期记录表
|    字段    |     类型     | 主键、外键 | 可以为空 | 默认值 |  约束  |    说明    |
|:----------:|:------------:|:----------:|:--------:|:------:|:------:|:----------:|
|  overdueId | varchar2(30) |    主键    |    否    |  null  | 无重复 | 逾期记录号 |
| overdueDay |    int(5)    |            |    否    |    1   |        |  逾期天数  |
|    fine    |    int(5)    |    外键    |    否    |  null  |        |  应缴罚款  |

#### 1.11. 罚款细则表
|    字段    |     类型     | 主键、外键 | 可以为空 | 默认值 |  约束  |    说明    |
|:----------:|:------------:|:----------:|:--------:|:------:|:------:|:----------:|
|    fine    |    int(5)    |    主键    |    否    |  null  |        |  应缴罚款  |

## 2. 界面设计
#### 2.1. 借书界面设计
<a href="https://wanghanwei19971211.github.io/is_analysis_pages/book/index.html" target="_blank">借书界面 is_analysis_pages</a>

![借书界面](https://github.com/WangHanWei19971211/is_analysis/blob/master/test5/book.jpg)

用例图参见：<a href="https://github.com/WangHanWei19971211/is_analysis/tree/master/test2" target="_blank">实验二 用例图</a>

类图参见：<a href="https://github.com/WangHanWei19971211/is_analysis/tree/master/test3" target="_blank">实验三 类图</a>

顺序图参见：<a href="https://github.com/WangHanWei19971211/is_analysis/tree/master/test4" target="_blank">实验四 顺序图</a>

#### API接口如下：
1.获取读者信息信息
  
  请求方式：GET
  
  请求参数：
  
  |        参数名称       |      必填	     | 说明 |
  |:-----------------:|:-------------:|:----------:|
  |  libraryCardNumber| 是 | 读者的借书卡号   |
  |  access_roken| 是 | 用于验证请求合法性的认证信息   |
  |  access_token| 是 |    用于验证请求合法性的认证信息。   |
  | userName| 否 |    读者用户名   |  
  | method| 是 |    固定为 “GET”   |
  返回示例：
  ```
  {
      "idNumber": "510603199912126666",
      "limitationOfBooks": "10",
      "borrowedBook": "3",
      "limitationOfDisc": "10",
      "borrowedDisc": "0",  
      "sex": "女",
      "code": 200
  }
  ```
  
  返回参数说明：
 
 |     参数名称  |  说明	|
 |:--------:|:-------:|
 | idNumber| 身份证号 |
 | limitationOfBooks| 图书限额 |
 | borrowedBook| 已借图书数 |
 | limitationOfDisc| 碟片限额 |
 | borrowedDisc| 已借碟片数 |
  | sex| 性别 |
 |  code| 返回码 | 

2、验证资源是否存在

请求方法：POST

请求参数：

|        参数名称       |      必填	     | 说明 |
|:-----------------:|:-------------:|:----------:|
|  resourceName | 是 |    资源名   |
|  action| 是 |    固定为 “checkResourceName”   |
|  access_token| 是 |    用于验证请求合法性的认证信息。   |
| method| 是 |    固定为 “GET”   |

返回示例：
```
{
    "info":"验证成功",
    "code":200
}
```
返回参数说明：

|     参数名称  |  说明	|
|:--------:|:-------:|
| info| 返回的提示信息 |
|  code| 返回码 |

3、借阅资源

请求方法：POST

请求参数：

|        参数名称       |      必填	     | 说明 |
|:-----------------:|:-------------:|:----------:|
|  resourceName | 是 |    资源名   |
  |  libraryCardNumber| 是 | 读者的借书卡号   |
|  action| 是 |    固定为 “checkResourceName”   |
|  access_token| 是 |    用于验证请求合法性的认证信息。   |
| method| 是 |    固定为 “GET”   |

返回示例：
```
{
    "borrowId":"abcdef123456789",
    "borrowDate":"2019-04-01",
    "returnDate":"2019-05-01",
    "code":200
}
```
返回参数说明：

|     参数名称  |  说明	|
|:--------:|:-------:|
| borrowId| 借书记录号 |
| borrowDate| 借书日期 |
| returnDate| 应还日期 |
|  code| 返回码 |


