
<!-- TOC depthfrom:1 depthto:6 orderedlist:false -->

- [API 编写规范](#api-%E7%BC%96%E5%86%99%E8%A7%84%E8%8C%83)
    - [ip:port/api/+模块+路径](#ipportapi%E6%A8%A1%E5%9D%97%E8%B7%AF%E5%BE%84)
    - [路径（Endpoint）统一采用驼峰式命名](#%E8%B7%AF%E5%BE%84endpoint%E7%BB%9F%E4%B8%80%E9%87%87%E7%94%A8%E9%A9%BC%E5%B3%B0%E5%BC%8F%E5%91%BD%E5%90%8D)
    - [响应基本格式：](#%E5%93%8D%E5%BA%94%E5%9F%BA%E6%9C%AC%E6%A0%BC%E5%BC%8F)
    - [响应实体格式](#%E5%93%8D%E5%BA%94%E5%AE%9E%E4%BD%93%E6%A0%BC%E5%BC%8F)
    - [响应列表格式](#%E5%93%8D%E5%BA%94%E5%88%97%E8%A1%A8%E6%A0%BC%E5%BC%8F)
    - [响应分页格式](#%E5%93%8D%E5%BA%94%E5%88%86%E9%A1%B5%E6%A0%BC%E5%BC%8F)

<!-- /TOC -->

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


