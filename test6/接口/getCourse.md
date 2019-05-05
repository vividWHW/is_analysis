<!-- markdownlint-disable MD033-->
<!-- 禁止MD033类型的警告 https://www.npmjs.com/package/markdownlint -->

# 接口：getCourse

- 权限：
    学生/老师。

- 功能：
    返回所有课程的列表。

- API请求地址：
   接口基本地址/v1/api/getCourse

- 请求方式 ：
    GET

- 请求参数:
    无

- 返回实例：

        {
            "status": true,
            "course_id":"1",
            "course_name":"信息系统分析", 
            "test_id":"1",
            "test_title":"实验6：期末项目"
        }

- 返回参数说明：

  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|
  |status|bool类型，true表示正确的返回，false表示有错误|
  |course_id|课程id|
  |course_name|课程名|
  |test_id|实验id|
  |test_title|实验名称|
