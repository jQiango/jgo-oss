# 快速开始指南

> 3分钟快速启动 S3 File Nexus 🚀

---

## 🚀 方式一：直接运行（推荐）

### 前置要求
- ✅ JDK 17+
- ✅ Maven 3.6+
- ✅ 一个S3兼容存储（如MinIO）

### 启动步骤

#### 1. 克隆项目
```bash
git clone https://github.com/yourusername/s3-file-nexus.git
cd s3-file-nexus
```

#### 2. 启动应用

**Windows:**
```bash
start.bat
```

**Linux/Mac:**
```bash
chmod +x start.sh
./start.sh
```

#### 3. 访问应用
打开浏览器访问：
```
http://localhost:8081/index.html
```

**就这么简单！** 🎉

---

## 📦 方式二：使用JAR包

### 1. 下载发布包
从 [Releases](https://github.com/yourusername/s3-file-nexus/releases) 下载最新版本：
- `s3-file-nexus-1.0.0.jar`

### 2. 运行JAR
```bash
java -jar s3-file-nexus-1.0.0.jar --spring.profiles.active=storage
```

### 3. 访问应用
```
http://localhost:8081/index.html
```

---

## 🔧 配置MinIO（可选）

如果你还没有S3存储，可以快速启动一个本地MinIO：

### 使用Docker
```bash
docker run -d \
  -p 9000:9000 \
  -p 9001:9001 \
  --name minio \
  -e "MINIO_ROOT_USER=minioadmin" \
  -e "MINIO_ROOT_PASSWORD=minioadmin" \
  minio/minio server /data --console-address ":9001"
```

### 访问MinIO控制台
```
http://localhost:9001
用户名: minioadmin
密码: minioadmin
```

### 创建存储桶
1. 登录MinIO控制台
2. 点击 "Create Bucket"
3. 输入桶名: `test-bucket`
4. 点击 "Create"

---

## ⚙️ 配置存储（首次使用）

### 方式1：通过页面配置

1. 访问主页面
2. 点击右上角的"设置"图标
3. 添加存储配置：
   ```
   名称: MinIO本地存储
   类型: S3
   Endpoint: http://localhost:9000
   Region: us-east-1
   Access Key: minioadmin
   Secret Key: minioadmin
   默认Bucket: test-bucket
   ```
4. 点击"测试连接"
5. 点击"保存"

### 方式2：修改配置文件

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

重启应用使配置生效。

---

## 📖 数据库配置（可选）

如需持久化存储配置，配置MySQL：

### 1. 创建数据库
```sql
CREATE DATABASE one_agent_4j DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

### 2. 导入表结构
```bash
mysql -u root -p one_agent_4j < src/main/resources/init/storage.sql
```

### 3. 修改配置
编辑 `application-storage.yml`：
```yaml
spring:
  datasource:
    url: jdbc:mysql://localhost:3306/one_agent_4j
    username: root
    password: your_password
```

### 4. 重启应用

---

## 🎯 开始使用

### 1. 上传文件

#### 方式1：点击上传按钮
1. 点击右上角的"上传文件"按钮
2. 选择文件
3. 等待上传完成

#### 方式2：拖拽上传
1. 直接将文件拖到页面
2. 自动开始上传

### 2. 浏览文件
- 点击文件夹进入
- 点击面包屑返回
- 使用搜索框搜索文件

### 3. 预览文件
- **图片**: 点击即可预览
- **视频/音频**: 点击播放
- **文档**: 点击查看

### 4. 管理文件
- **右键点击文件**: 显示操作菜单
  - 下载
  - 重命名
  - 删除
  - 生成分享链接
  - 预览

### 5. 切换视图
- 点击右上角的视图切换按钮
- 列表视图 ↔️ 网格视图

### 6. 暗色模式
- 点击右上角的月亮图标
- 切换亮色/暗色主题

---

## 🆘 常见问题

### Q: 启动失败，端口被占用？
```bash
# 修改端口 - application-storage.yml
server:
  port: 8082  # 改成其他端口
```

### Q: 无法连接MinIO？
检查：
1. MinIO是否正在运行: `docker ps`
2. 端口是否正确: 9000
3. 凭证是否正确: minioadmin/minioadmin

### Q: 上传失败？
检查：
1. 文件大小是否超过100MB
2. MinIO存储桶是否存在
3. 查看浏览器控制台错误信息

### Q: 页面空白？
1. 打开浏览器控制台 (F12)
2. 查看错误信息
3. 确认后端API是否正常运行

---

## 📚 下一步

- 📖 阅读完整文档：[README.md](README.md)
- 🔧 了解配置选项：[配置说明](README.md#-配置说明)
- 📡 查看API文档：http://localhost:8081/doc.html
- 🏗️ 学习架构设计：[CLAUDE.md](CLAUDE.md)

---

## 🎉 享受使用！

如果遇到问题：
- 📝 查看 [常见问题](README.md#-常见问题)
- 🐛 提交 [Issue](https://github.com/yourusername/s3-file-nexus/issues)
- 💬 参与 [Discussions](https://github.com/yourusername/s3-file-nexus/discussions)

**⭐ 如果觉得有用，请给个Star支持一下！**

---

<div align="center">

🔥 **Like a Phoenix, Rising to Excellence** 🔥

Made with ❤️ by S3 File Nexus Team

[GitHub](https://github.com/yourusername/s3-file-nexus) • [文档](README.md) • [问题反馈](https://github.com/yourusername/s3-file-nexus/issues)

</div>
