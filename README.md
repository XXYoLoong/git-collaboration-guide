# Git Collaboration Guide

<p align="center">
  <strong>A practical Git workflow guide for GitHub, Gitee, and GitCode.</strong>
</p>

<p align="center">
  Standardized branches · Conventional commits · Pull Requests · Issues · SSH setup · FAQ
</p>

<p align="center">
  <a href="./README_en.md">English</a> · <a href="#1-完整流程">完整流程</a> · <a href="#2-所有代码汇总">所有代码汇总</a> · <a href="#3-常见问题">常见问题</a> · <a href="#4-关于我">关于我</a>
</p>

---

## 项目简介

这是一个面向 **GitHub / Gitee / GitCode** 的 Git 协作与提交流程说明仓库，适合用于：

- 团队协作规范
- 课程项目协作说明
- 开源仓库贡献指南
- 内部 Git 操作手册

本文所有示例统一使用 `XXX` 作为占位符，不包含真实姓名、学号、邮箱、仓库名、组织名等隐私信息。原始基础内容来自你提供的提交流程文本，包括从克隆仓库、创建分支、查看状态、提交、推送到 FAQ 的完整说明 fileciteturn0file0。

---

## 目录

- [1. 完整流程](#1-完整流程)
- [2. 所有代码汇总](#2-所有代码汇总)
- [3. 常见问题](#3-常见问题)
- [4. 关于我](#4-关于我)

---

## 1. 完整流程

### 1.1 协作原则

- 默认保护分支：`main`
- 禁止直接在 `main` 分支上开发、提交、推送
- 所有改动都必须通过独立分支完成
- 开发前先同步最新代码
- 推送后按团队要求发起 Pull Request
- 需要讨论、追踪、分配任务时使用 Issue

### 1.2 标准分支命名规范

推荐统一使用：

```bash
feature/xxx
fix/xxx
docs/xxx
refactor/xxx
test/xxx
chore/xxx
hotfix/xxx
release/v1.0.0
```

命名要求：

- 全部小写
- 多个单词之间使用短横线 `-`
- 分支名要体现用途
- 不使用中文、不使用空格、不使用真实姓名、不使用学号

示例：

```bash
feature/login-page
fix/readme-link
docs/git-guide
refactor/user-service
test/api-check
chore/update-gitignore
hotfix/build-error
release/v1.0.0
```

### 1.3 提交信息规范

推荐格式：

```bash
type(scope): subject
```

简化格式：

```bash
type: subject
```

常用类型：

- `feat`：新增功能
- `fix`：修复问题
- `docs`：文档修改
- `style`：格式调整，不改逻辑
- `refactor`：重构
- `test`：测试相关
- `chore`：杂项维护
- `build`：构建配置修改
- `ci`：CI/CD 修改

示例：

```bash
git commit -m "feat(auth): add login validation"
git commit -m "fix(api): resolve timeout issue"
git commit -m "docs: update contribution guide"
git commit -m "refactor(user): simplify service logic"
git commit -m "test: add branch naming checks"
git commit -m "chore: clean unused files"
```

### 1.4 Pull Request 标准

Pull Request 标题建议：

```bash
[type] brief description
```

示例：

```bash
[feat] add login page
[fix] correct clone command
[docs] update git workflow guide
```

Pull Request 描述建议包含：

```text
1. 改动内容
2. 改动原因
3. 影响范围
4. 自测情况
5. 备注说明
```

推荐流程：

```text
Issue -> Branch -> Commit -> Push -> Pull Request
```

### 1.5 Issue 标准

Issue 标题建议：

```bash
[type] brief description
```

示例：

```bash
[bug] push command fails on new branch
[docs] improve ssh setup section
[feature] add gitee workflow examples
[chore] reorganize repository structure
```

Issue 正文建议包含：

```text
1. 问题或需求描述
2. 复现步骤
3. 期望结果
4. 实际结果
5. 环境信息
6. 补充说明
```

### 1.6 开发前必须执行的准备动作

这一步非常重要。

每次开始开发前，都先同步主分支最新代码，再创建新分支。不要基于过期代码直接写。

```bash
git checkout main
git pull origin main
git checkout -b docs/git-guide
```

如果你已经在自己的分支上继续开发，也建议先确认主分支是否有更新，再按团队规则决定是否合并或 rebase。

### 1.7 从克隆到提交的完整标准流程

#### 第 1 步：进入准备存放项目的目录

```bash
cd /d/XXX/XXX
```

注意：

- 进入的是仓库目录的上一级目录
- 不要提前手动创建同名仓库目录
- 不要在已进入仓库目录后再次执行 `git clone`

#### 第 2 步：克隆远程仓库

GitHub：

```bash
git clone git@github.com:XXX/XXX.git
```

Gitee：

```bash
git clone git@gitee.com:XXX/XXX.git
```

GitCode：

```bash
git clone git@gitcode.com:XXX/XXX.git
```

进入仓库目录：

```bash
cd XXX
```

#### 第 3 步：检查远程仓库地址

```bash
git remote show origin
```

正常输出示例：

```text
Fetch URL: git@github.com:XXX/XXX.git
Push  URL: git@github.com:XXX/XXX.git
HEAD branch: main
```

#### 第 4 步：开发前拉取项目最新代码

```bash
git checkout main
git pull origin main
```

这是每次正式开发前的标准动作。

#### 第 5 步：创建规范化分支

```bash
git checkout -b docs/git-guide
```

或者：

```bash
git checkout -b feature/login-page
git checkout -b fix/api-timeout
```

#### 第 6 步：确认当前分支

```bash
git branch
```

示例输出：

```text
* docs/git-guide
  main
```

#### 第 7 步：开始修改文件

此时在当前分支中完成代码、文档、测试或配置修改。

#### 第 8 步：查看修改情况

```bash
git status
```

#### 第 9 步：加入暂存区

提交全部修改：

```bash
git add .
```

只提交部分文件：

```bash
git add README.md
git add docs/XXX.md
```

#### 第 10 步：本地提交

```bash
git commit -m "docs: update collaboration guide"
```

#### 第 11 步：推送到远程分支

第一次推送当前分支：

```bash
git push -u origin docs/git-guide
```

后续继续推送：

```bash
git push
```

#### 第 12 步：发起 Pull Request

1. 打开仓库网页
2. 进入 Pull Requests
3. 点击 New Pull Request
4. 选择源分支和目标分支
5. 填写规范化标题和描述
6. 提交审核

#### 第 13 步：如有需要，创建或关联 Issue

适用场景：

- 提交 Bug 修复
- 提交新功能需求
- 提交文档改进建议
- 提交重构计划或维护任务

### 1.8 后续继续修改时的标准流程

```bash
git checkout docs/git-guide
git status
git add .
git commit -m "docs: refine faq section"
git push
```

### 1.9 需要避免的错误操作

#### 不要直接在 `main` 分支开发

```bash
git checkout main
git add .
git commit -m "docs: update readme"
git push origin main
```

#### 不要让推送分支名和当前分支不一致

当前分支如果是：

```text
docs/git-guide
```

就必须推送：

```bash
git push -u origin docs/git-guide
```

#### 不要把仓库地址单独当作命令输入

```bash
git@github.com:XXX/XXX.git
```

#### 不要在仓库目录内部重复执行 `git clone`

#### 不要提交无关文件

例如：

- 编译产物
- 缓存文件
- IDE 私有配置
- 密钥文件
- token 文件
- 个人敏感信息文件

---

## 2. 所有代码汇总

### 2.1 克隆仓库

```bash
git clone git@github.com:XXX/XXX.git
git clone git@gitee.com:XXX/XXX.git
git clone git@gitcode.com:XXX/XXX.git
cd XXX
```

### 2.2 查看远程仓库信息

```bash
git remote show origin
git remote -v
```

### 2.3 开发前同步最新代码

```bash
git checkout main
git pull origin main
```

### 2.4 创建分支

```bash
git checkout -b feature/xxx
git checkout -b fix/xxx
git checkout -b docs/xxx
git checkout -b refactor/xxx
git checkout -b test/xxx
git checkout -b chore/xxx
git checkout -b hotfix/xxx
git checkout -b release/v1.0.0
```

### 2.5 查看当前分支与状态

```bash
git branch
git status
```

### 2.6 添加文件到暂存区

```bash
git add .
git add README.md
git add docs/XXX.md
```

### 2.7 提交代码

```bash
git commit -m "feat: add new feature"
git commit -m "fix: resolve push issue"
git commit -m "docs: update readme"
git commit -m "refactor: simplify workflow"
git commit -m "test: add example checks"
git commit -m "chore: clean temp files"
```

### 2.8 推送代码

```bash
git push -u origin feature/xxx
git push -u origin fix/xxx
git push -u origin docs/xxx
git push
```

### 2.9 SSH 相关命令

```bash
ls ~/.ssh
ssh-keygen -t ed25519 -C "XXX@example.com"
ssh-keygen -t rsa -b 4096 -C "XXX@example.com"
cat ~/.ssh/id_ed25519.pub
cat ~/.ssh/id_rsa.pub
ssh -T git@github.com
ssh -T git@gitee.com
ssh -T git@gitcode.com
```

### 2.10 重新设置远程地址

```bash
git remote set-url origin git@github.com:XXX/XXX.git
git remote set-url origin git@gitee.com:XXX/XXX.git
git remote set-url origin git@gitcode.com:XXX/XXX.git
```

### 2.11 Pull Request / Issue 前的本地准备命令

```bash
git checkout main
git pull origin main
git checkout -b feature/xxx
git status
git add .
git commit -m "feat: add xxx"
git push -u origin feature/xxx
```

### 2.12 完整流程命令示例

```bash
cd /d/XXX/XXX
git clone git@github.com:XXX/XXX.git
cd XXX

git remote show origin

git checkout main
git pull origin main

git checkout -b docs/git-guide

git status
git add .
git commit -m "docs: add collaboration guide"
git push -u origin docs/git-guide
```

### 2.13 后续更新命令示例

```bash
cd /d/XXX/XXX/XXX
git checkout docs/git-guide
git status
git add .
git commit -m "docs: refine collaboration guide"
git push
```

---

## 3. 常见问题

### 3.1 没有安装 Git

常见报错：

```text
git: command not found
```

或者：

```text
'git' 不是内部或外部命令，也不是可运行的程序或批处理文件
```

解决方法：

```bash
git --version
```

如果命令不可用，先安装 Git，再重新打开终端。

### 3.2 SSH 未配置成功

常见报错：

```text
Permission denied (publickey)
fatal: Could not read from remote repository.
```

解决方法：

#### 第一步：检查是否已有 SSH 密钥

```bash
ls ~/.ssh
```

#### 第二步：生成 SSH 密钥

```bash
ssh-keygen -t ed25519 -C "XXX@example.com"
```

如果不支持 `ed25519`：

```bash
ssh-keygen -t rsa -b 4096 -C "XXX@example.com"
```

#### 第三步：查看公钥

```bash
cat ~/.ssh/id_ed25519.pub
```

或者：

```bash
cat ~/.ssh/id_rsa.pub
```

#### 第四步：把公钥添加到对应平台

- GitHub：`Settings -> SSH and GPG keys -> New SSH key`
- Gitee：`设置 -> 安全设置 -> SSH 公钥`
- GitCode：`个人设置 -> 安全设置 / SSH 公钥管理`

#### 第五步：测试连接

```bash
ssh -T git@github.com
ssh -T git@gitee.com
ssh -T git@gitcode.com
```

### 3.3 没有仓库权限

常见报错：

```text
You are not allowed to push code to this project
```

或者：

```text
Permission to XXX/XXX.git denied to XXX
```

解决方法：

- 联系仓库管理员或项目负责人开通写权限
- 确认账号是否加入组织或协作者列表
- 权限开通后重新执行推送

```bash
git push -u origin feature/xxx
```

### 3.4 `src refspec XXX does not match any`

常见报错：

```text
error: src refspec XXX does not match any
error: failed to push some refs
```

解决方法：

```bash
git branch
git status
git add .
git commit -m "docs: add content"
git push -u origin docs/xxx
```

### 3.5 不小心在 `main` 分支改了文件

如果还没有提交：

```bash
git checkout -b docs/xxx
```

如果已经提交到了 `main`：

- 先停止继续操作
- 联系项目负责人处理
- 后续不要再直接在 `main` 上开发

### 3.6 在仓库目录里重复 `git clone`

正确做法：

```bash
cd ..
git clone git@github.com:XXX/XXX.git
```

### 3.7 仓库地址被当成命令直接输入

错误示例：

```bash
git@github.com:XXX/XXX.git
```

正确示例：

```bash
git clone git@github.com:XXX/XXX.git
```

### 3.8 Pull Request 和 Issue 应该什么时候用

#### Pull Request 适用场景

- 代码已经完成，需要合并到目标分支
- 需要代码评审
- 需要团队审核后再进入主分支

#### Issue 适用场景

- 记录 Bug
- 跟踪需求
- 管理文档任务
- 沉淀讨论过程

推荐协作顺序：

```text
Issue -> Branch -> Commit -> Push -> Pull Request
```

---

## 4. 关于我

Yoloong 是这份文档仓库的维护者标识。

这里的“关于我”不放置任何真实隐私信息，只保留适合公开仓库展示的简要介绍：

- 关注 Git 协作规范、开发流程规范和项目工程化表达
- 希望把分散的 Git 操作经验整理成可复用、可下发、可公开展示的标准文档
- 本仓库适合作为 README 模板、团队协作模板、课程项目模板和开源项目贡献模板

为保护隐私，本文档中的示例统一使用 `XXX` 占位，不包含真实姓名、学号、邮箱、仓库名、组织名等个人信息。