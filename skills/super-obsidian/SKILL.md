# Super Obsidian — CLI-First Knowledge Base Operations

> 检测环境 → 用 Obsidian CLI 搜索/读写 → 永远不直接遍历 .md 文件

---

## 前提条件

1. **Obsidian App 必须正在运行**（CLI 是 App 的遥控器，不是独立工具）
2. CLI 已在 Settings → General → Command line interface 中启用
3. `obsidian` 命令在 PATH 中可用

**验证**：
```bash
obsidian version
```

如果命令不存在，提示用户：
- macOS: 在 Obsidian 设置中启用 CLI，会自动添加到 PATH
- 手动添加: 将 Obsidian 可执行文件路径加入 PATH

---

## 核心原则

1. **搜索必用 CLI**：`obsidian search` 使用 Obsidian 原生搜索引擎，效果远优于 grep/rg 遍历 .md 文件
2. **走正门**：通过 CLI 操作保证索引一致性，避免直接读写文件系统导致索引错乱
3. **引号规则**：参数有空格必须双引号，换行用 `\n`
4. **file 参数**：通常不需要 `.md` 后缀，Obsidian 自动解析；路径相对于 vault 根目录

---

## 命令速查

### 🔍 搜索（最重要 — 替代 grep/rg）

| 命令 | 用途 | 示例 |
|------|------|------|
| `obsidian search query="关键词"` | 全文搜索 | `obsidian search query="项目规划" --copy` |
| `obsidian search:context query="关键词" limit=N` | 带上下文的全文搜索 | `obsidian search:context query="瓶颈" limit=10` |
| `obsidian backlinks file="笔记名"` | 查反向链接（谁引用了这篇） | `obsidian backlinks file="项目A"` |
| `obsidian links file="笔记名"` | 查外链（这篇引用了谁） | `obsidian links file="项目A"` |
| `obsidian orphans` | 查找孤立笔记（无链接） | |
| `obsidian tags` | 列出所有标签 | |
| `obsidian tasks` | 显示所有任务 | |
| `obsidian random` | 随机打开一篇笔记 | |

### 📖 读取

| 命令 | 用途 | 示例 |
|------|------|------|
| `obsidian read file="笔记名"` | 读取笔记内容 | `obsidian read file="年度计划" --copy` |
| `obsidian daily:read` | 读取今日日记 | |
| `obsidian outline file="笔记名"` | 获取笔记大纲 | |
| `obsidian wordcount` | 字数统计 | |
| `obsidian bookmarks` | 书签列表 | |

### ✏️ 写入 / 创建

| 命令 | 用途 | 示例 |
|------|------|------|
| `obsidian create name="标题" content="内容"` | 创建新笔记 | `obsidian create name="会议记录" content="# 会议\n- 议题1" open` |
| `obsidian append path="文件.md" content="文字"` | 追加到指定笔记 | `obsidian append path="项目日志.md" content="\n## 进展\n..."` |
| `obsidian prepend path="文件.md" content="文字"` | 前插到指定笔记 | |
| `obsidian daily:append content="文字"` | 追加到今日日记 | `obsidian daily:append content="- [ ] 买牛奶"` |
| `obsidian daily:prepend content="文字"` | 前插到今日日记 | |

### 📅 日记（Daily Notes）

| 命令 | 用途 |
|------|------|
| `obsidian daily` | 打开今日笔记 |
| `obsidian daily:path` | 显示今日笔记路径 |
| `obsidian daily:read` | 读取今日笔记内容 |
| `obsidian daily:append content="..."` | 追加到今日笔记 |
| `obsidian daily:prepend content="..."` | 前插到今日笔记 |

### 📝 属性 / 标签 / 任务

| 命令 | 用途 | 示例 |
|------|------|------|
| `obsidian property:set file="笔记" name="键" value="值"` | 设置 YAML 属性 | `obsidian property:set file="项目A" name="status" value="done"` |
| `obsidian tags` | 列出所有标签 | |
| `obsidian task ref="文件:行号" toggle` | 切换任务完成状态 | |

### 📂 文件管理

| 命令 | 用途 | 示例 |
|------|------|------|
| `obsidian open file="笔记名"` | 打开笔记 | |
| `obsidian move file="旧名" to="新路径"` | 移动/重命名 | |
| `obsidian rename file="旧名" name="新名"` | 重命名 | |
| `obsidian delete file="笔记名"` | 删除（加 `permanent` 永久删除） | |

### 🗄️ Vault / 插件 / 工作区

| 命令 | 用途 |
|------|------|
| `obsidian vaults` | 列出所有 vault |
| `obsidian vault:open name="vault名"` | 切换 vault |
| `obsidian plugins` | 列出插件 |
| `obsidian plugin:enable id="插件ID"` | 启用插件 |
| `obsidian workspace:save name="工作区名"` | 保存工作区 |
| `obsidian workspace:load name="工作区名"` | 加载工作区 |

### 🛠️ 开发者 / 高级

| 命令 | 用途 |
|------|------|
| `obsidian eval code="JS代码"` | 执行 Obsidian 内部 JS API |
| `obsidian devtools` | 打开开发者工具 |
| `obsidian dev:screenshot` | 截图 |
| `obsidian help` | 查看全部命令 |
| `obsidian help <命令>` | 查看具体命令帮助 |
| `obsidian reload` | 重载窗口 |

---

## 典型工作流

### 搜索 → 阅读 → 总结追加

```bash
# 1. 搜索相关笔记
obsidian search query="项目规划"

# 2. 读取最相关的笔记
obsidian read file="2026年项目规划"

# 3. 追加 AI 总结
obsidian append path="2026年项目规划.md" content="\n---\n## AI 总结\n要点1...\n要点2..."
```

### 日记工作流

```bash
# 查看今日日记
obsidian daily:read

# 追加记录
obsidian daily:append content="\n## 工作记录\n- 完成了 X 功能\n- 发现了 Y 问题"

# 追加待办
obsidian daily:append content="\n- [ ] 明天跟进 Z"
```

### 知识图谱探索

```bash
# 查看某个笔记被谁引用
obsidian backlinks file="核心概念A"

# 查看某个笔记引用了什么
obsidian links file="核心概念A"

# 找到孤立笔记（可能需要整理）
obsidian orphans
```

### 批量属性管理

```bash
# 标记笔记状态
obsidian property:set file="项目A" name="status" value="completed"
obsidian property:set file="项目B" name="priority" value="high"
```

---

## ⚠️ 注意事项

1. **Obsidian 必须运行**：所有 CLI 命令都通过 App 执行，App 关闭则全部失败
2. **不要直接修改 .md 文件**：会导致 Obsidian 索引错乱，用 CLI 的 append/prepend/create
3. **搜索结果格式**：CLI 返回纯文本，可以直接解析
4. **content 中的换行**：使用 `\n`，不要使用实际换行符
5. **--copy 标志**：将结果复制到系统剪贴板，适合快速传递
6. **open / newtab 标志**：在 Obsidian UI 中打开笔记（create、open 等命令可用）

---

## 何时回退到文件系统操作

仅在以下情况直接操作文件：
- Obsidian App 未运行且无法启动
- 需要批量处理超出 CLI 能力的操作（如正则替换所有文件）
- 处理 .obsidian/ 配置文件本身

其他所有情况，**一律使用 Obsidian CLI**。
