
# API 编写规范
采用`RESTful API`编程规范，资料可以参考[这里](http://www.ruanyifeng.com/blog/2014/05/restful_api.html)

本项目API总体遵循以下原则：
<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [API 编写规范](#api-编写规范)
  - [1. `ip:port/api/`+`模块`+`路径`](#1-ipportapi模块路径)
  - [2. 路径（Endpoint）统一采用`蛇形命名法`](#2-路径endpoint统一采用蛇形命名法)
  - [3. 响应基本格式：](#3-响应基本格式)
  - [4. 响应实体格式](#4-响应实体格式)
  - [5. 响应列表格式](#5-响应列表格式)
  - [6. 响应分页格式](#6-响应分页格式)
- [log 的编写](#log-的编写)

<!-- /code_chunk_output -->

 
## 1. `ip:port/api/版本/+`模块`+`路径`

- 比如
  - `192.168.124.243:8081/api/v1/search/get_info` 表示`v1`版本的接口
  - `192.168.124.243:8081/api/v2/search/get_info` 表示`v2`版本的接口


## 2. 路径（Endpoint）统一采用`蛇形命名法`

- 下划线"_"分隔
- http://xxxx/get_user



## 3. 响应基本格式：

```
{
    "code": 200,
    "msg": "success"
}
```

其中

code : 请求处理状态（可以根据业务自行添加）

```
200: 请求处理成功

500: 请求处理失败

401: 请求未认证，跳转登录页

406: 请求未授权，跳转未授权提示页
```

msg: 请求处理消息（可以根据业务自行添加）
```
code=200 且 msg =="success": 请求处理成功

code=200 且 msg !="success": 请求处理成功, 普通消息提示：msg内容

code=500: 请求处理失败，警告消息提示：msg内容
```


## 4. 响应实体格式

```
{
    "code": 200,
    "msg": "success",
    "data": [
        "entity": {
            "id": 1,
            "name": "XXX",
            "phone": "XXX"
        }
    ]
}
```

## 5. 响应列表格式

```
{
    "code": 200,
    "msg": "success",
    "data": {
        "list":[
            {
                "id": 1,
                "name": "XXX",
                "code": "XXX"
            },
             {
                "id": 2,
                "name": "XXX",
                "code": "XXX"
            },
             {
                "id": 3,
                "name": "XXX",
                "code": "XXX"
            }
        ]
        
    }
}
```

## 6. 响应分页格式

```
{
    "code": 200,
    "msg":"success",
    "data": {
        "totalCount": 2,
        "totalPage": 1
        "pageNo": 1,
        "pageSize": 10,
        "list": [
            {
                "id": 1,
                "name": "XXX",
                "code": "H001"
            },
            {
                "id": 1,
                "name": "XXX",
                "code": "H001"
            },
            {
                "id": 1,
                "name": "XXX",
                "code": "H001"
            }
 ],
        
    }
}
```
- data.totalCount: 总记录数
- data.pageNo: 当前页码
- data.pageSize: 每页大小
- data.totalPage: 总页数


