# Github的SSH密钥设定

### 1. 检查网络连接

确保你的网络连接稳定。如果网络不稳定，大文件的上传可能会被中断或延迟。

### 2. 增加 Git 的传输缓冲区大小

大文件上传时可以增加 Git 的传输缓冲区大小，来改善上传速度：

```sh
git config --global http.postBuffer 524288000
```

这会将缓冲区大小设置为 500MB。

### 3. 使用 SSH 进行上传

如果 HTTPS 上传较慢，可以尝试使用 SSH 进行上传：

1. **生成 SSH 密钥**（如果尚未生成）：

    ```sh
    ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
    ```

2. **添加 SSH 密钥到 SSH 代理**：

    ```sh
    eval "$(ssh-agent -s)"
    ssh-add ~/.ssh/id_rsa
    ```

3. **将 SSH 公钥添加到 GitHub**：

    - 复制公钥到剪贴板：

        ```sh
        pbcopy < ~/.ssh/id_rsa.pub
        ```

    - 登录到 GitHub，进入 `Settings` -> `SSH and GPG keys` -> `New SSH key`，将公钥粘贴进去。

4. **更改远程仓库 URL 为 SSH**：

    ```sh
    git remote set-url origin git@github.com:Republic1024/Automode_LoRA.git
    ```

5. **再次推送**：

    ```sh
    git push -u origin main
    ```

### 4. 检查是否存在上传进度

如果上传过程中没有任何进展，可以尝试中断上传并重新开始：

```sh
# 中断当前上传
Ctrl + C

# 再次尝试推送
git push -u origin main
```

### 5. 使用 GitHub 大文件存储 (Git LFS)

如果你的项目包含大文件或二进制文件，建议使用 Git LFS (Large File Storage)：

1. **安装 Git LFS**：

    ```sh
    brew install git-lfs
    git lfs install
    ```

2. **跟踪大文件**：

    ```sh
    git lfs track "*.bin"  # 替换为实际文件类型
    ```

3. **添加并提交文件**：

    ```sh
    git add .gitattributes
    git add .
    git commit -m "Add large files"
    ```

4. **推送到远程仓库**：

    ```sh
    git push -u origin main
    ```

### 总结

在大文件上传过程中可能会遇到一些问题，以下是一些常见的解决方案：

1. **增加 Git 的传输缓冲区大小**：

    ```sh
    git config --global http.postBuffer 524288000
    ```

2. **使用 SSH 进行上传**：

    ```sh
    ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
    eval "$(ssh-agent -s)"
    ssh-add ~/.ssh/id_rsa
    pbcopy < ~/.ssh/id_rsa.pub  # 复制公钥到剪贴板
    # 在 GitHub 添加公钥
    git remote set-url origin git@github.com:Republic1024/Automode_LoRA.git
    git push -u origin main
    ```

3. **使用 GitHub 大文件存储 (Git LFS)**：

    ```sh
    brew install git-lfs
    git lfs install
    git lfs track "*.bin"  # 替换为实际文件类型
    git add .gitattributes
    git add .
    git commit -m "Add large files"
    git push -u origin main
    ```

希望这些方法能够帮助你顺利将本地文件上传到 GitHub。