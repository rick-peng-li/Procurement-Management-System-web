<!-- 项目 Git 地址：git@github.com:rick-peng-li/Procurement-Management-System-web.git -->

# Procurement-Management-System-web

采购管理系统 Web 项目，面向采购业务中的多角色协同场景，覆盖站点经理、采购员工、供应商等核心角色的日常操作流程。仓库当前包含 Web 前端、Node.js 后端，以及一套基于 Expo 的移动端代码。

## 项目简介

该项目围绕采购业务流程进行设计，支持从用户登录、站点管理、商品管理，到草稿订单、订单审批、收货与发票管理等一系列业务功能。

核心业务模块包括：

- 用户与角色管理：站点经理、员工、供应商登录与注册
- 站点管理：站点创建、列表查询、编辑维护
- 商品管理：供应商商品维护、站点经理/员工查看商品
- 订单管理：草稿订单、待审批订单、供应商接单/拒单、订单详情查看
- 收货管理：已下单收货、收货记录管理
- 发票管理：发票创建、发票列表与订单关联

## 仓库结构

```text
Procurement-Management-System-web/
├─ backend/    # Express + MongoDB 后端接口服务
├─ frontend/   # React Web 前端
├─ mobileapp/  # React Native / Expo 移动端
└─ README.md
```

## 架构与技术栈

### 1. 前端（frontend）

- React 17
- React Router DOM 5
- Redux + Redux Thunk
- Axios
- Bootstrap / Material UI / Semantic UI
- Create React App 构建体系

前端采用典型的按职责分层方式组织代码：

- `src/actions`：封装异步请求与业务动作
- `src/constants`：统一维护 action 常量
- `src/reducers`：状态管理与数据更新
- `src/screens`：页面级功能模块
- `src/components`：通用组件

### 2. 后端（backend）

- Node.js
- Express
- MongoDB
- Mongoose
- JWT
- Jest

后端采用常见的接口分层结构：

- `routes`：接口路由定义
- `controllers`：业务处理逻辑
- `models`：MongoDB 数据模型
- `middleware`：鉴权、中间件与异常处理
- `config`：数据库连接等配置
- `utils`：辅助工具

当前接口入口位于 `backend/server.js`，默认监听端口为 `5000`。

### 3. 移动端（mobileapp）

- React Native
- Expo
- React Navigation
- Axios

移动端主要用于订单相关业务的移动化操作，作为仓库中的扩展端存在。

## 运行环境

建议使用以下环境：

- Node.js 14 及以上
- npm 6 及以上
- MongoDB 实例

后端依赖环境变量：

- `MONGO_URI`：MongoDB 连接地址
- `PORT`：后端端口，可选，默认 `5000`

前端开发代理已配置为：

- `http://127.0.0.1:5000`

## 启动方式

### 1. 启动后端

在 `backend` 目录安装依赖并启动服务：

```bash
cd backend
npm install
npx nodemon server.js
```

如果不需要热更新，也可以使用：

```bash
cd backend
npm install
node server.js
```

### 2. 启动前端

在 `frontend` 目录安装依赖并启动开发环境：

```bash
cd frontend
npm install
npm start
```

启动成功后，浏览器默认访问：

- 前端地址：`http://localhost:3000`
- 后端地址：`http://localhost:5000`

### 3. 启动移动端（可选）

如果需要运行移动端：

```bash
cd mobileapp
npm install
npm start
```

随后可通过 Expo 在模拟器或真机中调试。

## 开发说明

推荐本地开发顺序：

1. 先准备 MongoDB 连接信息
2. 启动后端服务
3. 再启动前端页面
4. 按角色分别验证业务流程

## 测试与格式化

### 后端测试

```bash
cd backend
npm test
```

### 代码格式化

```bash
cd backend
npm run format
```

```bash
cd frontend
npm run format
```

```bash
cd mobileapp
npm run format
```

## 说明

- 当前仓库以多端协同方式组织，Web 前后端是主要业务实现部分
- 若用于本地联调，请优先保证 MongoDB 与后端接口服务可正常访问
- 如需部署上线，建议分别为前端、后端、数据库配置独立环境变量与部署流程
