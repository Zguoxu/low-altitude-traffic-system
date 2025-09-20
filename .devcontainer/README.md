# 低空交通系统 - Dev Container 开发环境

## 🚀 快速开始

这个项目已经配置了Dev Container开发环境，您的朋友可以通过以下步骤直接开始开发，无需手动安装任何依赖。

### 前置要求

您的朋友需要在本地安装：

1. **Docker Desktop** (Windows/Mac) 或 **Docker Engine** (Linux)
   - 下载：https://www.docker.com/products/docker-desktop

2. **Visual Studio Code**
   - 下载：https://code.visualstudio.com/

3. **Dev Containers 扩展**
   - 在VSCode中搜索并安装 "Dev Containers" 扩展

### 🔧 使用步骤

1. **克隆项目**
   ```bash
   git clone <项目地址>
   cd low-altitude-traffic-system
   ```

2. **在VSCode中打开项目**
   ```bash
   code .
   ```

3. **启动Dev Container**
   - VSCode会自动检测到`.devcontainer`配置
   - 右下角会弹出提示："Reopen in Container"，点击确认
   - 或者使用命令面板 (Ctrl+Shift+P)，输入 "Dev Containers: Reopen in Container"

4. **等待环境构建**
   - 首次运行会下载和构建Docker镜像（可能需要10-15分钟）
   - 后续启动会很快（1-2分钟）

5. **开始开发！**
   - 环境已经包含所有必要的工具和依赖
   - 数据库会自动启动并初始化

## 🛠️ 开发环境包含

### 前端开发
- **Node.js** (最新LTS版本)
- **Vue CLI** 和相关工具
- **npm** 包管理器
- **ESLint** 代码检查
- **Prettier** 代码格式化

### 后端开发
- **C++17** 开发环境
- **CMake** 构建系统
- **vcpkg** 包管理器
- **GDB** 调试器
- 预安装的 C++ 库：
  - httplib (HTTP服务器)
  - nlohmann/json (JSON处理)
  - OpenSSL (加密)
  - libmysql (数据库连接)
  - ixwebsocket (WebSocket)

### 数据库
- **MySQL 8.0**
- 预配置的数据库和用户
- 自动加载数据库架构

### 开发工具
- **Git** 版本控制
- **MySQL客户端**
- **调试工具** (GDB, Valgrind)

## 📋 快速命令

打开VSCode终端后，可以使用以下命令：

### 前端开发
```bash
# 安装依赖
npm install

# 启动开发服务器
npm run serve
# 或使用快捷脚本
./run-frontend.sh

# 构建生产版本
npm run build

# 代码检查
npm run lint
```

### 后端开发
```bash
# 构建后端
./build-backend.sh

# 或手动构建
cd backend/build
cmake -DCMAKE_TOOLCHAIN_FILE=$VCPKG_ROOT/scripts/buildsystems/vcpkg.cmake ..
make -j$(nproc)

# 运行后端
./backend/build/low_altitude_traffic_system_backend
```

### 数据库操作
```bash
# 连接数据库
mysql -h mysql -u appuser -papppassword low_altitude_traffic

# 检查数据库连接
mysql -h mysql -u appuser -papppassword -e "SELECT 'Database connection successful!' as status;"
```

## 🌐 访问地址

开发环境启动后，可以通过以下地址访问：

- **前端应用**: http://localhost:5173
- **后端API**: http://localhost:8080
- **数据库**: localhost:3306

## ⚡ VSCode 功能

### 调试支持
- **F5**: 启动C++后端调试
- **Ctrl+F5**: 启动前端开发服务器
- 支持断点调试和变量检查

### 任务快捷键
使用 `Ctrl+Shift+P` 打开命令面板，然后输入：
- `Tasks: Run Task` 查看所有可用任务
- 包括构建、运行、测试等任务

### 内置终端
- 自动配置好环境变量
- 支持多个终端标签
- 预设工作目录

## 🔧 自定义配置

如需修改开发环境配置，可以编辑以下文件：

- `.devcontainer/devcontainer.json` - 主配置
- `.devcontainer/docker-compose.dev.yml` - 服务配置
- `.devcontainer/Dockerfile.dev` - 容器镜像
- `.vscode/settings.json` - VSCode设置
- `.vscode/launch.json` - 调试配置
- `.vscode/tasks.json` - 任务配置

## 🐛 故障排除

### 常见问题

1. **容器启动失败**
   - 确保Docker正在运行
   - 检查磁盘空间是否充足
   - 重启Docker Desktop

2. **数据库连接失败**
   - 等待MySQL容器完全启动（通常需要30秒）
   - 检查 `.devcontainer/setup.sh` 中的连接测试

3. **端口冲突**
   - 确保端口5173、8080、3306没有被其他程序占用
   - 可以修改 `.devcontainer/docker-compose.dev.yml` 中的端口映射

4. **构建失败**
   - 清理Docker缓存：`docker system prune`
   - 重新构建容器

### 获取帮助

如果遇到问题，可以：
1. 查看VSCode的Dev Container日志
2. 检查Docker容器状态：`docker ps`
3. 查看容器日志：`docker logs <container-name>`

## 📝 注意事项

- 首次运行需要下载较大的Docker镜像
- 建议在稳定的网络环境下初始化
- 代码文件会自动同步到容器中
- 容器内的文件修改会实时反映到本地

---

**现在您的朋友只需要安装Docker和VSCode，就可以立即开始开发了！** 🎉