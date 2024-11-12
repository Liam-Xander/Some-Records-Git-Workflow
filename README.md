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
   - 这样，你的最新代码和标签都将被上传到远程仓库。
     
**删除本地标签**
   - 如果需要，可以在本地删除标签：
     ```bash
     git tag -d v8.0
     ```

---

## 进入想要上传一个新文件夹的终端下

1. **新建并初始化仓库**
   ```bash
   git init
   ```

2. **将文件夹内的所有文件都添加到仓库中，如果缺少哪个，可以使用 git add XXXX 添加；**
     ```bash
     git add .
     ```

3. **上传文件至本地仓库， -m之后的输入是本次提交的说明。**
     ```bash
     git commit -m "first commit"
     ```

4. **创建主分支**
   ```bash
   git branch -M main
   ```

5. **关联 GitHub 仓库,将本地文件夹和github仓库关联，后面是自己之前新建的github仓库地址**
     ```bash
     git remote add origin https://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@github.com/Liam-Xander/RMM-FUEL.git
     git remote add origin https://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@github.com/Liam-Xander/predict_based_rmmfastplanner.git
     ```

   - 其中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是令牌，@github.com/Liam-Xander/Multi-Fast.git是上传仓库

   - 如果出现fatal:远程origin已经存在则
     ```bash
     git remote remove origin
     ```

6. **推送到远程仓库**
   - 推送文件到远程仓库的主分支：
     ```bash
     git push -u origin main
     ```
   - 如果执行这句命令出现：fatal: 无法读取远程仓库   就再执行一遍
     ```bash
      git remote add origin https://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@github.com/Liam-Xander/RMM-FastPlanner.git
     ```
   - 然后
      ```bash
     git push -u origin main
     ```
   - 就行了。

---

## 添加文件方案

- **如果像我一样需要添加文件夹，输入：**
  ```bash
  git add /home/lxyu/fastplanner_ws/src/Fast-Planner/README2.md
  ```
- **后面为需要的文件夹路径**

  ```bash
  git commit -m "add another readme"
  git branch -M main
  git remote add origin https://Liam-Xander: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@github.com/Liam-Xander/Multi-Fast.git
  ```
  
- **如果输出fatal:远程origin已经存在，这会是添加文件，就不需要git remote remove origin了直接下面：**

  ```bash
  git push -u origin main
  ```

---

## 更新文件方案

1. **拉取远程更改：**
   - 提示：更新被拒绝，因为远程仓库包含您本地尚不存在的提交。这通常是因为另外
   - 提示：一个仓库已向该引用进行了推送。再次推送前，您可能需要先整合远程变更
   - 需要从远程仓库拉取最新的更改，并将其与本地分支合并：：
     ```bash
     git pull origin main
     ```
   - 这一步会将远程仓库的最新改动拉取到本地，并尝试自动合并。如果在这个过程中没有冲突，Git 会自动完成合并。如果有冲突，您需要手动解决冲突。

2. **解决冲突（如果有）：**
   - 如果 `README.md` 文件有冲突，Git 会提示您手动解决冲突。找到冲突标记（如 `<<<<<<`, `======`, `>>>>>>`），然后编辑冲突文件，保留您想要保留的内容。
   - 编辑完成后，保存文件并标记冲突已经解决：
     ```bash
     git add README.md
     ```

3. **重新提交并推送：**
   - 完成合并或解决冲突后，重新提交改动并推送到远程仓库：
     ```bash
     git commit -m "Update README"
     git push origin main
     ```
   - 这样，您就可以将本地的 README.md文件更新推送到 GitHub 上了。
   - 如果在合并过程中没有冲突，您可以直接进行推送：
     ```bash
     git push origin main
     ```
   - 这样就可以成功将本地的更改推送到远程仓库。
---

## 更新整个项目

1. **添加所有更改并提交：**
   ```bash
   git add .
   ```
2. **上传文件至本地仓库， -m之后的输入是本次提交的说明：**
   ```bash
   git commit -m "fix some problems"
   ```
3. ** **
   ```bash
   git branch -M main
   ```
4. **将本地文件夹和github仓库关联，后面是自己之前新建的github仓库地址**
   ```bash
   git remote add origin https://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@github.com/Liam-Xander/RMM-FUEL.git
   ```
   ```bash
   git remote add origin https://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@github.com/Liam-Xander/RMM-FUEL.git
   ```
- 其中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是令牌，@github.com/Liam-Xander/Multi-Fast.git是上传仓库

- 如果fatal:远程origin已经存在则
     ```bash
   git remote remove origin
   ```
5. ** **
   ```bash
   git push -u origin main
   ```
- 如果执行这句命令出现：fatal: 无法读取远程仓库   就再执行一遍
   ```bash
   git remote add origin https://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@github.com/Liam-Xander/RMM-FastPlanner.git
   ```
- 然后git push -u origin main就行了。

---
