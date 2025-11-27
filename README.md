# S3 云管理器 - 对象存储文件管理系统

> 基于 AWS S3 协议的现代化对象存储文件管理系统

[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.4.8-brightgreen.svg)](https://spring.io/projects/spring-boot)
[![Vue.js](https://img.shields.io/badge/Vue.js-3.x-brightgreen.svg)](https://vuejs.org/)
[![Java](https://img.shields.io/badge/Java-17-orange.svg)](https://www.oracle.com/java/)

## 📖 项目简介

这是一个简洁易用的S3对象存储文件管理系统，提供现代化的Web界面，支持所有兼容S3协议的对象存储服务。

### ✨ 核心特性

- 🎨 **现代化UI** - Vue 3 + Tailwind CSS，支持暗色模式
- 📁 **完整文件管理** - 上传、下载、删除、搜索、创建文件夹
- 🚀 **即开即用** - 无需构建工具，CDN直接加载
- 📊 **智能分页** - 默认每页1000条，支持S3原生分页
- 🔄 **多存储桶管理** - 轻松切换不同的存储桶
- 🔍 **实时搜索** - 快速过滤文件和文件夹
- 📈 **上传进度** - 实时显示上传进度和速度
- 🧭 **面包屑导航** - 快速返回上级目录
- 🌓 **暗色模式** - 完整支持暗色主题
- 🎯 **双视图模式** - 列表视图 / 网格视图切换

---

## 🚀 快速开始

### 环境要求

- JDK 17+
- Maven 3.6+
- 浏览器（Chrome、Firefox、Edge等现代浏览器）

### 3步快速启动

#### 步骤1: 启动后端

**Windows:**
```bash
start.bat
```

**Linux/Mac:**
```bash
./start.sh
```

**或手动启动:**
```bash
mvn spring-boot:run -Dspring-boot.run.profiles=storage
```

#### 步骤2: 打开浏览器

访问：**http://localhost:8081/s3-manager.html**

#### 步骤3: 开始使用

- 左侧选择存储桶
- 浏览文件
- 右下角上传文件
- 享受使用！

详细使用说明请查看 **[快速启动文档](START-VUE.md)**

---

## 📸 界面预览

```
┌─────────────────────────────────────────────────────┐
│  ☁ S3 云管理器                            🌓 主题   │
├──────────┬──────────────────────────────────────────┤
│ 📁 文件管理│  🏠 根目录 / folder1 / ...              │
│ ⚙ 配置设置 │  🔍 [搜索...]    📋 列表  🎨 网格       │
│          │────────────────────────────────────────  │
│ 存储桶:   │  📂 文件夹1        500KB   2025-11-25   │
│ ✓ bucket1 │  📂 文件夹2        2.5MB   2025-11-24   │
│   bucket2 │  📄 文件.pdf      10.2MB   2025-11-23   │
│   bucket3 │  🖼 图片.jpg       1.5MB   2025-11-22   │
│          │                                    ↓ ⬇ 🗑│
│          │                                          │
│          │                      🔵 上传  ⚪ 新建    │
└──────────┴──────────────────────────────────────────┘
```

---

## 📋 核心功能

| 功能 | 状态 | 说明 |
|------|------|------|
| 存储桶切换 | ✅ | 左侧列表快速切换，LocalStorage持久化 |
| 文件浏览 | ✅ | 列表/网格视图，文件夹自动置顶 |
| 文件上传 | ✅ | 多选上传，实时进度条 |
| 文件下载 | ✅ | 单击即可下载 |
| 文件删除 | ✅ | 带二次确认 |
| 创建文件夹 | ✅ | 支持多级目录 |
| 文件搜索 | ✅ | 实时过滤，高亮显示 |
| 面包屑导航 | ✅ | 快速跳转任意层级 |
| 暗色模式 | ✅ | 完整主题切换支持 |
| 文件详情 | ✅ | 右侧抽屉显示详细信息 |

---

## 🔧 技术架构

### 后端

- **Spring Boot 3.4.8** - 应用框架
- **AWS SDK v2 (2.28.16)** - S3客户端
- **MyBatis-Plus 3.5.9** - 数据访问
- **Java 17** - 编程语言

### 前端

- **Vue 3** - 渐进式框架（CDN方式）
- **Tailwind CSS 3.x** - 实用CSS框架（CDN）
- **Material Icons & Symbols** - Google图标库
- **Axios** - HTTP客户端

### 文件位置

```
src/main/resources/static/
├── s3-manager.html    ← 主页面（推荐使用）
└── s3-manager.js      ← Vue 3 应用逻辑
```

### API接口

| 接口 | 方法 | 说明 |
|------|------|------|
| `/api/storage/buckets` | GET | 获取存储桶列表 |
| `/api/storage/files/list` | POST | 获取文件列表（支持分页） |
| `/api/storage/upload` | POST | 上传文件（带进度） |
| `/api/storage/download` | GET | 下载文件 |
| `/api/storage/files` | DELETE | 删除文件 |
| `/api/storage/folder` | POST | 创建文件夹 |
| `/api/storage/search` | GET | 搜索文件 |

---

## 🔐 S3兼容性

支持所有兼容S3协议的对象存储服务：

- ✅ AWS S3
- ✅ MinIO
- ✅ 阿里云 OSS
- ✅ 腾讯云 COS
- ✅ 华为云 OBS
- ✅ Cloudflare R2
- ✅ 自建S3服务

### 配置示例

编辑 `src/main/resources/application-storage.yml`：

```yaml
storage:
  default-backend: minio
  backends:
    minio:
      name: MinIO本地存储
      type: S3
      endpoint: http://localhost:9000
      access-key-id: minioadmin
      access-key-secret: minioadmin
      region: us-east-1
      default-bucket: test-bucket
      enabled: true
```

---

## ⚙️ 配置说明

### 修改端口

```yaml
server:
  port: 8081  # 修改为你想要的端口
```

### 修改文件大小限制

```yaml
storage:
  upload:
    max-file-size: 104857600  # 100MB

spring:
  servlet:
    multipart:
      max-file-size: 100MB
      max-request-size: 100MB
```

### 修改分页大小

在 `s3-manager.js` 中修改：

```javascript
const response = await axios.post('/api/storage/files/list', {
    bucketName: currentBucket.value,
    prefix: currentPath.value,
    delimiter: '/',
    pageSize: 1000  // 改为你想要的值
});
```

---

## 🎨 自定义样式

### 修改主题色

在 `s3-manager.html` 中找到 Tailwind 配置：

```javascript
tailwind.config = {
    theme: {
        extend: {
            colors: {
                primary: {
                    500: '#3b82f6',  // 改为你的颜色
                    600: '#2563eb',
                }
            }
        }
    }
}
```

### 修改布局

```html
<!-- 修改侧边栏宽度 -->
<aside class="w-64">  <!-- 改成 w-72 变宽 -->

<!-- 修改网格列数 -->
<div class="grid-cols-5">  <!-- 改成 grid-cols-6 显示更多列 -->
```

---

## 🐛 常见问题

### 端口被占用

修改 `application-storage.yml` 中的 `server.port`

### 无法连接S3

1. 检查 endpoint 配置是否正确
2. 检查 access-key 和 secret-key
3. 检查网络连接
4. 查看后端日志

### 上传失败

1. 检查文件大小是否超过限制（默认100MB）
2. 检查文件类型是否被允许
3. 查看浏览器控制台错误
4. 检查S3权限

### 图标不显示

已同时加载Material Icons和Material Symbols，至少一个能用。如果都不显示：
1. 检查网络连接
2. 检查是否能访问Google Fonts CDN
3. 查看浏览器控制台

### 页面空白

1. 检查浏览器控制台错误
2. 确认后端API正常运行
3. 清除浏览器缓存
4. 尝试无痕模式

更多问题请查看 **[Vue 3 使用指南](VUE3-GUIDE.md)**

---

## 📁 项目结构

```
one-agent-4j-storage/
├── src/main/
│   ├── java/                        # Java源码
│   │   └── com/all/in/one/agent/storage/
│   │       ├── controller/          # API控制器
│   │       ├── service/             # 业务逻辑
│   │       ├── mapper/              # 数据访问
│   │       └── util/                # 工具类
│   └── resources/
│       ├── static/                  # 前端资源
│       │   ├── s3-manager.html      # Vue 3 主页面 ⭐
│       │   └── s3-manager.js        # Vue 3 应用逻辑 ⭐
│       ├── application-storage.yml  # 配置文件
│       └── init/                    # 数据库初始化脚本
├── VUE3-GUIDE.md                    # Vue 3 详细使用指南 ⭐
├── START-VUE.md                     # Vue 3 快速启动文档 ⭐
├── FEATURE-CHECKLIST.md             # 功能清单
├── ICON-FIX-GUIDE.md                # 图标问题解决指南
├── README.md                        # 项目说明（本文件）
├── start.bat                        # Windows启动脚本
└── pom.xml                          # Maven配置
```

---

## 🆚 为什么选择Vue 3版本？

### 优势

1. **无需构建** - 修改代码即刻生效，F5刷新即可
2. **启动快速** - 1秒启动，无需npm install
3. **简单直接** - 2个文件即可运行
4. **学习曲线低** - 容易理解和修改
5. **部署简单** - 直接放到static目录

### 适用场景

- ✅ 快速原型开发
- ✅ 小型项目
- ✅ 个人使用
- ✅ 不想配置构建工具
- ✅ 需要快速迭代

---

## 📝 版本历史

### v3.0.0 (2025-11-25) - Vue 3 CDN版本

#### 🎉 重大更新
- 采用Vue 3 + Tailwind CSS（CDN方式）
- 无需构建工具，即开即用
- 完整的暗色模式支持

#### ✨ 新增功能
- 列表/网格双视图模式
- 上传进度面板（实时显示）
- Toast通知系统
- 文件详情抽屉
- 搜索高亮
- 悬浮操作按钮
- LocalStorage状态持久化

#### 🔧 技术优化
- S3原生分页（不再内存分页）
- 文件按修改时间倒序排序
- 文件夹自动置顶
- Material Icons + Material Symbols双重支持
- 响应式设计优化

---

## 🤝 开发指南

### 实时修改，无需重启

```bash
# 1. 打开文件
notepad src\main\resources\static\s3-manager.js

# 2. 修改代码

# 3. 刷新浏览器 (F5) - 立即看到效果！
```

### 添加新功能

参考 **[Vue 3 使用指南](VUE3-GUIDE.md)** 中的详细示例。

### 调试

打开浏览器控制台（F12）查看：
- Network 标签 - 查看API请求
- Console 标签 - 查看JavaScript日志
- Vue DevTools - 查看Vue组件状态

---

## 📚 文档索引

- **[START-VUE.md](START-VUE.md)** - 快速启动指南（3步搞定）
- **[VUE3-GUIDE.md](VUE3-GUIDE.md)** - 详细使用指南和开发文档
- **[FEATURE-CHECKLIST.md](FEATURE-CHECKLIST.md)** - 功能清单对照表
- **[ICON-FIX-GUIDE.md](ICON-FIX-GUIDE.md)** - 图标问题解决方案
- **[CLAUDE.md](CLAUDE.md)** - 项目架构和开发规范（给AI看的）

---

## 🎯 后续计划

### P0 - 核心功能（需后端支持）

- [ ] 文件预览（图片/PDF/文本）
- [ ] 文件重命名
- [ ] 文件移动
- [ ] 配置管理页面

### P1 - 增强功能

- [ ] 复制分享链接
- [ ] 批量操作（多选）
- [ ] 拖拽上传
- [ ] 排序UI控制

### P2 - 体验优化

- [ ] 文件上传速度显示
- [ ] 剩余时间预估
- [ ] 快捷键支持
- [ ] 更多文件类型图标

---

## 📞 技术支持

遇到问题？请查看：
1. 浏览器控制台错误信息（F12）
2. 后端日志
3. [VUE3-GUIDE.md](VUE3-GUIDE.md) 中的常见问题部分

---

## 📄 License

MIT License

---

**享受使用S3云管理器！** 🎉

现在就开始：

```bash
start.bat
```

然后访问：**http://localhost:8081/s3-manager.html**
