---
sidebar: auto
---

# API

::: tip
大部分接口无法直接请求，需进行 JWT 认证后方可请求
:::

## 通用返回结果
每一个请求的接口都将包含以下部分：

| 参数名称                  | 类型  | 说明  |
| ------------- | ----:| ---:|
| code      | number | 返回值 |
| msg      | string | 返回消息 |

## 登录

### 用户登录

#### 接口地址
`POST /user/login`

#### 请求参数
| 参数名称        | 是否必须           | 类型  | 说明  |
| ------------- |:-------------:| -----:| ----:|
| username      | 是 | string | 用户名 |
| password      | 是 | string | 密码 |

#### 返回值
| 参数名称                  | 类型  | 说明  |
| ------------- | ----:| ---:|
| data      | object | 返回数据 |
| token      | string | 登录令牌 |

### 用户信息

#### 接口地址
`POST /user/info`

#### 请求参数
无

#### 返回值
| 参数名称                  | 类型  | 说明  |
| ------------- | ----:| ---:|
| data      | object | 返回数据 |
| avatar      | string | 用户头像 |
| id      | number | 用户ID |
| nickname      | string | 用户昵称 |
| username      | string | 登录账号 |
| roles      | array | 用户权限 |

## 首页

### 获取首页数据

#### 接口地址
`GET /book/home`

#### 请求参数
无

#### 返回值
| 参数名称                  | 类型  | 说明  |
| ------------- | ----:| ---:|
| data      | Object | 返回数据 |
| book      | number | 电子书总数 |
| rank      | number | 总评分数 |
| shelf      | number | 总书架数 |
| user      | number | 总用户数 |

## 图书管理

### 获取电子书列表

#### 接口地址
`GET /book/list`

#### 请求参数
| 参数名称        | 是否必须           | 类型  | 说明  |
| ------------- |:-------------:| -----:| ----:|
| page      | 否 | number | 当前页数 |
| pageSize  | 否 | number | 每页显示数据量 |
| sort  | 否 | string | 排序字段 |
| title  | 否 | string | 标题 |
| author | 否 | string | 作者 |
| category  | 否 | string | 分类名称 |

#### 返回值
| 参数名称                  | 类型  | 说明  |
| ------------- | ----:| ---:|
| page      | number | 当前页数 |
| pageSize      | number | 每页显示数据量 |
| total      | number | 总数据量 |
| data      | array | 电子书列表 |
| author      | string | 作者 |
| category      | number | 分类ID |
| categoryText      | string | 分类名称 |
| cover      | string | 封面URL |
| fileName      | string | 文件名 |
| id      | string | 电子书ID |
| language      | string | 语种 |
| publisher      | string | 出版社 |
| rootFile      | string | 根文件路径 |
| title      | string | 书名 |

### 删除电子书

#### 接口地址
`GET /book/delete`

#### 请求参数
| 参数名称        | 是否必须           | 类型  | 说明  |
| ------------- |:-------------:| -----:| ----:|
| fileName  | 是 | string | 电子书文件名 |

#### 返回值
| 参数名称                  | 类型  | 说明  |
| ------------- | ----:| ---:|
| data      | null | 无 |

### 获取电子书

#### 接口地址
`GET /book/get`

#### 请求参数
| 参数名称        | 是否必须           | 类型  | 说明  |
| ------------- |:-------------:| -----:| ----:|
| fileName  | 否 | string | 电子书文件名 |

#### 返回值
| 参数名称                  | 类型  | 说明  |
| ------------- | ----:| ---:|
| data      | object | 电子书 |
| author      | string | 作者 |
| category      | number | 分类ID |
| categoryText      | string | 分类名称 |
| cover      | string | 封面URL |
| fileName      | string | 文件名 |
| id      | string | 电子书ID |
| language      | string | 语种 |
| publisher      | string | 出版社 |
| rootFile      | string | 根文件路径 |
| title      | string | 书名 |
| contents      | array | 电子书目录 |
| contentsTree      | object | 树状电子书目录 |

### 编辑电子书

#### 接口地址
`POST /book/update`

#### 请求参数
| 参数名称        | 是否必须           | 类型  | 说明  |
| ------------- |:-------------:| -----:| ----:|
| author      | 否 |string | 作者 |
| cover      | 否 | string | 封面URL |
| coverPath      | 否 | string | 封面路径 |
| fileName      | 是 | string | 文件名 |
| filePath      | 否 | string | 文件路径 |
| language      | 否 | string | 语种 |
| originalName      | 否 | string | 电子书文件原名 |
| publisher      | 否 | string | 出版社 |
| rootFile      | 否 | string | 根文件路径 |
| title      | 否 | string | 书名 |
| unzipPath      | 否 | string | 解压后文件路径 |

#### 返回值
| 参数名称                  | 类型  | 说明  |
| ------------- | ----:| ---:|
| data      | null | 无 |

### 上传并解析电子书

#### 接口地址
`POST /book/upload`

#### 请求参数
| 参数名称        | 是否必须           | 类型  | 说明  |
| ------------- |:-------------:| -----:| ----:|
| file      | 是 | binary | 电子书文件 |

#### 返回值
| 参数名称                  | 类型  | 说明  |
| ------------- | ----:| ---:|
| data      | object | 电子书 |
| author      | string | 作者 |
| category      | number | 分类ID |
| categoryText      | string | 分类名称 |
| cover      | string | 封面URL |
| fileName      | string | 文件名 |
| id      | string | 电子书ID |
| language      | string | 语种 |
| publisher      | string | 出版社 |
| rootFile      | string | 根文件路径 |
| title      | string | 书名 |
| contents      | array | 电子书目录 |
| contentsTree      | object | 树状电子书目录 |

### 新增电子书

#### 接口地址
`POST /book/create`

#### 请求参数
| 参数名称        | 是否必须           | 类型  | 说明  |
| ------------- |:-------------:| -----:| ----:|
| author      | 否 |string | 作者 |
| cover      | 否 | string | 封面URL |
| coverPath      | 否 | string | 封面路径 |
| fileName      | 是 | string | 文件名 |
| filePath      | 否 | string | 文件路径 |
| language      | 否 | string | 语种 |
| originalName      | 否 | string | 电子书文件原名 |
| publisher      | 否 | string | 出版社 |
| rootFile      | 否 | string | 根文件路径 |
| title      | 否 | string | 书名 |
| unzipPath      | 否 | string | 解压后文件路径 |
| url      | 否 | string | 电子书下载路径 |

#### 返回值
| 参数名称                  | 类型  | 说明  |
| ------------- | ----:| ---:|
| data      | null | 无 |

### 获取电子书分类

#### 接口地址
`GET /book/category`

#### 请求参数
无

#### 返回值
| 参数名称                  | 类型  | 说明  |
| ------------- | ----:| ---:|
| data      | array | 分类列表 |
| label      | string | 分类名称 |
| value      | number | 分类ID |
| num      | number | 分类下电子书总数 |
