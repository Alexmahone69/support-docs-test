
### 请求方法

POST


### 请求地址

/api/c/compapi/v2/cc/delete_service_template/


### 通用参数

| 字段 | 类型 | 必选 |  描述 |
|-----------|------------|--------|------------|
| bk_app_code  |  string    | 是 | 应用 ID     |
| bk_app_secret|  string    | 是 | 安全密钥(应用 TOKEN)，可以通过 蓝鲸智云开发者中心 -> 点击应用 ID -> 基本信息 获取 |
| bk_token     |  string    | 否 | 当前用户登录态，bk_token 与 bk_username 必须一个有效，bk_token 可以通过 Cookie 获取 |
| bk_username  |  string    | 否 | 当前用户用户名，应用免登录态验证白名单中的应用，用此字段指定当前用户 |


### 功能描述

根据服务模板 ID 删除服务模板

### 请求参数



#### 接口参数

| 字段                 |  类型      | 必选	   |  描述                 |
|----------------------|------------|--------|-----------------------|
| service_template_id | int  | 是   | 服务模板 ID |
| bk_biz_id                  | int        | 是     | 业务 ID|

### 请求参数示例

```python
{
  "bk_app_code": "esb_test",
  "bk_app_secret": "xxx",
  "bk_username": "xxx",
  "bk_token": "xxx",
  "bk_biz_id": 1,
  "service_template_id": 1
}
```

### 返回结果示例

```python
{
  "result": false,
  "code": 1199056,
  "message": "delete service template failed",
  "permission": null,
  "request_id": "e43da4ef221746868dc4c837d36f3807",
  "data": null
}
```

### 返回结果参数说明

#### response

| 名称  | 类型  | 描述 |
|---|---|---|
| result | bool | 请求成功与否。true:请求成功；false 请求失败 |
| code | int | 错误编码。 0 表示 success，>0 表示失败错误 |
| message | string | 请求失败返回的错误信息 |
| permission    | object | 权限信息    |
| request_id    | string | 请求链 id    |
| data | object | 请求返回的数据 |