---
name: springboot4-ddd-standard-scaffold
description: 基于 Spring Boot 4.0.1 + JDK 17 + Maven 多模块生成后端标准脚手架（dao/facade/web），整合 MyBatis-Plus、fastjson2、Lombok、Apache Commons 与默认 MySQL，并按 DDD 约束组织代码，且 HTTP API 默认统一使用 POST；当用户要求搭建或完善 SpringBoot4 后端标准框架、多模块项目、统一父 POM 依赖管理或统一接口封装规范时使用。
---

# 目标

输出一个可直接开发的 Spring Boot 4 标准后端框架，默认满足以下硬性约束：

- 使用 `Spring Boot 4.0.1`
- 使用 `JDK 17`
- 使用 `MyBatis-Plus`
- 使用 Maven 多模块，包含 `dao`、`facade`、`web`
- `web` 模块包含配置、控制器、异常处理、拦截器、service（业务编排）
- 严格执行 DDD 分层边界
- 基础组件包含 `fastjson2`、`lombok`、`commons-lang3`、`commons-collections4`
- 未指定数据库时默认 `MySQL`
- HTTP API 默认统一使用 `POST`
- Java 基础包名必须由用户明确提供
- `groupId` 优先基于用户确认后的包名确定
- 父 `pom.xml` 统一管理版本、插件和打包策略

# 执行流程

1. 收集最小上下文

- 获取 `groupId`、`artifactId`、`base package`、服务名。
- `base package` 为必填项。触发本 Skill 后，如果用户没有明确给出包名，必须先询问用户，例如：`请提供项目基础包名，例如 com.company.project`
- 禁止根据 `groupId`、`artifactId` 自动推导 `base package`
- 在 `base package` 未确认前，禁止继续输出父 `pom.xml`、模块结构和代码骨架
- 若用户未单独指定 `groupId`，默认令 `groupId = base package`
- 若用户单独指定了 `groupId`，仍需先确认 `base package`，再继续生成项目
- 未提供时使用默认值：
  - `artifactId`: `demo-backend`

2. 建立 Maven 多模块骨架

- 根目录创建父工程（`packaging=pom`）。
- 强制包含三大模块：
  - `dao`：领域模型与持久化抽象
  - `facade`：对外契约（接口、请求/响应模型、防腐层）
  - `web`：启动与接入层（controller、service、配置、异常、拦截器）

3. 按 DDD 约束组织目录

- `dao` 模块建议包结构：
  - `domain/entity`
  - `domain/vo`
  - `domain/bo`
  - `domain/dto`
  - `domain/repository`（仓储接口）
  - `infrastructure/mapper`（MyBatis-Plus Mapper）
  - `infrastructure/repository`（仓储实现）
  - `infrastructure/convertor`
- `facade` 模块建议包结构：
  - `api`（Facade 接口）
  - `model/request`
  - `model/response`
  - `assembler`
- `web` 模块建议包结构：
  - `bootstrap`（启动类）
  - `controller`
  - `service`
  - `config`
  - `exception`
  - `interceptor`
  - `common`（统一返回体、错误码、上下文）

4. 固化依赖与版本管理 

- 在父 POM 的 `dependencyManagement` 统一管理：
  - `spring-boot-dependencies:4.0.1`
  - `mybatis-plus` 相关版本（选择与 Boot 4 兼容的稳定版）
  - `fastjson2`
  - `lombok`
  - `commons-lang3`
  - `commons-collections4`
  - `mysql-connector-j`
- 在父 POM 的 `properties` 固化：
  - `java.version=17`
  - `maven.compiler.release=17`
- 在父 POM 的 `pluginManagement` 统一管理：
  - `maven-compiler-plugin`
  - `maven-surefire-plugin`
  - `spring-boot-maven-plugin`（只在 web 启动模块执行 repackage）

5. 落地 web 层基础能力

- 提供全局异常处理（`@RestControllerAdvice`）。
- 提供拦截器与统一注册（`WebMvcConfigurer`）。
- 提供统一响应模型（如 `ApiResponse<T>`）。
- 控制器接口统一使用 `@PostMapping`，请求参数优先使用 `@RequestBody`
- 配置 JSON 序列化（优先 fastjson2）。
- 配置时间处理策略：
  - 统一时区（例如 `Asia/Shanghai`，可配置化）
  - 统一日期时间格式（`yyyy-MM-dd HH:mm:ss`）

6. 落地 MyBatis-Plus 与 MySQL 默认配置

