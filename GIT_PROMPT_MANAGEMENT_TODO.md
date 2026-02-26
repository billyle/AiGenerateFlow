# Git化Prompt管理功能开发计划

## 🎯 项目概述
实现基于Git的Prompt模板版本管理功能，支持远程仓库同步、AI驱动的commit message生成等功能。

## 📋 功能需求清单

### 核心功能模块

#### 1. 配置管理模块
- [ ] 在 `IdeaSettings.State` 中添加Git相关配置项：
  - `gitRepositoryUrl` - 远程Git仓库URL
  - `localRepositoryPath` - 本地仓库路径  
  - `promptFilePath` - Prompt文件相对路径
  - `autoPushEnabled` - 是否自动推送开关
  - `gitUserName` - Git用户名
  - `gitUserEmail` - Git邮箱

#### 2. Git操作核心模块
- [ ] 创建 `GitPromptManager` 类封装Git操作
- [ ] 实现仓库初始化逻辑（clone/pull）
- [ ] 实现保存并提交功能
- [ ] 实现拉取远程功能
- [ ] 实现推送远程功能
- [ ] 实现差异比较功能

#### 3. AI集成模块
- [ ] 实现基于Git diff的commit message自动生成
- [ ] 集成当前选择的AI模型
- [ ] 设计合理的prompt模板用于commit message生成

#### 4. UI界面模块
- [ ] 在配置面板添加Git仓库配置区域
- [ ] 添加核心操作按钮：克隆/初始化、拉取、推送、打开文件夹
- [ ] 在Prompt编辑界面添加"保存并提交"按钮
- [ ] 添加状态显示区域（Git状态、提交历史等）

## 🔧 技术实现细节

### 类结构设计
```
com.huq.idea.flow.git
├── GitPromptManager.java          # Git操作核心类
├── GitConfig.java                 # Git配置数据类  
├── GitOperationException.java     # Git操作异常类
└── ui/
    ├── GitConfigPanel.java        # Git配置UI面板
    └── GitStatusPanel.java        # Git状态显示面板
```

### 核心方法清单

**GitPromptManager类：**
- [ ] `initializeRepository(String remoteUrl, String localPath)` - 初始化仓库
- [ ] `saveAndCommit(String promptContent, AiProvider provider)` - 保存并提交
- [ ] `generateCommitMessage(String diff, AiProvider provider)` - 生成commit message
- [ ] `pullRemote()` - 拉取远程更改
- [ ] `pushRemote()` - 推送本地更改
- [ ] `getCommitHistory()` - 获取提交历史
- [ ] `getCurrentStatus()` - 获取当前Git状态

### UI组件设计

**配置面板组件：**
- [ ] Git仓库URL输入框
- [ ] 本地路径选择器
- [ ] Prompt文件路径输入框
- [ ] 自动推送复选框
- [ ] Git用户信息输入框
- [ ] 操作按钮组（克隆、拉取、推送、打开文件夹）

**Prompt编辑界面增强：**
- [ ] "保存并提交"按钮替代原有的"应用修改"
- [ ] Git状态指示器
- [ ] 最近提交历史快速查看

## ⚡ 关键技术点

### Git操作实现
- 使用JGit库进行Git操作
- 异步执行避免UI阻塞
- 完善的错误处理和用户提示

### AI集成要点
- 调用当前选择的AI提供商
- 设计专门的commit message生成prompt
- 处理AI调用失败的降级方案

### 用户体验优化
- 进度条显示长时间操作
- 状态栏实时显示Git状态
- 快捷键支持
- 操作历史记录

## 🛡️ 安全和稳定性考虑

- [ ] 敏感信息（Git凭证）的安全存储
- [ ] 网络操作的超时和重试机制
- [ ] 冲突处理和合并策略
- [ ] 本地备份机制防止数据丢失
- [ ] 权限检查和操作限制

## 📈 开发优先级建议

### 第一阶段（MVP）：
1. 基础Git操作功能
2. 核心配置管理
3. 基本的保存和提交功能

### 第二阶段（增强功能）：
1. AI驱动的commit message生成
2. 完整的UI界面
3. 状态监控和历史查看

### 第三阶段（高级功能）：
1. 分支管理
2. 冲突解决界面
3. 批量操作支持

## 📝 待决策事项

- [ ] Commit message的语言偏好（中文/英文）
- [ ] 默认的Prompt文件名和路径
- [ ] 自动推送的默认开启状态
- [ ] 本地仓库的默认存储位置
- [ ] 错误处理的具体策略
- [ ] 用户界面的最终布局设计

## 🔗 相关依赖
- JGit库用于Git操作
- 现有的AI工具类
- IntelliJ Platform API
- Swing UI组件

---
*此文档将持续更新，记录开发进展和需求变更*