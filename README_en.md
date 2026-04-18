# Git Collaboration Guide

<p align="center">
  <strong>A practical Git workflow guide for GitHub, Gitee, and GitCode.</strong>
</p>

<p align="center">
  Standardized branches · Conventional commits · Pull Requests · Issues · SSH setup · FAQ
</p>

<p align="center">
  <a href="./README.md">中文</a> · <a href="#1-complete-workflow">Complete Workflow</a> · <a href="#2-command-reference">Command Reference</a> · <a href="#3-faq">FAQ</a> · <a href="#4-about-me">About Me</a>
</p>

---

## Overview

This repository is a Git collaboration and submission guide for **GitHub / Gitee / GitCode**. It can be used as:

- a team collaboration guide
- a course project workflow guide
- an open-source contribution guide
- an internal Git operation handbook

All examples in this document use `XXX` as placeholders. No real names, student IDs, emails, repository names, or organization names are exposed.

---

## Table of Contents

- [1. Complete Workflow](#1-complete-workflow)
- [2. Command Reference](#2-command-reference)
- [3. FAQ](#3-faq)
- [4. About Me](#4-about-me)

---

## 1. Complete Workflow

### 1.1 Collaboration Rules

- Default protected branch: `main`
- Never develop, commit, or push directly on `main`
- All changes must be completed in dedicated branches
- Always sync the latest code before starting development
- Open a Pull Request after pushing your branch
- Use Issues to track bugs, tasks, and discussions

### 1.2 Branch Naming Convention

Recommended patterns:

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

Rules:

- use lowercase only
- use hyphens `-` between words
- branch names must clearly indicate purpose
- do not use Chinese, spaces, real names, or student IDs

Examples:

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

### 1.3 Commit Message Convention

Recommended format:

```bash
type(scope): subject
```

Simplified format:

```bash
type: subject
```

Common types:

- `feat`: new feature
- `fix`: bug fix
- `docs`: documentation changes
- `style`: formatting only, no logic change
- `refactor`: code refactor
- `test`: test-related changes
- `chore`: maintenance tasks
- `build`: build config changes
- `ci`: CI/CD updates

Examples:

```bash
git commit -m "feat(auth): add login validation"
git commit -m "fix(api): resolve timeout issue"
git commit -m "docs: update contribution guide"
git commit -m "refactor(user): simplify service logic"
git commit -m "test: add branch naming checks"
git commit -m "chore: clean unused files"
```

### 1.4 Pull Request Standard

Recommended PR title format:

```bash
[type] brief description
```

Examples:

```bash
[feat] add login page
[fix] correct clone command
[docs] update git workflow guide
```

Recommended PR body sections:

```text
1. What changed
2. Why it changed
3. Scope of impact
4. Self-test result
5. Notes
```

Suggested workflow:

```text
Issue -> Branch -> Commit -> Push -> Pull Request
```

### 1.5 Issue Standard

Recommended Issue title format:

```bash
[type] brief description
```

Examples:

```bash
[bug] push command fails on new branch
[docs] improve ssh setup section
[feature] add gitee workflow examples
[chore] reorganize repository structure
```

Recommended Issue body sections:

```text
1. Problem or request
2. Reproduction steps
3. Expected result
4. Actual result
5. Environment
6. Extra notes
```

### 1.6 Required Preparation Before Development

This step is essential.

Before starting any work, always sync the latest code from the main branch first, and then create a new branch.

```bash
git checkout main
git pull origin main
git checkout -b docs/git-guide
```

If you continue working on your own branch, first confirm whether `main` has been updated and then decide whether to merge or rebase according to your team rules.

### 1.7 Full Standard Workflow: From Clone to Submission

#### Step 1: Enter the parent directory where you want to store the project

```bash
cd /d/XXX/XXX
```

Notes:

- enter the parent directory of the repository
- do not manually create a same-name folder in advance
- do not run `git clone` again inside the repository directory

#### Step 2: Clone the remote repository

GitHub:

```bash
git clone git@github.com:XXX/XXX.git
```

Gitee:

```bash
git clone git@gitee.com:XXX/XXX.git
```

GitCode:

```bash
git clone git@gitcode.com:XXX/XXX.git
```

Enter the repository directory:

```bash
cd XXX
```

#### Step 3: Check the remote repository

```bash
git remote show origin
```

Example output:

```text
Fetch URL: git@github.com:XXX/XXX.git
Push  URL: git@github.com:XXX/XXX.git
HEAD branch: main
```

#### Step 4: Pull the latest code before development

```bash
git checkout main
git pull origin main
```

#### Step 5: Create a standardized branch

```bash
git checkout -b docs/git-guide
```

Or:

```bash
git checkout -b feature/login-page
git checkout -b fix/api-timeout
```

#### Step 6: Confirm the current branch

```bash
git branch
```

Example output:

```text
* docs/git-guide
  main
```

#### Step 7: Modify files

Make your code, document, test, or config changes on the current branch.

#### Step 8: Check file changes

```bash
git status
```

#### Step 9: Add changes to staging area

Add all changes:

```bash
git add .
```

Add selected files only:

```bash
git add README.md
git add docs/XXX.md
```

#### Step 10: Commit locally

```bash
git commit -m "docs: update collaboration guide"
```

#### Step 11: Push to remote branch

First push:

```bash
git push -u origin docs/git-guide
```

Later pushes:

```bash
git push
```

#### Step 12: Open a Pull Request

1. Open the repository webpage
2. Go to Pull Requests
3. Click New Pull Request
4. Select head and base branches
5. Fill in a standard title and description
6. Submit for review

#### Step 13: Create or link an Issue if needed

Use cases:

- bug fixes
- new feature requests
- documentation improvements
- refactor or maintenance plans

### 1.8 Standard Workflow for Later Updates

```bash
git checkout docs/git-guide
git status
git add .
git commit -m "docs: refine faq section"
git push
```

### 1.9 Wrong Operations to Avoid

#### Never develop directly on `main`

```bash
git checkout main
git add .
git commit -m "docs: update readme"
git push origin main
```

#### Do not mismatch the current branch and push target branch

If the current branch is:

```text
docs/git-guide
```

then push:

```bash
git push -u origin docs/git-guide
```

#### Do not type the repository URL as a command

```bash
git@github.com:XXX/XXX.git
```

#### Do not run `git clone` repeatedly inside the repository directory

#### Do not commit irrelevant files

Examples:

- build outputs
- cache files
- IDE private configs
- key files
- token files
- personal sensitive files

---

## 2. Command Reference

### 2.1 Clone repository

```bash
git clone git@github.com:XXX/XXX.git
git clone git@gitee.com:XXX/XXX.git
git clone git@gitcode.com:XXX/XXX.git
cd XXX
```

### 2.2 Check remote repository info

```bash
git remote show origin
git remote -v
```

### 2.3 Sync latest code before development

```bash
git checkout main
git pull origin main
```

### 2.4 Create branches

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

### 2.5 Check current branch and status

```bash
git branch
git status
```

### 2.6 Add files to staging area

```bash
git add .
git add README.md
git add docs/XXX.md
```

### 2.7 Commit changes

```bash
git commit -m "feat: add new feature"
git commit -m "fix: resolve push issue"
git commit -m "docs: update readme"
git commit -m "refactor: simplify workflow"
git commit -m "test: add example checks"
git commit -m "chore: clean temp files"
```

### 2.8 Push changes

```bash
git push -u origin feature/xxx
git push -u origin fix/xxx
git push -u origin docs/xxx
git push
```

### 2.9 SSH commands

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

### 2.10 Reset remote URL

```bash
git remote set-url origin git@github.com:XXX/XXX.git
git remote set-url origin git@gitee.com:XXX/XXX.git
git remote set-url origin git@gitcode.com:XXX/XXX.git
```

### 2.11 Local preparation before PR / Issue

```bash
git checkout main
git pull origin main
git checkout -b feature/xxx
git status
git add .
git commit -m "feat: add xxx"
git push -u origin feature/xxx
```

### 2.12 Full example

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

### 2.13 Update example

```bash
cd /d/XXX/XXX/XXX
git checkout docs/git-guide
git status
git add .
git commit -m "docs: refine collaboration guide"
git push
```

---

## 3. FAQ

### 3.1 Git is not installed

Common errors:

```text
git: command not found
```

or:

```text
'git' is not recognized as an internal or external command
```

Solution:

```bash
git --version
```

If the command is unavailable, install Git first and then reopen the terminal.

### 3.2 SSH is not configured correctly

Common errors:

```text
Permission denied (publickey)
fatal: Could not read from remote repository.
```

Solution:

#### Step 1: Check whether SSH keys already exist

```bash
ls ~/.ssh
```

#### Step 2: Generate SSH keys

```bash
ssh-keygen -t ed25519 -C "XXX@example.com"
```

If `ed25519` is unavailable:

```bash
ssh-keygen -t rsa -b 4096 -C "XXX@example.com"
```

#### Step 3: Check the public key

```bash
cat ~/.ssh/id_ed25519.pub
```

or:

```bash
cat ~/.ssh/id_rsa.pub
```

#### Step 4: Add the public key to the platform account

- GitHub: `Settings -> SSH and GPG keys -> New SSH key`
- Gitee: `Settings -> Security -> SSH Public Keys`
- GitCode: `Profile Settings -> Security / SSH Key Management`

#### Step 5: Test the connection

```bash
ssh -T git@github.com
ssh -T git@gitee.com
ssh -T git@gitcode.com
```

### 3.3 No repository permission

Common errors:

```text
You are not allowed to push code to this project
```

or:

```text
Permission to XXX/XXX.git denied to XXX
```

Solution:

- contact the repository administrator or project maintainer
- confirm whether your account has write access
- retry after permission is granted

```bash
git push -u origin feature/xxx
```

### 3.4 `src refspec XXX does not match any`

Common errors:

```text
error: src refspec XXX does not match any
error: failed to push some refs
```

Solution:

```bash
git branch
git status
git add .
git commit -m "docs: add content"
git push -u origin docs/xxx
```

### 3.5 Files were modified on `main` by mistake

If you have not committed yet:

```bash
git checkout -b docs/xxx
```

If you already committed to `main`:

- stop further operations
- contact the project maintainer
- do not continue direct development on `main`

### 3.6 Re-running `git clone` inside the repository directory

Correct usage:

```bash
cd ..
git clone git@github.com:XXX/XXX.git
```

### 3.7 Typing the repository URL directly as a command

Wrong:

```bash
git@github.com:XXX/XXX.git
```

Correct:

```bash
git clone git@github.com:XXX/XXX.git
```

### 3.8 When should Pull Requests and Issues be used

#### Pull Request is suitable when:

- code is ready to merge into the target branch
- code review is required
- team approval is required before merging

#### Issue is suitable when:

- tracking bugs
- tracking feature requests
- managing documentation tasks
- preserving discussions

Suggested order:

```text
Issue -> Branch -> Commit -> Push -> Pull Request
```

---

## 4. About Me

### License

This project is licensed under the Apache License 2.0. See LICENSE for details.

### Maintainer

Yoloong (倪家诚) focuses on HarmonyOS / ArkUI application development, AI capability integration, full-stack web engineering, and agent-oriented system building. His work spans the full implementation path of a software project, including product-facing UI development, backend services, API integration, deployment, and iterative delivery. Current projects mainly center on smart healthcare, intelligent interaction, productivity tools, and scenario-driven software systems. More work and ongoing projects can be found at yoloong.com and harmonycare.cn.