- 默认 `datasource` 使用 MySQL：
  - 驱动：`com.mysql.cj.jdbc.Driver`
  - URL：`jdbc:mysql://127.0.0.1:3306/${db}?useUnicode=true&characterEncoding=utf8&serverTimezone=Asia/Shanghai&useSSL=false&allowPublicKeyRetrieval=true`
- 添加 MyBatis-Plus 常用配置：
  - `mapperLocations`
  - 驼峰映射
  - 逻辑删除（如有要求）
  - 分页拦截器

# 依赖与模块规则

1. 模块依赖方向

- `web -> facade -> dao`
- `web -> dao` 仅允许在应用服务确有需要且不破坏边界时使用
- 禁止 `dao` 反向依赖 `web` 或 `facade`

2. 分层职责约束

- `controller` 仅做参数校验、协议转换、调用 service。
- `service` 负责业务编排与事务边界，不直接暴露数据库细节。
- `repository` 屏蔽 MyBatis-Plus 细节，领域侧只依赖仓储接口。
- `entity/vo/bo/dto` 放在 `dao` 统一管理并明确语义：
  - `entity`：领域实体
  - `vo`：值对象
  - `bo`：业务对象（流程编排上下文）
  - `dto`：跨层传输对象（避免与 facade request/response 混用）

3. 组件使用约束

- `fastjson2`：作为默认 JSON 处理组件。
- `lombok`：用于样板代码简化（`@Getter/@Setter/@Builder` 等）。
- `commons-lang3`：字符串、对象判空等工具。
- `commons-collections4`：集合判空、转换等工具。

4. API 设计约束

- HTTP 接口统一使用 `POST`，不默认生成 `GET`、`PUT`、`DELETE`、`PATCH`。
- 查询、详情、分页、创建、修改、删除都按 `POST` 设计。
- 控制器方法统一使用 `@PostMapping`。
- 请求对象统一放在 `facade/model/request` 或 `dao/domain/dto`，并通过 `@RequestBody` 接收。
- 返回对象统一使用 `ApiResponse<T>` 包装。
- URI 命名采用动作式或业务语义式，例如：
  - `/user/create`
  - `/user/update`
  - `/user/delete`
  - `/user/query`
  - `/user/page`
- 只有用户明确要求健康检查、文件下载、回调验签等特殊接口时，才允许偏离统一 `POST` 规则。

# 父 POM 最小模板（示意）

```xml
<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>${groupId}</groupId>
  <artifactId>${artifactId}</artifactId>
  <version>1.0.0-SNAPSHOT</version>
  <packaging>pom</packaging>

  <properties>
    <java.version>17</java.version>
    <maven.compiler.release>17</maven.compiler.release>
    <spring-boot.version>4.0.1</spring-boot.version>
    <mybatis-plus.version>${compatible.version}</mybatis-plus.version>
    <fastjson2.version>${compatible.version}</fastjson2.version>
  </properties>

  <modules>
    <module>dao</module>
    <module>facade</module>
    <module>web</module>
  </modules>

  <dependencyManagement>
    <dependencies>
      <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-dependencies</artifactId>
        <version>${spring-boot.version}</version>
        <type>pom</type>
        <scope>import</scope>
      </dependency>
    </dependencies>
  </dependencyManagement>
</project>
```

# 交付内容要求

每次执行本 Skill，至少产出以下内容：

- 若用户未提供包名，先询问包名；包名未确认前，不输出父 `pom.xml` 和项目骨架
- 完整模块目录树（dao/facade/web）
- 父 `pom.xml`（含版本管理、插件管理、modules）
- 各模块子 `pom.xml`
- 启动类、示例 controller、service、异常处理、拦截器
- 示例 controller 必须使用 `@PostMapping`
- MyBatis-Plus 配置类与示例 mapper/repository
- `application.yml`（默认 MySQL + 时间配置）

# 自检清单

输出前必须逐项核对：

- 是否明确 `Spring Boot 4.0.1` 与 `JDK 17`
- 是否包含 `MyBatis-Plus`
- 是否为 Maven 多模块且包含 `dao/facade/web`
- 是否体现 DDD 职责边界与依赖方向
- 是否集成 `fastjson2`、`lombok`、`commons-lang3`、`commons-collections4`
- 未指定数据库时是否默认 MySQL
- 是否所有默认 HTTP API 都使用 `POST`
- 是否控制器示例统一使用 `@PostMapping + @RequestBody`
- 是否已主动询问并确认用户的 `base package`
- `groupId` 是否已使用用户确认后的 `base package` 或用户明确指定值
- 在 `base package` 未确认前，是否停止输出父 `pom.xml` 与项目骨架
- 父 POM 是否集中管理依赖版本与插件
