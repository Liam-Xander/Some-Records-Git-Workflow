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
   - 将提交的最新代码推送到远程仓库对应的分支上，例如 `main2` 或 `v7.0`：
     ```bash
     git push origin main2  # 或者 git push origin v7.0
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
```bash
/*---------------------------step 1.-----------------------------*/
(base) lxyu@lxyu-Inspiron-7501:~/rmmfastplanner/src/Fast-Planner$ git push origin main
To https://github.com/Liam-Xander/predict_based_rmmfastplanner.git
 ! [rejected]        main -> main (non-fast-forward)
error: 无法推送一些引用到 'https://密钥@github.com/Liam-Xander/predict_based_rmmfastplanner.git'
提示：更新被拒绝，因为您当前分支的最新提交落后于其对应的远程分支。
提示：再次推送前，先与远程变更合并（如 'git pull ...'）。详见
提示：'git push --help' 中的 'Note about fast-forwards' 小节。
/*---------------------------step 2.-----------------------------*/
(base) lxyu@lxyu-Inspiron-7501:~/rmmfastplanner/src/Fast-Planner$ git pull origin main
remote: Enumerating objects: 14, done.
remote: Counting objects: 100% (14/14), done.
remote: Compressing objects: 100% (14/14), done.
error: RPC failed; curl 18 transfer closed with outstanding read data remaining
fatal: The remote end hung up unexpectedly
fatal: early EOF
fatal: unpack-objects 失败
/*---------------------------step 3.-----------------------------*/
(base) lxyu@lxyu-Inspiron-7501:~/rmmfastplanner/src/Fast-Planner$ git config --global http.postBuffer 524288000
(base) lxyu@lxyu-Inspiron-7501:~/rmmfastplanner/src/Fast-Planner$ git pull origin main
remote: Enumerating objects: 14, done.
remote: Counting objects: 100% (14/14), done.
remote: Compressing objects: 100% (14/14), done.
remote: Total 14 (delta 5), reused 1 (delta 0), pack-reused 0 (from 0)
展开对象中: 100% (14/14), 完成.
来自 https://github.com/Liam-Xander/predict_based_rmmfastplanner
 * branch            main       -> FETCH_HEAD
   441f8c5..1143911  main       -> origin/main
Merge made by the 'recursive' strategy.
 README.md                | 291 +++-------------------------------------------------------------
 files/predict.gif        | Bin 0 -> 15577113 bytes
 files/withoutpredict.gif | Bin 0 -> 19219951 bytes
 3 files changed, 11 insertions(+), 280 deletions(-)
 create mode 100644 files/predict.gif
 create mode 100644 files/withoutpredict.gif

/*---------------------------step 4.-----------------------------*/
然后从头开始git add .往后继续就行
```
`or`
```bash
(base) lxyu@lxyu-Inspiron-7501:~/rmmfastplanner/src/Fast-Planner$ git push origin main
To https://github.com/Liam-Xander/predict_based_rmmfastplanner.git
 ! [rejected]        main -> main (fetch first)
error: 无法推送一些引用到 'https://ghp_密钥@github.com/Liam-Xander/predict_based_rmmfastplanner.git'
提示：更新被拒绝，因为远程仓库包含您本地尚不存在的提交。这通常是因为另外
提示：一个仓库已向该引用进行了推送。再次推送前，您可能需要先整合远程变更
提示：（如 'git pull ...'）。
提示：详见 'git push --help' 中的 'Note about fast-forwards' 小节。
(base) lxyu@lxyu-Inspiron-7501:~/rmmfastplanner/src/Fast-Planner$ git pull --rebase 
remote: Enumerating objects: 13, done.
remote: Counting objects: 100% (13/13), done.
remote: Compressing objects: 100% (13/13), done.
remote: Total 13 (delta 6), reused 0 (delta 0), pack-reused 0 (from 0)
展开对象中: 100% (13/13), 完成.
来自 https://github.com/Liam-Xander/predict_based_rmmfastplanner
   5e58ebd..55dc62d  main       -> origin/main
首先，回退分支以便在上面重放您的工作...
应用：1120stable version record and comment extractSurfacePointsWithBoundary and 200

-----------然后就git push origin main

