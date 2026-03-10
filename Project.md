## 角色
你是一名系统架构师

## 任务列表
1. 读取本文件夹下XXX文件，根据文件内容，完成系统的需求分析。
2. 根据需求分析,完成系统数据库表结构的设计和创建,完成系统的前端工程及后端工程的研发和启动。
3. 工程目录分为前端(frontend)，后端(backend)。
4. 前端架构需要满足前端规范
5. 后端架构需要满足后端规范

## 前端规范
### 技术栈选型
1. 框架:React 18+
2. 语言:TypeScript
3. 构建工具:Vite
4. CSS解决方案:Tailwind Less/Scoped
5. 状态管理:React Context API (状态树/src/context/index.ts，定义全局状态，如:userInfo、token等)
6. 页面路由:React Router DOM
7. 组件库:Antd-design
8. 接口请求:Axios
    - 封装axios实例 /src/services/index.ts，包含loading状态、异常处理控制; 
    - 根据业务类型定义请求/src/services/xxx.ts,使用封装好的axios实例，请求数据，如getList、getDetail等具体请求
9. 代码规范:
    - 遵循ESLint + Prettier规范，变量命名使用小驼峰，组件命名使用PascalCase
    - 禁止使用var，优先使用const/let；避免冗余代码，提取可复用逻辑为hooks或工具函数
    - 样式单位统一使用rem/vw，适配[移动端/PC端]，设计稿基准宽度为[750px/1920px]
    10. 性能要求:
    - 图片使用懒加载，样式避免深层嵌套（CSS嵌套不超过3层）
    - 非必要不引入全局样式，组件样式作用域隔离

### 样式交互风格
1. 主题风格
   - 颜色: 主色: #1890FF; 中性色: #F5F5F5; 成功: #52C41A; 出错: #FF4D4F; 失败: #FF4D4F; 提醒: #FAAD14
   - 字体: 字体: 平方字体 大小: 14px 颜色: #333333
   - 间距: 大:12px 中: 8px 小: 4px
   - 圆角:
   - 阴影:
2. 交互规范
   - 点击:
   - 禁用:
   - 加载中:
   - 错误处理:
   - 成功处理:
   - 删除\移除\危险行为:

### 输出结构规范
1. 代码结构、目录规范
   ```bash
   src/
   ├── assets/             # 静态资源（图片、全局字体、SVG 等）
   ├── components/         # 全局共享的通用 UI 组件（Button, Input, Modal）
   │   └── Button/
   │       ├── Button.tsx
   │       ├── Button.module.css
   │       └── index.ts    # 导出入口，方便 import { Button } from '@/components'
   ├── config/             # 全局配置（API Endpoints, 常量, 枚举）
   ├── features/           # 核心业务逻辑（按功能模块划分）⭐ 推荐做法
   │   ├── auth/           # 登录注册相关
   │   │   ├── components/ # 仅限 auth 使用的组件
   │   │   ├── hooks/      # auth 专用 hooks
   │   │   ├── services/   # auth 相关 API 请求
   │   │   └── types.ts    # 类型定义
   │   └── dashboard/      # 仪表盘相关
   ├── hooks/              # 全局复用的自定义 Hooks（如 useDebounce, useLocalStorage）
   ├── layouts/            # 页面布局组件（MainLayout, AdminLayout）
   ├── pages/              # 路由页面（通常只负责拼装 features 中的组件）
   ├── services/           # 全局 API 客户端配置（Axios 实例、拦截器）
   ├── store/              # 状态管理（Redux slices, Zustand stores）
   ├── types/              # 全局通用 TypeScript 类型定义
   └── utils/              # 纯工具函数（格式化日期、校验等）
   ```
2. 输出内容:
   - 完整的.tsx文件代码（包含交互逻辑、render）
   - 必要的注释（如组件功能、核心逻辑、参数说明）
   - 依赖说明（如需要安装的npm包:npm install antd-design）
   - 运行说明（如:npm run dev即可启动项目）
3. 额外要求:
   - 代码无语法错误，可直接复制到React项目中运行
   - 样式1:1还原UI设计稿，无错位、漏样式问题
   - 优先使用原生Vue3特性，避免过度封装

## 后端规范
### 技术栈选型
1. 框架: Spring Boot 3+
2. 语言: Java 17
3. 数据库: MySQL 8.0+ (user: root password: Root@123456)
4. 数据库连接池: MyBatis、MyBatis-Plus
5. 接口文档: Swagger 2.0
6. 构建工具: Maven
7. 部署环境: Docker
8. 服务注册与发现: Nacos 2.2.3
9. 消息队列: Kafka 2.8.1

### 输出结构规范
1. 核心目录结构
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

2. 资源文件结构 (src/main/resources)
resources/
├── mapper/                # MyBatis XML 映射文件
├── application.yml        # 主配置文件 (包括 Nacos 连接地址)
├── application-dev.yml    # 开发环境配置 (MySQL: root/Root@123456)
├── application-prod.yml   # 生产环境配置
└── logback-spring.xml     # 日志配置