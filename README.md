## iMap: 基于百度地图 API 的地图工具

### ✨ 特点

- `Flask` 后端框架: 轻量级 Web 框架，适用于简单项目快速落地

- `sqlite` 与 `flask_sqlalchemy`：轻量级数据库和强大的数据库连接工具

- `Bootstrap` 前端框架：便捷的 CDN 链接导入形式

- `Jinja2` 模板引擎：提高 html 代码复用性

- `Blueprint` 蓝图：高扩展、低耦合

- 百度地图 API：调用 JS API 快速实现相关功能

### 🚀 本地运行

1. 克隆项目到本地
    
    ```bash
    git clone https://github.com/shaneworld/iMap.git
    ```

2. 安装依赖

    ```bash
    pip install -r reqirements.txt
    ```

3. 初始化数据库迁移工具

    ```bash
    flask db init
    flask db migrate -m "Initial migration."
    flask db upgrade
    ```

4. 在[百度地图开放平台](https://lbsyun.baidu.com/)创建应用并获取 API 密钥（AK），
并将密钥复制到 `app/constants.py` 中对应位置。

5. 在根目录中执行 `flask run` 或者 `./run.sh` 运行该项目。

### 🔨 项目结构

```
drwxr-xr-x   .
drwxr-xr-x  ├──  app
.rw-r--r--  │   ├──  __init__.py
drwxr-xr-x  │   ├──  blueprints
drwxr-xr-x  │   │   ├──  map
drwxr-xr-x  │   │   └──  metro
.rw-r--r--  │   ├──  constants.py
drwxr-xr-x  │   ├──  database
.rw-r--r--  │   │   ├──  init.sql
.rw-r--r--  │   │   └──  locations.db
drwxr-xr-x  │   ├──  models
.rw-r--r--  │   │   └──  locations.py
drwxr-xr-x  │   └──  templates
.rw-r--r--  │       └──  basic.html
.rw-r--r--  ├──  config.py
.rw-r--r--  ├── 󰂺 README.md
.rw-r--r--  ├──  requirements.txt
.rwxr-xr-x  └──  run.sh
```

1. `run.sh`：
    为执行脚本，收到 `Ctrl-c` 终止信号后自动删除项目生成的 `__pycache__` 缓存文件夹。

2. `config.py`：
    包含 flask 应用初始化配置信息，如应用密钥（随机生成）以及数据库文件生成路径。
    统一管理，便于维护。

3. `app/__init__`：
    初始化应用，包括数据库连接、蓝图等。

4. `constants.py`：
    存放所有常量。

5. `app/blueprints/`：
    定义所有蓝图模块，每个文件夹代表一个模块。如需新功能，可以新建模块进行扩展。

6. `app/database/`：
    存放数据库文件。`init.sql` 为初始化的实例数据，用于测试，可以在初始化数据库后导入数据库文件。

7. `app/models/`：
    定义数据库表以及表结构，使用 `flask_sqlalchemy` 实现与数据库的连接。

8. `app/templates/`：
    定义所有 html 模板文件，显示前端页面。
