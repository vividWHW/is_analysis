<!-- markdownlint-disable MD033-->
<!-- 禁止MD033类型的警告 https://www.npmjs.com/package/markdownlint -->

# 接口：setCourseInfo 

- 功能：
    管理课程信息。
    
- 权限：
    老师：管理课程信息，必须先登录。    
    
- API请求地址： 
    接口基本地址/v1/api/setCourseInfo

- 请求方式 ：
    POST

- 请求实例：

        {
            "course_id":"1",          
        }
        
- 请求参数说明:        

  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |course_id|课程ID|
  
- 返回实例：

        {         
            "status": true,
            "course_name":"信息系统分析", 
            "test_id":"1"
        }
 
- 返回参数说明：    
 
  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |status|bool类型，true表示正确的返回，false表示有错误|
  |course_name|课程名|
  |test_id|实验id|


