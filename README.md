# Some-Records

---

# 上传不同版本的 Git 工作流程

## 提交和推送最新代码，并创建标签

1. **确保所有更改已添加并提交**
   - 在创建标签之前，确保所有更改已提交到本地仓库：
     ```bash
     git add .
     git commit -m "全局障碍物不给1，预测版本latest"
     ```

2. **推送最新代码到远程仓库**
   - 将提交的最新代码推送到远程仓库对应的分支上，例如 `main` 或 `v7.0`：
     ```bash
     git push origin main  # 或者 git push origin v7.0
     ```

3. **创建带注释的标签**
   - 在项目目录（例如 `/predicted_ws/src/Fast-Planner`）下执行以下命令，创建一个带注释的标签：
     ```bash
     git tag -a v14.2 -m "全局障碍物不给1，预测版本latest."
     ```

4. **查看标签**
   - 确认标签是否已正确创建：
     ```bash
     git tag
     ```

5. **推送标签到远程仓库**
   - 将标签推送到远程仓库：
     ```bash
     git push origin v14.2
     ```

6. **删除本地标签**
   - 如果需要，可以在本地删除标签：
     ```bash
     git tag -d v8.0
     ```

---

## 初始化新仓库并上传文件

1. **新建并初始化仓库**
   ```bash
   git init
   ```

2. **添加文件夹内的所有文件到仓库**
   - 如果缺少某些文件，可以使用 `git add 文件名` 添加单个文件：
     ```bash
     git add .
     ```

3. **提交文件到本地仓库**
   - `-m` 后输入提交说明：
     ```bash
     git commit -m "first commit"
     ```

4. **创建主分支**
   ```bash
   git branch -M main
   ```

5. **关联 GitHub 仓库**
   - 将本地文件夹与 GitHub 仓库关联，后面是 GitHub 仓库地址：
     ```bash
     git remote add origin https://ghp_令牌@github.com/Liam-Xander/RMM-FUEL.git
     ```

   - 如果出现 `fatal: 远程 origin 已经存在` 错误，可以移除已有的 `origin`：
     ```bash
     git remote remove origin
     ```

6. **推送到远程仓库**
   - 推送文件到远程仓库的主分支：
     ```bash
     git push -u origin main
     ```

---

## 添加文件方案

- **添加文件夹：**
  ```bash
  git add /home/lxyu/fastplanner_ws/src/Fast-Planner/README2.md
  ```

- **提交文件并推送：**
  ```bash
  git commit -m "add another readme"
  git push -u origin main
  ```

---

## 更新文件方案

1. **拉取远程更改：**
   - 如果提示远程仓库包含未同步的提交，请先拉取远程更新并合并：
     ```bash
     git pull origin main
     ```

2. **解决冲突（如果有）：**
   - 如果有冲突，找到冲突标记（如 `<<<<<<`, `======`, `>>>>>>`），解决后保存并标记解决完成：
     ```bash
     git add README.md
     ```

3. **重新提交并推送：**
   - 完成合并或解决冲突后，重新提交并推送更新：
     ```bash
     git commit -m "Update README"
     git push origin main
     ```

---

## 更新整个项目

1. **添加所有更改并提交：**
   ```bash
   git add .
   git commit -m "fix some problems"
   ```

2. **关联 GitHub 仓库（如未关联）：**
   ```bash
   git remote add origin https://ghp_令牌@github.com/Liam-Xander/RMM-FUEL.git
   ```

3. **推送到远程仓库：**
   ```bash
   git push -u origin main
   ```

---
