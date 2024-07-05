## 将本地文件夹上传到GitHub仓库的步骤

以下是将本地文件夹 `~/Downloads/其他相关材料/Automode_LoRA` 上传到 GitHub 仓库 `https://github.com/Republic1024/Automode_LoRA` 的详细步骤。

### 1. 创建 GitHub 仓库

1. 登录到 GitHub。
2. 创建一个新仓库，名称为 `Automode_LoRA`。
3. 复制仓库的 HTTPS URL，例如 `https://github.com/Republic1024/Automode_LoRA.git`。

### 2. 省流版

#### 第二版

##### 温柔上传（推荐）(可以只看这一个，剩下不用看)

```bash
# 初始化一个新的Git仓库
git init

# 将远程仓库添加为origin
git remote add origin https://github.com/Republic1024/TestRepo.git

# 从远程仓库的main分支拉取最新代码
git pull origin main

# 移除未跟踪的文件，例如.DS_Store（Mac系统生成的隐藏文件）
rm .DS_Store  

# 将所有更改添加到暂存区
git add .

# 提交暂存区的更改并添加提交信息
git commit -m "Initial commit or merge or rebase remote changes"

# 从远程仓库获取最新的提交
git fetch origin

# 将本地的main分支变基到远程main分支的最新提交
git rebase origin/main

# 将本地main分支的更改推送到远程main分支
git push origin main

```

##### 暴力上传

```bash
# 导航到本地文件夹
cd ~/Downloads/其他相关材料/Automode_LoRA

# 初始化 Git 仓库
git init

# 添加远程仓库
git remote add origin https://github.com/Republic1024/Automode_LoRA.git

rm .DS_Store  # 例如移除未跟踪的文件

# 添加所有文件到暂存区
git add .

# 创建初始提交
git commit -m "Initial commit"

# 推送到 GitHub 仓库
git push origin main -f
```

#### 第一版

```sh
# 导航到本地文件夹
cd ~/Downloads/其他相关材料/Automode_LoRA

# 初始化 Git 仓库
git init

# 添加远程仓库
git remote add origin https://github.com/Republic1024/Automode_LoRA.git

# 添加所有文件到暂存区
git add .

# 创建初始提交
git commit -m "Initial commit"

# 推送到 GitHub 仓库
git push origin main -f
```


### 2. 打开终端并导航到本地文件夹

```sh
cd ~/Downloads/其他相关材料/Automode_LoRA
```

### 3. 初始化本地 Git 仓库

```sh
git init
```

### 4. 添加远程仓库

```sh
git remote add origin https://github.com/Republic1024/Automode_LoRA.git
```

### 5. 添加所有文件到暂存区

```sh
git add .
```

### 6. 创建初始提交

```sh
git commit -m "Initial commit"
```

### 7. 推送到 GitHub 仓库

由于 GitHub 现在使用 Personal Access Token (PAT) 代替密码，确保你已经生成了一个 PAT，并替换 `<token>` 为你的实际 token。

```sh
git push -u origin main
```

如果遇到认证问题，可以使用以下命令设置远程 URL：

```sh
git remote set-url origin https://<token>@github.com/Republic1024/Automode_LoRA.git
```

然后再次推送：

```sh
git push origin main -f
```

### 8. 处理可能的冲突

如果推送时遇到错误提示 `Updates were rejected because the remote contains work that you do not have locally`，请按照以下步骤处理：

1. **拉取远程仓库最新内容并合并**

    ```sh
    git fetch origin
    git pull --rebase origin main
    ```

2. **解决可能的冲突**
   
    如果存在冲突，按照 Git 提示解决冲突后继续：

    ```sh
    git add <conflicted-files>
    git rebase --continue
    ```

3. **再次推送**

    ```sh
    git push -u origin main
    ```

## 总结

将本地文件夹上传到 GitHub 仓库的完整流程如下：

```sh
# 导航到本地文件夹
cd ~/Downloads/其他相关材料/Automode_LoRA

# 初始化 Git 仓库
git init

# 添加远程仓库
git remote add origin https://github.com/Republic1024/Automode_LoRA.git

# 添加所有文件到暂存区
git add .

# 创建初始提交
git commit -m "Initial commit"

# 推送到 GitHub 仓库
git push -u origin main
```

如遇认证问题：

```sh
# 设置远程 URL 包含 PAT
git remote set-url origin https://<token>@github.com/Republic1024/Automode_LoRA.git

# 再次推送
git push -u origin main
```

如遇冲突问题：

```sh
# 拉取远程仓库最新内容并合并
git fetch origin
git pull --rebase origin main

# 解决可能的冲突
git add <conflicted-files>
git rebase --continue

# 再次推送
git push -u origin main
```

以上步骤确保你的本地文件夹成功上传到 GitHub 仓库。