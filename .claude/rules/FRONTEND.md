---
paths:
  - "frontend/**/*.ts"
  - "frontend/**/*.vue"
  - "frontend/**/*.js"
  - "frontend/**/*.json"
---
# 前端研发规范
前端工程从技术栈选型、页面风格细节、工程结构三个方面进行规范。

## 技术栈选型规范（根据需求自主选择）
1. 框架：Vue 3（组合式API，优先使用<script setup lang="ts">语法糖）
2. 语言：TypeScript
3. 构建工具：Vite
4. CSS解决方案：Tailwind LESS/Scoped CSS/Element Plus
5. 状态管理：Pinia (状态树/src/store/index.ts，定义全局状态如userInfo、token等)
6. 页面路由：vue-router (路由入口/src/router/index.ts，动态导入具体页面)
7. 组件库：Element Plus
8. 接口请求：axios
   - 封装axios实例 /src/api/index.ts，包含loading状态、异常处理控制; 
   - 根据业务类型定义请求/src/api/xxx.ts,使用封装好的axios实例，请求数据，如getList、getDetail等具体请求
9. 代码规范：
   - 遵循ESLint + Prettier规范，变量命名使用小驼峰，组件命名使用PascalCase
   - 组件结构：<template>（语义化标签）→ <script setup lang="ts">（逻辑）→ <style scoped>（样式）
   - 禁止使用var，优先使用const/let；避免冗余代码，提取可复用逻辑为hooks或工具函数
   - 样式单位统一使用rem/vw，适配[移动端/PC端]，设计稿基准宽度为[750px/1920px]
10. 性能要求：
   - 图片使用懒加载，样式避免深层嵌套（CSS嵌套不超过3层）
   - 非必要不引入全局样式，组件样式作用域隔离

## 风格细节规范
1. 主题风格
   - 颜色: 
     - 主色: #1890FF (Element Plus默认)
     - 次色: #409EFF (Element Plus默认)
     - 成功色: #67C23A (Element Plus默认)
     - 警告色: #E6A23C (Element Plus默认)
     - 错误色: #F56C6C (Element Plus默认)
   - 字体:
     - 型号: 正文(PingFangSC-Regular) 加粗(PingFangSC-Semibold) 标题(PingFangSC-Medium)
     - 大小: 正文(14px) 突出(18px) 标题(22px)
     - 粗细: normal(400)、medium(500)、bold(800)
   - 间距: 
      - xl(16px)
      - l(12px)
      - m(8px)
      - s(4px)
   - 圆角:
      - base(4px)
      - container(8px)
   - 阴影: 
     - m(0 2px 4px rgba(0, 0, 0, 0.1))
     - xl(0 4px 8px rgba(0, 0, 0, 0.15))
2. 交互规范
   - 点击: 鼠标样式为pointer，可点击
   - 录入: 长度限制50字符、判断是否必填项校验
   - 禁用: 鼠标样式为not-allowed，不可点击
   - 加载中: 添加loading效果
   - 错误处理: 调用Message 消息提示组件，显示错误提示（如：message.error）
   - 成功处理: 调用Message 消息提示组件，显示成功提示（如：message.success）
   - 删除\移除\危险行为: 调用confirm-dialog组件，确认后执行删除操作

## 工程结构输出规范
1. 代码结构
   ```bash
   src/
   ├── api/                # 接口请求配置
   │   ├── index.ts        # axios实例初始化、请求拦截、异常处理
   │   ├── goods.ts        # 商品相关接口（如：/goods/list）
   │   └── user.ts         # 用户相关接口
   ├── assets/             # 静态资源
   │   ├── images/         # 图片文件
   │   └── styles/         # 全局样式（如：variables.scss, main.css）
   ├── components/         # 公用业务组件（非页面级）
   │   ├── Header.vue      # 公共头部
   │   ├── NavMenu.vue     # 导航菜单
   │   └── Common/         # 更通用的原子组件
   ├── constants/          # 常量定义
   │   ├── routes.ts       # 路由路径常量
   │   └── apiUrls.ts      # 接口 URL 常量
   ├── router/             # 路由配置
   │   └── index.ts        # 路由入口（包含 /goods/list 等配置）
   ├── store/              # 状态管理（Pinia / Vuex）
   │   ├── index.ts        # Store 入口
   │   └── modules/
   │       └── userInfo.ts # 用户信息状态
   ├── utils/              # 工具函数
   │   ├── validate.ts     # 格式校验函数（正则等）
   │   └── request.ts      # Axios 拦截器封装
   ├── views/              # 页面组件（与路由对应）
   │   ├── goods/
   │   │   └── GoodsList.vue # 商品列表页
   │   └── login/
   │       └── Login.vue
   ├── App.vue             # 根组件
   └── main.ts             # 入口文件（Vue 实例、Element Plus 引入、路由挂载）
   ```
2. 输出内容：
   - 完整的.vue文件代码（包含template、script setup、style scoped）
   - 必要的注释（如组件功能、核心逻辑、参数说明）
   - 依赖说明（如需要安装的npm包：npm install element-plus）
   - 运行说明（如：npm run dev即可启动项目）
3. 额外要求：
   - 代码无语法错误，可直接复制到Vue3+Vite项目中运行
   - 样式1:1还原UI设计稿，无错位、漏样式问题
   - 优先使用原生Vue3特性，避免过度封装