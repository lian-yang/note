## Swagger**文档语法说明**



@Summary：简单阐述 API 的功能

@Description：API 详细描述

@Tags：API 所属分类

@Accept：API 接收参数的格式

@Produce：输出的数据格式，这里是 JSON 格式

@Param：参数，分为 6 个字段，其中第 6 个字段是可选的，各字段含义为：

1. ​    参数名称
2. ​    参数在 HTTP 请求中的位置（body、path、query）
3. ​    参数类型（string、int、bool 等）
4. ​    是否必须（true、false）
5. ​    参数描述
6. ​    选项，这里用的是 default() 用来指定默认值



@Success Or @Failure 成功失败返回数据格式，分为 4 个字段

1. ​    HTTP 返回 Code
2. ​    返回数据类型
3. ​    返回数据模型
4. ​    说明



@Router：路由格式，分为 2 个字段：

1. ​    API 路**径**
2. ​    HTTP 方法



API 文档有更新时，要重新执行 swag init 并重新编译