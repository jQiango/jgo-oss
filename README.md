# S3 File Nexus

<div align="center">

[![GitHub release](https://img.shields.io/github/release/yourusername/s3-file-nexus.svg)](https://github.com/yourusername/s3-file-nexus/releases)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.4.8-brightgreen.svg)](https://spring.io/projects/spring-boot)
[![Vue.js](https://img.shields.io/badge/Vue.js-3.x-42b883.svg)](https://vuejs.org/)
[![Java](https://img.shields.io/badge/Java-17-orange.svg)](https://www.oracle.com/java/)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

**🚀 Enterprise-grade S3 Object Storage Management System**

A powerful, modern web-based file manager for S3-compatible object storage.
Connect all your cloud storage in one place with a beautiful interface.

**企业级S3对象存储管理系统 - 连接你的所有云存储**

[功能特性](#-核心功能) • [快速开始](#-快速开始) • [技术架构](#-技术架构) • [API文档](#-api-文档) • [配置说明](#-配置说明)

</div>

---

## ✨ 核心功能

### 🎯 文件管理
- ✅ **上传下载** - 多文件上传、实时进度、拖拽上传
- ✅ **文件操作** - 删除、重命名、移动、复制
- ✅ **文件夹管理** - 创建文件夹、文件夹大小计算、层级导航
- ✅ **批量操作** - 多选文件、批量删除、批量下载

### 🔍 搜索与筛选
- ✅ **实时搜索** - 文件名快速搜索、关键词高亮
- ✅ **高级筛选** - 按文件类型、时间范围、大小筛选
- ✅ **智能排序** - 按名称、大小、时间排序

### 👁️ 文件预览
- ✅ **图片预览** - 支持JPG、PNG、GIF、WEBP等格式，带图片压缩
- ✅ **视频播放** - 支持MP4、AVI、MKV等格式，内置播放器
- ✅ **音频播放** - 支持MP3、WAV、OGG等格式，内置播放器
- ✅ **文档预览** - 支持PDF、TXT等文本文档
- ✅ **Markdown渲染** - 支持MD文件渲染，带代码高亮
- ✅ **Office预览** - 支持Word、Excel、PPT在线预览

### 🎨 用户体验
- ✅ **双视图模式** - 列表视图 / 网格视图自由切换
- ✅ **暗色模式** - 完整的深色主题支持
- ✅ **面包屑导航** - 快速跳转任意层级，支持右键菜单
- ✅ **右键菜单** - 文件卡片、面包屑都支持右键操作
- ✅ **拖拽上传** - 支持拖拽文件到页面上传
- ✅ **响应式设计** - 完美支持桌面端和移动端

### 🚀 性能优化
- ✅ **虚拟滚动** - 大量文件列表性能优化
- ✅ **图片懒加载** - 减少初始加载时间
- ✅ **Service Worker** - PWA离线缓存支持
- ✅ **文件缓存** - 智能LRU缓存机制
- ✅ **图片压缩** - 自动压缩预览图片

### 🔗 分享协作
- ✅ **分享链接** - 生成临时分享链接，支持过期时间
- ✅ **预签名URL** - 安全的文件访问链接
- ✅ **权限控制** - 基于配置的访问权限管理

### 📊 统计监控
- ✅ **存储统计** - 文件数量、总大小、类型分布
- ✅ **上传趋势** - 可视化上传趋势分析
- ✅ **缓存监控** - 缓存命中率、使用情况

---

## 🚀 快速开始

### 环境要求

- **JDK 17+** - Java运行环境
- **Maven 3.6+** - 构建工具
- **MySQL 5.7+** - 数据库（可选）
- **现代浏览器** - Chrome、Firefox、Edge等

### 一键启动

#### Windows
```bash
# 方式1: 使用启动脚本
start.bat

# 方式2: 手动启动
mvn spring-boot:run -Dspring-boot.run.profiles=storage
```

#### Linux/Mac
```bash
# 方式1: 使用启动脚本
./start.sh

# 方式2: 手动启动
mvn spring-boot:run -Dspring-boot.run.profiles=storage
```

### 访问应用

启动成功后，在浏览器访问：

- **主界面**: http://localhost:8081/index.html
- **API文档**: http://localhost:8081/doc.html (Swagger)

### 数据库配置（可选）

如需持久化存储配置，请先创建数据库：

```bash
# 1. 创建数据库
mysql -u root -p
CREATE DATABASE one_agent_4j DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

# 2. 导入表结构
mysql -u root -p one_agent_4j < src/main/resources/init/storage.sql

# 3. 修改配置文件
# 编辑 src/main/resources/application-storage.yml
spring:
  datasource:
    url: jdbc:mysql://localhost:3306/one_agent_4j
    username: your_username
    password: your_password
```

---

## 🏗️ 技术架构

### 后端技术栈

| 技术 | 版本 | 说明 |
|------|------|------|
| Spring Boot | 3.4.8 | 应用框架 |
| AWS SDK for Java | 2.28.16 | S3客户端 |
| MyBatis-Plus | 3.5.9 | ORM框架 |
| MySQL | 8.0+ | 数据库 |
| Lombok | 1.18.30 | 简化代码 |
| Hutool | 5.8.25 | 工具库 |

### 前端技术栈

| 技术 | 版本 | 说明 |
|------|------|------|
| Vue.js | 3.x | 渐进式框架（CDN） |
| Tailwind CSS | 3.x | 原子化CSS（CDN） |
| Axios | 1.x | HTTP客户端 |
| Bootstrap Icons | 1.11.3 | 图标库 |
| Marked.js | 11.1.1 | Markdown解析 |
| Highlight.js | 11.9.0 | 代码高亮 |

### 架构设计

```
┌─────────────────────────────────────────────────────────┐
│                      前端层 (Vue 3)                      │
│  ┌──────────┬──────────┬──────────┬──────────────────┐  │
│  │ 文件管理 │ 预览播放 │ 搜索筛选 │ 右键菜单/导航   │  │
│  └──────────┴──────────┴──────────┴──────────────────┘  │
└───────────────────────────┬─────────────────────────────┘
                            │ REST API
┌───────────────────────────▼─────────────────────────────┐
│                    控制器层 (Controller)                 │
│  ┌──────────┬──────────┬──────────┬──────────────────┐  │
│  │ Storage  │  Cache   │  Stats   │  Config          │  │
│  └──────────┴──────────┴──────────┴──────────────────┘  │
└───────────────────────────┬─────────────────────────────┘
                            │
┌───────────────────────────▼─────────────────────────────┐
│                    服务层 (Service)                      │
│  ┌──────────┬──────────┬──────────┬──────────────────┐  │
│  │ Storage  │FileCach  │FilePrevi │ StorageStats     │  │
│  │ Service  │eService  │ewService │ Service          │  │
│  └──────────┴──────────┴──────────┴──────────────────┘  │
└───────────────────────────┬─────────────────────────────┘
                            │
┌───────────────────────────▼─────────────────────────────┐
│                  数据访问层 (Mapper)                     │
│  ┌──────────────────────┬───────────────────────────┐   │
│  │ StorageConfigMapper  │  StorageFileMapper        │   │
│  └──────────────────────┴───────────────────────────┘   │
└───────────────────────────┬─────────────────────────────┘
                            │
┌───────────────────────────▼─────────────────────────────┐
│                    存储层 (Storage)                      │
│  ┌──────────┬──────────┬──────────┬──────────────────┐  │
│  │ AWS S3   │  MinIO   │ 阿里OSS  │  其他S3兼容      │  │
│  └──────────┴──────────┴──────────┴──────────────────┘  │
└─────────────────────────────────────────────────────────┘
```

### 核心组件说明

#### 1. StorageService
核心业务服务，负责所有文件操作：
- 自动创建不存在的存储桶
- 文件名安全校验和清理
- 更新文件访问时间
- 预签名URL生成
- 文件夹对象处理

#### 2. FileCacheService
两层缓存系统：
- **内存缓存** - ConcurrentHashMap存储元数据
- **磁盘缓存** - 本地文件系统存储数据
- **LRU淘汰** - 达到上限时自动清理
- **TTL过期** - 默认5分钟过期
- 线程安全设计

#### 3. S3ClientUtil
动态S3客户端创建工具：
- 支持自定义endpoint（MinIO/OSS兼容）
- 支持路径风格访问（MinIO必需）
- 区域配置
- 凭证注入

#### 4. FileSecurityUtils
文件安全工具：
- 文件类型白名单/黑名单
- 文件名清理防止路径遍历
- MIME类型检测

---

## 📁 项目结构

```
one-agent-4j-storage/
├── src/main/
│   ├── java/com/all/in/one/agent/storage/
│   │   ├── controller/              # REST API控制器
│   │   │   ├── StorageController.java       # 文件操作API
│   │   │   ├── CacheController.java         # 缓存管理API
│   │   │   ├── StorageStatsController.java  # 统计API
│   │   │   └── StorageConfigController.java # 配置管理API
│   │   ├── service/                 # 业务逻辑层
│   │   │   ├── impl/
│   │   │   │   ├── StorageServiceImpl.java      # 存储服务实现
│   │   │   │   ├── FileCacheServiceImpl.java    # 缓存服务实现
│   │   │   │   ├── FilePreviewServiceImpl.java  # 预览服务实现
│   │   │   │   └── StorageStatsServiceImpl.java # 统计服务实现
│   │   │   └── [接口定义]
│   │   ├── mapper/                  # 数据访问层
│   │   │   ├── StorageConfigMapper.java     # 配置CRUD
│   │   │   └── StorageFileMapper.java       # 文件元数据CRUD
│   │   ├── entity/                  # 实体类
│   │   │   ├── StorageConfig.java          # 存储配置实体
│   │   │   └── StorageFile.java            # 文件元数据实体
│   │   ├── util/                    # 工具类
│   │   │   ├── S3ClientUtil.java           # S3客户端工具
│   │   │   └── FileTypeUtils.java          # 文件类型工具
│   │   └── security/                # 安全模块
│   │       └── FileSecurityUtils.java      # 文件安全工具
│   └── resources/
│       ├── static/                  # 前端资源
│       │   ├── index.html              # 主页面 ⭐
│       │   ├── service-worker.js       # PWA Service Worker ⭐
│       │   └── favicon.svg             # 网站图标
│       ├── init/                    # 数据库初始化
│       │   └── storage.sql             # 表结构和示例数据
│       ├── application.yml          # 主配置文件
│       └── application-storage.yml  # 存储专用配置 ⭐
├── CLAUDE.md                        # AI开发指南 ⭐
├── README.md                        # 项目说明（本文件）
├── start.bat                        # Windows启动脚本
├── start.sh                         # Linux/Mac启动脚本
└── pom.xml                          # Maven配置
```

---

## 🔧 配置说明

### 应用配置

编辑 `src/main/resources/application-storage.yml`：

```yaml
server:
  port: 8081                          # 服务端口
  servlet:
    context-path: /                   # 上下文路径

spring:
  datasource:
    url: jdbc:mysql://localhost:3306/one_agent_4j
    username: root
    password: your_password
  servlet:
    multipart:
      max-file-size: 100MB            # 最大文件大小
      max-request-size: 100MB         # 最大请求大小

storage:
  upload:
    max-file-size: 104857600          # 100MB
    chunk-size: 5242880               # 5MB 分片大小
    temp-dir: /tmp/storage            # 临时目录

  preview:
    url-expiration: 3600              # 预览URL过期时间（秒）
    max-size: 10485760                # 10MB 预览最大大小

  security:
    allowed-file-types:               # 允许的文件类型
      - jpg
      - png
      - pdf
      - mp4
      - mp3
      - docx
      # ... 更多类型

    blocked-file-types:               # 禁止的文件类型
      - exe
      - sh
      - bat

  cache:
    ttl: 300                          # 缓存TTL（秒）
    max-entries: 1000                 # 最大缓存条目
    cache-dir: /tmp/storage-cache     # 缓存目录
```

### S3存储配置

支持多种S3兼容存储，在数据库中配置或通过API动态添加：

#### AWS S3
```yaml
type: S3
endpoint: https://s3.amazonaws.com
region: us-east-1
access-key-id: your_access_key
access-key-secret: your_secret_key
default-bucket: my-bucket
```

#### MinIO
```yaml
type: S3
endpoint: http://localhost:9000
region: us-east-1
access-key-id: minioadmin
access-key-secret: minioadmin
default-bucket: test-bucket
path-style-access: true              # MinIO必需
```

#### 阿里云OSS
```yaml
type: S3
endpoint: https://oss-cn-hangzhou.aliyuncs.com
region: cn-hangzhou
access-key-id: your_access_key_id
access-key-secret: your_access_key_secret
default-bucket: my-oss-bucket
```

---

## 📡 API 文档

### 存储配置管理

#### 保存配置
```http
POST /api/storage/config
Content-Type: application/json

{
  "name": "MinIO本地存储",
  "type": "S3",
  "endpoint": "http://localhost:9000",
  "accessKeyId": "minioadmin",
  "accessKeySecret": "minioadmin",
  "region": "us-east-1",
  "defaultBucket": "test-bucket"
}
```

#### 获取配置列表
```http
GET /api/storage/config/list
```

#### 测试连接
```http
POST /api/storage/config/test
Content-Type: application/json

{
  "endpoint": "http://localhost:9000",
  "accessKeyId": "minioadmin",
  "accessKeySecret": "minioadmin",
  "region": "us-east-1"
}
```

### 文件操作

#### 上传文件
```http
POST /api/storage/upload
Content-Type: multipart/form-data

bucketName=test-bucket
prefix=folder/
file=@/path/to/file.jpg
```

#### 获取文件列表
```http
POST /api/storage/files/list
Content-Type: application/json

{
  "bucketName": "test-bucket",
  "prefix": "folder/",
  "delimiter": "/",
  "pageSize": 100,
  "continuationToken": null
}
```

#### 下载文件
```http
GET /api/storage/download/{fileId}
```

#### 删除文件
```http
DELETE /api/storage/files/{fileId}
```

#### 重命名文件
```http
POST /api/storage/rename
Content-Type: application/json

{
  "bucketName": "test-bucket",
  "oldKey": "folder/old-name.jpg",
  "newKey": "folder/new-name.jpg"
}
```

#### 创建文件夹
```http
POST /api/storage/folder
Content-Type: application/json

{
  "bucketName": "test-bucket",
  "folderPath": "new-folder/"
}
```

#### 计算文件夹大小
```http
GET /api/storage/folder/size?bucketName=test-bucket&folderPath=folder/
```

#### 文件预览
```http
GET /api/storage/files/{fileId}/preview
```

#### 生成分享链接
```http
POST /api/storage/share
Content-Type: application/json

{
  "fileId": 123,
  "expirationMinutes": 60
}
```

### 缓存管理

#### 获取缓存统计
```http
GET /api/storage/cache/stats
```

#### 清除所有缓存
```http
DELETE /api/storage/cache/clear
```

#### 清除指定缓存
```http
DELETE /api/storage/cache/{cacheKey}
```

### 统计分析

#### 获取存储统计
```http
GET /api/storage/stats/config/{configId}
```

#### 文件类型分布
```http
GET /api/storage/stats/type/{configId}
```

#### 上传趋势
```http
GET /api/storage/stats/trend/{configId}?days=7
```

---

## 🔐 支持的存储服务

| 存储服务 | 状态 | 说明 |
|---------|------|------|
| AWS S3 | ✅ | 完全支持 |
| MinIO | ✅ | 完全支持 |
| 阿里云 OSS | ✅ | S3协议模式 |
| 腾讯云 COS | ✅ | S3协议模式 |
| 华为云 OBS | ✅ | S3协议模式 |
| Cloudflare R2 | ✅ | S3协议模式 |
| 七牛云 Kodo | ✅ | S3协议模式 |
| 其他S3兼容 | ✅ | 只要兼容S3协议即可 |

---

## 🛠️ 开发指南

### 本地开发

```bash
# 1. 克隆项目
git clone https://github.com/yourusername/s3-file-nexus.git
cd s3-file-nexus

# 2. 配置数据库（可选）
mysql -u root -p < src/main/resources/init/storage.sql

# 3. 修改配置
# 编辑 src/main/resources/application-storage.yml

# 4. 启动应用
mvn spring-boot:run -Dspring-boot.run.profiles=storage

# 5. 访问应用
# http://localhost:8081/index.html
```

### 前端开发

前端采用Vue 3 CDN模式，无需构建：

```bash
# 1. 修改代码
# 编辑 src/main/resources/static/index.html

# 2. 刷新浏览器 (F5) - 立即看到效果！
```

### 调试技巧

#### 后端调试
```yaml
# 开启调试日志 - application-storage.yml
logging:
  level:
    com.all.in.one.agent.storage: DEBUG
    software.amazon.awssdk: DEBUG
```

#### 前端调试
1. 打开浏览器开发者工具 (F12)
2. **Console** - 查看JavaScript日志
3. **Network** - 查看API请求
4. **Application** - 查看缓存和存储

### 打包部署

```bash
# 1. 构建JAR包
mvn clean package -DskipTests

# 2. 运行JAR
java -jar target/one-agent-4j-storage-0.0.1-SNAPSHOT.jar --spring.profiles.active=storage

# 3. 或使用Docker（未来版本）
docker build -t one-agent-storage .
docker run -p 8081:8081 one-agent-storage
```

---

## 📚 项目文档

- **[CLAUDE.md](CLAUDE.md)** - 项目架构和开发规范（AI开发指南）
- **[API文档](http://localhost:8081/doc.html)** - Swagger在线API文档
- **[数据库设计](src/main/resources/init/storage.sql)** - 表结构和示例数据

---

## 🐛 常见问题

### Q: 端口8081被占用怎么办？
A: 修改 `application-storage.yml` 中的 `server.port` 配置。

### Q: 无法连接到S3存储？
A: 检查以下几点：
1. endpoint配置是否正确
2. access key和secret key是否正确
3. 网络是否可以访问endpoint
4. MinIO需要设置 `path-style-access: true`

### Q: 上传文件失败？
A: 检查以下几点：
1. 文件大小是否超过限制（默认100MB）
2. 文件类型是否在允许列表中
3. 存储桶权限是否正确
4. 查看后端日志获取详细错误

### Q: 图片预览不显示？
A: 检查以下几点：
1. 浏览器控制台是否有CORS错误
2. 预签名URL是否过期
3. 存储桶是否允许公开访问
4. 查看Network面板确认请求状态

### Q: Service Worker缓存问题？
A: 清除缓存方法：
1. 点击页面右上角的垃圾桶图标
2. 或手动清除：F12 → Application → Clear storage

### Q: 如何在Windows上使用？
A: Windows的临时目录路径需要修改：
```yaml
storage:
  upload:
    temp-dir: C:/Temp/storage
  cache:
    cache-dir: C:/Temp/storage-cache
```

---

## 🎯 路线图

### v1.1.0 (计划中)
- [ ] 跨桶文件复制/移动
- [ ] 存储桶搜索和分组
- [ ] 文件版本管理
- [ ] 回收站功能

### v1.2.0 (计划中)
- [ ] 多用户支持
- [ ] 权限管理
- [ ] 操作日志
- [ ] 审计追踪

### v2.0.0 (计划中)
- [ ] Docker镜像
- [ ] Kubernetes部署
- [ ] 集群支持
- [ ] 负载均衡

---

## 🤝 贡献指南

欢迎贡献代码、报告问题或提出建议！

### 贡献流程

1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 提交 Pull Request

### 代码规范

- Java代码遵循阿里巴巴Java开发手册
- 前端代码遵循Vue.js风格指南
- 提交信息遵循 [Conventional Commits](https://www.conventionalcommits.org/)

---

## 📄 开源协议

本项目采用 [MIT License](LICENSE) 开源协议。

---

## 💖 致谢

感谢以下开源项目：

- [Spring Boot](https://spring.io/projects/spring-boot) - 优秀的Java应用框架
- [Vue.js](https://vuejs.org/) - 渐进式JavaScript框架
- [Tailwind CSS](https://tailwindcss.com/) - 实用优先的CSS框架
- [AWS SDK for Java](https://aws.amazon.com/sdk-for-java/) - AWS官方Java SDK
- [MinIO](https://min.io/) - 高性能对象存储
- [MyBatis-Plus](https://baomidou.com/) - MyBatis增强工具

---

## 📞 联系方式

- **Issues**: [GitHub Issues](https://github.com/yourusername/s3-file-nexus/issues)
- **Discussions**: [GitHub Discussions](https://github.com/yourusername/s3-file-nexus/discussions)

---

<div align="center">

**⭐ 如果这个项目对您有帮助，请给个Star支持一下！⭐**

🔥 **Like a Phoenix, Rising to Excellence** 🔥

Made with ❤️ by S3 File Nexus Team

[Homepage](https://github.com/yourusername/s3-file-nexus) • [Documentation](README.md) • [Report Bug](https://github.com/yourusername/s3-file-nexus/issues)

</div>
