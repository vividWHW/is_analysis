﻿<!-- markdownlint-disable MD033-->
<!-- 禁止MD033类型的警告 https://www.npmjs.com/package/markdownlint -->

# 接口：login 

- 功能：
    登录到平台。
    
- 权限：
    访客。    
    
- API请求地址： 
    接口基本地址/v1/api/login

- 请求方式 ：
    POST

- 请求实例：

        {
            "id":"123456789987",
            "password":"whw123",
            "type":"student"
        }
        
- 请求参数说明:        

  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |id|type为student时是学生学号，type为teacher时是老师的工号。|
  |password|用户的密码| 
  |type|用户类型，student（学生）或者teacher（老师）|
  
- 返回实例：

        { 
            "status": true,
            "info": null,    
        }
 
- 返回参数说明：    
 
  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |status|bool类型，true表示正确的返回，false表示有错误|
  |info|返回结果说明信息|