```


---------------------------------------
      ```bash
      wsl --shutdown 
      wsl --list --running # 确保wsl完全关闭
      wsl  # 启动
      
      
      nhy@LAPTOP-C24LBKAL:~$ ifconfig
      eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
              inet 192.168.12.149  netmask 255.255.255.0  broadcast 192.168.12.255
      
      nhy@LAPTOP-C24LBKAL:~$ ip route
      default via 192.168.12.139 dev eth0
      192.168.12.0/24 dev eth0 proto kernel scope link src 192.168.12.149
      
      IP 地址： 192.168.12.149
      子网： 192.168.12.0/24
      默认网关： 192.168.12.139
      ```

1. 测试默认网关连通性
操作： 执行 ping 192.168.12.139
目的： 检查是否能与默认网关通信。如果网关无法ping通，说明局域网内部就有连接问题，可能需要检查路由器或网络线缆问题。
2. 测试外部网络连接
操作： 如果网关ping通，再尝试 ping 8.8.8.8
目的： 检查是否可以访问外部网络。如果能够ping通外部IP，则说明网络连接正常；如果依然无法ping通，问题可能出在路由器或ISP连接上。

3.接下来测试域名解析：
尝试执行如下命令，检查 DNS 是否能正确解析域名：

      ```bash
      ping github.com
      nslookup github.com
      dig github.com
      ```

如果ping成功了，但是还是卡住
尝试先压缩
      ```bash
      git gc --aggressive
      ```
然后
      ```bash
      git push -u origin main
      ```
---------------------------------------------







## 创建新分支

1.查看当前分支
```bash
git status
```

2.在当前所在的 `master` 分支基础上创建新分支 `main2`

```bash
git checkout -b main2
```

这条命令首先会基于当前的 `master` 分支创建一个名为 `main2` 的新分支，然后自动切换到 `main2` 分支上。之后你就可以在 `main2` 分支上进行代码的修改、添加等操作，完成后记得提交更改并根据需要推送到远程仓库。例如，在 `main2` 分支上完成一些工作后：

3.执行：
```bash
git add.
git commit -m "在 main2 分支上的提交说明"
git push origin main2
```

这样就可以将 `main2` 分支的更改推送到远程仓库对应的 `main2` 分支上了（前提是远程仓库已经设置好并且你有相应的推送权限）。 

4. **创建带注释的标签**
   - 在项目目录（例如 `/predicted_ws/src/Fast-Planner`）下执行以下命令，创建一个带注释的标签：
     ```bash
     git tag -a v14.2 -m "全局障碍物不给1，预测版本latest."
     ```

5. **查看标签**
   - 确认标签是否已正确创建：
     ```bash
     git tag
     ```

6. **推送标签到远程仓库**
   - 将标签推送到远程仓库：
     ```bash
     git push origin v14.2
     ```
   - 这样，你的最新代码和标签都将被上传到远程仓库。
---
     
## 新设备中代码上传到已有仓库中
### 一、设置 Git 用户名和邮箱（若未设置）
如果在使用 Git 过程中出现因未设置用户名和邮箱导致的错误，可按如下步骤操作：
1. **设置全局用户名和邮箱**：
   运行以下命令来设置你的全局用户名和邮箱（请用你自己的真实信息替换示例中的内容）：
   ```bash
   git config --global user.name "Liam-Xander"
   git config --global user.email "2432485055@qq.com"
   ```
2. **检查配置是否生效**：
   设置后，使用以下命令检查配置是否正确：
   ```bash
   git config --global --list
   ```

### 二、初始化本地 Git 仓库并关联远程仓库（若尚未操作）
1. 进入你的项目目录：
   ```bash
   cd ~/predict/src/Fast-Planner
   ```
2. 初始化 Git（如果尚未初始化）：
   ```bash
   git init
   ```
3. 添加远程仓库：
   ```bash
   git remote add origin https://密钥@github.com/Liam-Xander/predict_based_rmmfastplanner_GTX1650.git
   ```

### 三、提交文件到本地仓库
1. **检查当前仓库的状态**：
   查看当前仓库的状态，确认是否有更改未提交。
   ```bash
   git status
   ```

   查看本地分支
      ```bash
      git branch
      ```
这个命令会列出所有本地的分支，并且当前所在的分支会有一个 * 标记。


要切换到名为 main2 的分支，您可以使用以下命令：
 ```bash
git checkout main3
 ```
如果 main2 分支还没有被创建，您可以先创建该分支并切换到它：
 ```bash
