# 情绪日记

基于SpringBoot2+Vue+ElementUI开发的情绪日记，实现了管理员和普通用户的不同功能模块。

## 项目技术栈

### 后端技术栈

- SpringBoot 2.7.5
- Spring Security
- MyBatis-Plus 3.5.2
- MySQL 8.0
- 阿里巴巴Druid连接池
- JWT认证
- JDK 1.8
- Maven

### 前端技术栈

- Vue.js 2.6
- ElementUI 2.15
- Axios
- Vuex
- Vue Router

## 功能模块

### 管理员模块

1. **登录功能**
   - 管理员账号密码登录
   - 登录成功后显示欢迎信息和系统菜单

2. **用户管理**
   - 实现用户信息的CRUD操作
   - 支持按用户名、手机号等字段进行模糊查询
   - 用户头像上传与显示功能

3. **日志管理**
   - 记录系统操作日志（包括操作人、操作时间、操作内容）
   - 支持日志查看功能，分页展示
   - 支持日志删除功能

4. **个人信息管理**
   - 管理员可修改个人基本信息
   - 可修改登录密码

5. **公告管理**
   - 实现公告信息的CRUD操作
   - 支持公告发布、撤回、置顶等操作

### 普通用户模块

1. **注册功能**
   - 用户可通过邮箱/手机号注册账号
   - 注册时需设置密码，密码需符合强度要求

2. **个人信息管理**
   - 用户可修改个人基本信息
   - 可修改登录密码
   - 可上传/修改个人头像

3. **公告查看**
   - 查看系统发布的公告信息
   - 支持公告详情查看

## 数据库设计

系统包含三张核心表：

1. **用户表(ums_user)**
   - 记录用户基本信息

2. **操作日志表(sys_operation_log)**
   - 记录系统操作日志

3. **公告表(sys_notice)**
   - 记录公告信息

## 项目运行

### 方法一：使用启动脚本（推荐）

#### Windows 用户
```bash
# 双击运行startup.bat文件
startup.bat
```

#### Linux/Mac 用户
```bash
# 赋予执行权限
chmod +x startup.sh

# 运行启动脚本
./startup.sh
```

### 方法二：手动运行

#### 后端运行

1. 创建数据库
   ```sql
   CREATE DATABASE user_management;
   ```

2. 执行SQL脚本
   ```bash
   mysql -u root -p user_management < src/main/resources/sql/init.sql
   ```

3. 修改配置
   - 修改`application.yml`中的数据库连接信息

4. 启动项目
   ```bash
   mvn spring-boot:run
   ```

#### 前端运行

1. 进入前端目录
   ```bash
   cd src/main/resources/frontend
   ```

2. 安装依赖
   ```bash
   npm install
   ```

3. 启动开发服务器
   ```bash
   npm run serve
   ```

### 方法三：使用Docker部署

#### 前提条件
- 安装Docker和Docker Compose

#### 使用Docker运行
```bash
# 构建并启动容器
docker-compose up -d

# 查看运行状态
docker-compose ps

# 查看日志
docker-compose logs -f
```

## 访问系统

- 前端地址：http://localhost:8080
- 后端API地址：http://localhost:8080/api

## 默认账号密码

- 管理员账号：admin / admin123
- 示例用户：注册后使用

## 生产环境部署

对于生产环境，请确保：

1. 修改默认密码和JWT密钥
2. 配置HTTPS
3. 调整数据库连接池参数
4. 配置适当的日志级别

可以通过环境变量覆盖配置：
```
SPRING_DATASOURCE_URL=jdbc:mysql://your-mysql-server:3306/user_management
SPRING_DATASOURCE_USERNAME=production_user
SPRING_DATASOURCE_PASSWORD=strong_password
PASSWORD_SALT=your_custom_salt
JWT_SECRET=your_custom_jwt_secret
```

## 注意事项

1. 确保MySQL版本为8.0或以上
2. 确保JDK版本为1.8
3. 所有图片存储在static/images目录下 