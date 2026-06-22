---
name: Vibe Coding
description: 在涉及到编写代码时，尽量按照以下规范去编写，注释、提示消息、日志请使用中文
---

# Vibe Coding 规范

本规范用于指导 AI 代码生成，确保生成的代码符合企业级 Java 项目的通用规范和架构风格。

---

## 1. 项目架构

### 1.1 项目结构

项目采用多模块分层架构，推荐结构如下：
- common：公共模块，包含统一返回封装、异常定义、工具类
- model：数据模型模块，包含 Entity、VO、Request、BO、DAO
- service：业务逻辑模块，包含 Service 接口和实现
- web：Web 应用模块，包含 Controller、配置类
- 其他业务模块：按功能划分

### 1.2 技术栈（通用）

- Spring Boot（主流版本）
- 持久层框架（MyBatis-Plus / MyBatis / JPA / JDBC Template 等）
- 关系型数据库（MySQL / PostgreSQL 等）
- 缓存（Redis / Caffeine 等）
- 搜索引擎（Elasticsearch / Solr 等，可选）
- API 文档（Swagger / SpringDoc / Knife4j）
- 安全认证（JWT / Spring Security / OAuth2）
- 工具库（Lombok / Hutool / Guava 等）
- 分页组件（PageHelper / MyBatis-Plus 分页等）

---

## 2. 代码生成规范

### 2.1 Controller 层规范

**类注解要求：**
- 必须添加 RestController 注解标记为 REST API 控制器
- 必须添加 Slf4j 注解启用日志
- 必须添加 Api 或 Tag 注解设置模块中文名称
- 必须添加 RequestMapping 注解设置基础路径，推荐带版本前缀如 /api/v1

**方法注解要求：**
- 只能使用  POST 请求
- POST 提交类接口使用 PostMapping 注解
- 所有方法必须添加 ApiOperation 或 Operation 注解并设置中文操作描述

**方法签名规范：**
- 方法必须为 public 修饰
- 返回值类型必须统一封装，如 ResultInfo 或 Result
- GET 请求参数使用 RequestParam 注解
- POST 请求体使用 RequestBody 注解
- 路径参数使用 PathVariable 注解
- 请求对象需要添加 Validated 或 Valid 注解进行参数校验

**返回值规范：**
- 成功返回调用统一成功方法，如 ResultInfo.success(data)
- 失败返回调用统一失败方法，如 ResultInfo.buildFail(message)

---

### 2.2 Service 层规范

**接口定义要求：**
- 接口名必须以 Service 结尾
- 方法命名使用小驼峰风格
- 分页方法返回类型为分页对象，如 PageInfo 或 Page
- 创建类方法返回主键 ID
- 查询单条返回 VO 对象或 Entity
- 查询列表返回分页对象或 List

**实现类要求：**
- 类名必须以 ServiceImpl 结尾
- 必须添加 Service 注解标记为服务组件
- 必须添加 Slf4j 注解启用日志

**依赖注入要求：**
- 推荐使用 Resource 注解或 Autowired 注解进行依赖注入
- 推荐使用构造函数注入方式（Spring 推荐）

**事务要求：**
- 涉及数据库写入操作必须添加 Transactional 注解
- rollbackFor 属性必须包含业务异常和 Exception

**查询方式要求：**
- 优先使用框架提供的链式查询方式
- 复杂查询可使用条件构造器方式
- 单条查询返回单个对象
- 多条查询返回列表对象

**分页查询要求：**
- 使用分页组件开启分页
- 传入分页参数 pageNum 和 pageSize
- 返回分页结果对象

---

### 2.3 Entity 层规范

**类注解要求：**
- 必须添加 Data 注解自动生成 getter 和 setter（或使用 Lombok）
- 必须添加表名映射注解，如 TableName 或 Entity
- 必须实现 Serializable 接口

**字段要求：**
- 必须定义 serialVersionUID 静态常量
- 主键字段添加主键注解并设置自增策略
- 状态字段使用 Integer 类型，需定义常量说明（如 0-禁用 1-启用）
- 时间字段使用 LocalDateTime 或 Date 类型

**数据库类型映射：**
- bigint 类型映射为 Long
- int 和 tinyint 类型映射为 Integer
- varchar 和 char 类型映射为 String
- text 类型映射为 String
- datetime 和 timestamp 类型映射为 LocalDateTime
- decimal 类型映射为 BigDecimal
- json 类型映射为 String 或对象 JSON 字符串

---

### 2.4 Request 层规范

**类注解要求：**
- 必须添加 Data 注解
- 必须实现 Serializable 接口

