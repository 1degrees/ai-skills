---
paths:
  - "backend/**/*.java"
  - "backend/**/*.xml"
  - "backend/**/*.json"
---

# 后端研发规范
后端工程从技术栈选型和工程结构两个方面进行规范。

## 技术栈选型规范（根据需求自主选择）
1. 框架: Spring Boot 3+
2. 语言: Java 17
3. 数据库: MySQL 8.0+ (user: root password: Root@123456)
4. 数据库连接池: MyBatis、MyBatis-Plus
5. 接口文档: Swagger 2.0
6. 构建工具: Maven
7. 部署环境: Docker
8. 服务注册与发现: Nacos 2.2.3
9. 消息队列: Kafka 2.8.1

## 工程结构输出规范
1. 核心目录结构
   ```bash
   src/main/java/com/yourcompany/projectname
   ├── common/                # 公共模块
   │   ├── annotation/        # 自定义注解
   │   ├── config/            # 全局配置（如 Swagger, MyBatisPlusConfig）
   │   ├── constant/          # 常量枚举
   │   ├── exception/         # 异常定义与全局异常处理器
   │   └── result/            # 统一返回结果封装 (R.java)
   ├── controller/            # 接口层 (RESTful API)
   ├── domain/                # 数据模型
   │   ├── dto/               # 前端传输对象 (接收参数)
   │   ├── entity/            # 数据库实体类 (与 MySQL 表对应)
   │   └── vo/                # 视图对象 (返回给前端的数据)
   ├── mapper/                # MyBatis/MyBatis-Plus 持久层接口
   ├── service/               # 业务逻辑接口层
   │   └── impl/              # 业务逻辑实现层
   ├── listener/              # Kafka 消息监听器
   ├── manager/               # 通用业务处理层（可选，处理第三方 SDK 或跨 Service 组合）
   └── utils/                 # 工具类 (Date, String, Encryption)
   ```

2. 资源文件结构 (src/main/resources)
   ```bash
   resources/
   ├── mapper/                # MyBatis XML 映射文件
   ├── application.yml        # 主配置文件 (包括 Nacos 连接地址)
   ├── application-dev.yml    # 开发环境配置 (MySQL: root/Root@123456)
   ├── application-prod.yml   # 生产环境配置
   └── logback-spring.xml     # 日志配置
   ```