git checkout -b main3
 ```

3. **如果没有提交记录，先做一次提交**：
   - 添加所有文件：
     ```bash
     git add .
     ```
   - 提交文件并添加提交信息：
     ```bash
     git commit -m "1201version on Y9000P"
     ```

### 四、创建并推送标签
1. **创建标签**：
   提交后，就可以创建标签了：
   ```bash
   git tag -a Y9000P1.0 -m "1201version on Y9000P"
   ```
2. **推送标签到远程仓库**：
   如果标签创建成功，推送标签到远程仓库：
   ```bash
   git push origin Y9000P1.0
   ```

以上可完成从设置 Git 基本信息、初始化本地仓库并关联远程仓库，到提交文件和创建推送标签的一系列操作。

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
     git remote add origin https://密钥@github.com/Liam-Xander/RMM-FUEL.git
     git remote add origin https://密钥@github.com/Liam-Xander/predict_based_rmmfastplanner.git
     ```

   - 其中ghp_**************是令牌，@github.com/Liam-Xander/Multi-Fast.git是上传仓库

   - 如果出现fatal:远程origin已经存在则
     ```bash
     git remote remove origin
     ```

6. **推送到远程仓库**
   - 推送文件到远程仓库的主分支：
     ```bash
     git push -u origin main
     ```
   - 如果执行这句命令出现：fatal: 无法读取远程仓库
   - 第一种方式：多换几个热点，重新尝试就行
   - 第二种方式：就再执行一遍
     ```bash
      git remote add origin https://密钥@github.com/Liam-Xander/RMM-FastPlanner.git
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
  git remote add origin https://Liam-Xander:密钥@github.com/Liam-Xander/Multi-Fast.git
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
   git remote add origin https://密钥@github.com/Liam-Xander/RMM-FUEL.git
   ```
   ```bash
   git remote add origin https://密钥@github.com/Liam-Xander/RMM-FUEL.git
   ```
- 其中密钥是令牌，@github.com/Liam-Xander/Multi-Fast.git是上传仓库

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
   git remote add origin https://密钥@github.com/Liam-Xander/RMM-FastPlanner.git
   ```
- 然后git push -u origin main就行了。

---


## 以前仓库添加新分支
```bash
git init
git add .
nhy@LAPTOP-C24LBKAL:~/fuel_predict/src/RMM-FUEL$ git branch
* master
nhy@LAPTOP-C24LBKAL:~/fuel_predict/src/RMM-FUEL$ ^C
nhy@LAPTOP-C24LBKAL:~/fuel_predict/src/RMM-FUEL$ ^C
nhy@LAPTOP-C24LBKAL:~/fuel_predict/src/RMM-FUEL$ git branch main2
nhy@LAPTOP-C24LBKAL:~/fuel_predict/src/RMM-FUEL$ git branch
  main2
* master

nhy@LAPTOP-C24LBKAL:~/fuel_predict/src/RMM-FUEL$ git checkout main2
Switched to branch 'main2'
nhy@LAPTOP-C24LBKAL:~/fuel_predict/src/RMM-FUEL$ git branch              * main2
  master

nhy@LAPTOP-C24LBKAL:~/fuel_predict/src/RMM-FUEL$ git commit -m "1210 commit"
On branch main2
nothing to commit, working tree clean

nhy@LAPTOP-C24LBKAL:~/fuel_predict/src/RMM-FUEL$ git remote add origin https://密钥@github.com/Liam-Xander/RMM-FUEL.git

nhy@LAPTOP-C24LBKAL:~/fuel_predict/src/RMM-FUEL$ git push -u origin main2
Enumerating objects: 1530, done.
Counting objects: 100% (1530/1530), done.
Delta compression using up to 32 threads
Compressing objects: 100% (1433/1433), done.
Writing objects: 100% (1530/1530), 69.94 MiB | 4.32 MiB/s, done.
Total 1530 (delta 482), reused 0 (delta 0)
remote: Resolving deltas: 100% (482/482), done.
remote:
remote: Create a pull request for 'main2' on GitHub by visiting:
remote:      https://github.com/Liam-Xander/RMM-FUEL/pull/new/main2
remote:
To https://github.com/Liam-Xander/RMM-FUEL.git
 * [new branch]      main2 -> main2
Branch 'main2' set up to track remote branch 'main2' from 'origin'.
```
