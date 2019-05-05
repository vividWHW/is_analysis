<!-- markdownlint-disable MD033-->
<!-- 禁止MD033类型的警告 https://www.npmjs.com/package/markdownlint -->

# 接口：setInfo  

- 功能：
    管理用户信息。
    
- 权限：
    学生/老师：管理信息，必须先登录。    
    
- API请求地址： 
    接口基本地址/v1/api/setInfo

- 请求方式 ：
    POST

- 请求实例：

        {
            "user_id":"123456789987",
            "password":"abcdefg123"
        }
        
- 请求参数说明:        

  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |user_id|用户的ID号。对应表USERS.USER_ID的值|
  |password|用户的密码。| 
  
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
