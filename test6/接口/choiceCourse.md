<!-- markdownlint-disable MD033-->
<!-- 禁止MD033类型的警告 https://www.npmjs.com/package/markdownlint -->

# 接口：choiceCourse

- 功能：
    选择课程。
    
- 权限：
    已登入的学生。    
    
- API请求地址： 
    接口基本地址/v1/api/choiceCourse

- 请求方式 ：
    POST

- 请求实例：

        {
            "id":"123456789987",
            "course_id":"1",
            "type":"student"
        }
        
- 请求参数说明:        

  |参数名称|说明|
  |:---------:|:--------------------------------------------------------| 
  |id|type为student时是学生学号，type为teacher时是老师的工号。|
  |course_id|课程ID|
  |type|用户类型，student（学生）或者teacher（老师）|
  
- 返回实例：

        {         
            "status": true,
        }
 
- 返回参数说明：    
 
  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |status|bool类型，true表示正确的返回，false表示有错误|
  
  
  
  