**字段校验要求：**
- 必填字段添加 NotNull 或 NotBlank 注解并配置中文提示消息
- 字符串长度使用 Size 或 Length 注解限制
- 数值范围使用 Min 和 Max 注解限制
- 默认值直接在字段上赋值

---

### 2.5 VO 层规范

**类注解要求：**
- 必须添加 Data 注解
- 必须实现 Serializable 接口

**字段要求：**
- 只包含需要返回给前端的字段
- 时间字段添加 JsonFormat 注解并设置格式化模式
- 敏感字段（如密码）不得出现在 VO 中

---

### 2.6 BO 层规范

**类注解要求：**
- 必须添加 Data 注解
- 必须实现 Serializable 接口

**用途说明：**
- 用于 Service 层内部业务逻辑传递
- 字段比 Entity 精简，比 VO 更贴近业务

---

### 2.7 DAO / Repository 层规范

**接口要求：**
- 必须添加 Mapper 或 Repository 注解
- 推荐继承框架提供的基础接口，如 BaseMapper 或 JpaRepository
- 自定义 SQL 方法使用 Param 或 Param 注解标记参数
- 复杂查询可使用 XML 或注解方式编写 SQL

---

### 2.8 异常处理规范

**业务异常：**
- 使用自定义业务异常类抛出业务错误
- 构造方法传入中文错误消息
- 全局异常处理器捕获并统一返回

**参数校验异常：**
- Controller 层参数校验失败自动处理
- 返回统一失败响应包装校验错误消息
---

## 3. 代码风格

### 3.1 日志使用

- 类上添加 Slf4j 注解引入日志
- info 级别记录正常业务操作
- error 级别记录异常信息并传入异常对象
- debug 级别记录调试信息，生产环境不输出
- warn 级别记录警告信息

### 3.2 判空处理

- 对象判空使用 Objects.nonNull 和 Objects.isNull
- 字符串判空使用 StringUtils 工具类方法
- 集合判空使用 CollectionUtils 工具类方法
- 复杂场景使用 Optional 进行链式操作
- 避免直接使用 null 判断

### 3.3 流式操作

- 集合处理优先使用 Stream API
- filter 用于条件过滤
- map 用于类型转换
- collect 用于收集结果
- 复杂逻辑提取为方法引用

### 3.4 时间处理

- 推荐使用 LocalDateTime 表示日期时间（JDK 8+）
- 使用 DateTimeFormatter 进行格式化
- 使用 isBefore 和 isAfter 进行比较
- 时间戳转日期使用工具类统一处理

### 3.5 异常处理

- 业务异常统一抛出，由全局处理器处理
- 不要捕获异常后不处理
- 异常日志必须记录堆栈信息
- 对外接口不暴露内部异常详情

---

## 4. 注意事项

1. 所有实体类必须实现 Serializable 接口并定义 serialVersionUID
2. Service 层依赖注入推荐使用 @Autowired 注解，不要用@RequiredArgsConstructor
3. Controller 方法返回值必须统一使用 项目统一封装的实体返回类
4. VO 返回时间字段必须添加 JsonFormat 注解格式化
5. Request 字段必须使用 JSR-303 注解进行参数校验
6. 所有类添加 Slf4j 注解并使用 log 对象记录日志
7. 分页查询必须使用分页组件，传入 pageNum 和 pageSize
8. 数据库写入操作必须添加 Transactional 事务注解并指定回滚异常
9. 敏感信息（密码、密钥等）不得明文返回给前端
10. SQL 查询注意 SQL 注入防护，使用预编译参数

---

## 5. 二方api调用封装
### 5.1 封装
- 接口地址通过枚举配置，统一使用一个目录来管理这个二方请求
- 返回值统一加工

## 6. Vibe Coding 提示词模板

### 6.1 生成 CRUD 接口

指令格式：
在某模块中创建某管理功能的 CRUD 接口，包含以下要求：
- Entity 对应某表，包含某字段
- 需要接口：列表分页、创建、详情、更新、删除
- 请求字段和响应字段说明
- 查询条件和排序规则

### 6.2 生成查询接口

指令格式：
创建某查询接口，包含以下要求：
- 是否支持分页
- 查询条件字段说明
- 返回字段说明
- 排序规则说明

### 6.3 生成 Service 方法

指令格式：
在某 Service 中添加方法，包含以下要求：
- 方法名称说明
- 入参类型和说明
- 出参类型和说明
- 业务逻辑描述
- 是否需要事务

### 6.4 生成 Entity

指令格式：
创建某表的 Entity 类，包含以下要求：
- 表名说明
- 字段列表及类型
- 主键策略
- 索引说明

### 6.5 生成工具类

指令格式：
创建某工具类，包含以下要求：
- 类名说明
- 方法列表及功能说明
- 是否单例模式
- 线程安全要求
