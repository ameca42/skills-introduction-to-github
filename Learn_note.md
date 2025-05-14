# git学习笔记

| 参考[git教程](https://liaoxuefeng.com/books/git/introduction/index.html)

## 常用命令

**常用 Git 命令**

*   **git init**: 初始化一个新的 Git 仓库。
*   **git clone**: 从远程仓库克隆一个仓库到本地。
*   **git add**: 将文件添加到暂存区。
*   **git commit**: 将暂存区的文件提交到本地仓库。
*   **git push**: 将本地仓库的提交推送到远程仓库。
*   **git pull**: 从远程仓库拉取更新到本地仓库。
*   **git branch**: 创建、列出或删除分支。
*   **git checkout**: 切换到不同的分支。
*   **git merge**: 将一个分支的更改合并到另一个分支。
*   **git log**: 查看提交历史。
*   **git status**: 查看仓库状态。
*   **git diff**: 比较文件的差异。
*   **git reset**: 将当前分支重置到指定的提交。
*   **git revert**: 撤销指定的提交。

**常用场景下的使用流程**

1.  **创建新的 Git 仓库**

    *   在本地创建一个新的目录。
    *   使用 `git init` 命令将该目录初始化为一个 Git 仓库。
2.  **克隆远程仓库**

    *   使用 `git clone <远程仓库地址>` 命令将远程仓库克隆到本地。
3.  **修改文件并提交**

    *   修改本地文件。
    *   使用 `git add <文件名>` 命令将修改后的文件添加到暂存区。
    *   使用 `git commit -m "提交说明"` 命令将暂存区的文件提交到本地仓库。
4.  **推送到远程仓库**

    *   使用 `git push origin <分支名>` 命令将本地仓库的提交推送到远程仓库。
5.  **从远程仓库拉取更新**

    *   使用 `git pull origin <分支名>` 命令从远程仓库拉取更新到本地仓库。
6.  **创建和切换分支**

    *   使用 `git branch <分支名>` 命令创建一个新的分支。
    *   使用 `git checkout <分支名>` 命令切换到指定的分支。
7.  **合并分支**

    *   切换到要合并到的目标分支。
    *   使用 `git merge <要合并的分支名>` 命令将指定分支的更改合并到当前分支。
8.  **解决冲突**

    *   如果在合并分支时发生冲突，需要手动解决冲突。
    *   解决冲突后，使用 `git add <文件名>` 命令将解决后的文件添加到暂存区。
    *   使用 `git commit -m "提交说明"` 命令提交解决冲突后的更改。

**示例：**

开发一个名为 "my\_project" 的项目，并且你想要使用 Git 来管理你的代码。

1.  **创建本地仓库：**

    ```bash
    mkdir my_project
    cd my_project
    git init
    ```
2.  **创建并切换到新分支:**

    ```bash
    git branch feature/new-feature
    git checkout feature/new-feature
    ```
3.  **进行一些更改，暂存并提交：**

    ```bash
    # 修改一些文件
    git add .
    git commit -m "Implement new feature"
    ```
4.  **推送到远程仓库：**

    ```bash
    git push origin feature/new-feature
    ```

## 常见的使用场景
几个完整的使用场景教程，包括如何配合 GitHub 使用，以及如何为已有项目做贡献：

**场景 1：创建新项目并上传到 GitHub**

1.  **在本地创建项目目录：**

    ```bash
    mkdir my_new_project
    cd my_new_project
    ```
2.  **初始化 Git 仓库：**

    ```bash
    git init
    ```
3.  **创建并编辑项目文件：**

    ```bash
    # 例如，创建一个 README.md 文件
    echo "# My New Project" > README.md
    ```
4.  **添加文件到暂存区：**

    ```bash
    git add README.md
    ```
5.  **提交更改：**

    ```bash
    git commit -m "Initial commit: Add README.md"
    ```
6.  **在 GitHub 上创建新的仓库：**

    *   登录 GitHub。
    *   点击 "+" -> "New repository"。
    *   填写仓库名称、描述等信息。
    *   选择 "Create repository"。
    *   **注意：** 不要勾选 "Initialize this repository with a README"。
7.  **将本地仓库关联到 GitHub 仓库：**

    *   复制 GitHub 仓库的 "HTTPS" 或 "SSH" 地址。
    *   在本地仓库中执行以下命令（将 `<your_github_repo_url>` 替换为实际的 URL）：

        ```bash
        git remote add origin <your_github_repo_url>
        ```
8.  **将本地仓库推送到 GitHub：**

    ```bash
    git push -u origin main
    ```

    *   如果提示错误，可能需要先执行 `git pull origin main`，解决冲突后再推送。

**场景 2：参与 GitHub 上的开源项目**

1.  **Fork 目标仓库：**

    *   在 GitHub 上找到你想要贡献的开源项目。
    *   点击 "Fork" 按钮，将仓库复制到你自己的 GitHub 账户下。
2.  **克隆 Fork 后的仓库到本地：**

    ```bash
    git clone <your_forked_repo_url>
    cd <project_directory>
    ```
3.  **添加原始仓库作为 upstream：**

    ```bash
    git remote add upstream <original_repo_url>
    ```

    *   这样可以方便地从原始仓库获取最新的更新。
4.  **创建并切换到新分支：**

    ```bash
    git checkout -b feature/my-contribution
    ```
5.  **进行更改并提交：**

    ```bash
    # 修改代码...
    git add .
    git commit -m "Implement feature/fix: My contribution"
    ```
6.  **将本地分支推送到你的 GitHub 仓库：**

    ```bash
    git push origin feature/my-contribution
    ```
7.  **创建 Pull Request：**

    *   在你的 GitHub 仓库页面上，切换到 `feature/my-contribution` 分支。
    *   点击 "Compare & pull request" 按钮。
    *   填写 Pull Request 的标题和描述，说明你的更改。
    *   点击 "Create pull request"。

**场景 3：团队协作开发**

1.  **克隆远程仓库：**

    ```bash
    git clone <remote_repo_url>
    cd <project_directory>
    ```
2.  **创建并切换到新分支：**

    ```bash
    git checkout -b feature/new-feature
    ```
3.  **进行更改并提交：**

    ```bash
    # 修改代码...
    git add .
    git commit -m "Implement new feature"
    ```
4.  **拉取远程仓库的最新更改：**

    ```bash
    git pull origin main
    ```

    *   解决可能出现的冲突。
5.  **将本地分支推送到远程仓库：**

    ```bash
    git push origin feature/new-feature
    ```
6.  **创建 Pull Request：**

    *   通知团队成员进行代码审查。
    *   根据审查意见进行修改。
    *   合并 Pull Request 到主分支。

**一些建议：**

*   **保持本地仓库与远程仓库同步：** 经常使用 `git pull` 命令。
*   **编写清晰的提交信息：** 好的提交信息可以帮助其他人理解你的更改。
*   **使用分支进行开发：** 避免直接在主分支上进行更改。
*   **及时解决冲突：** 冲突越早解决越容易。
*   **阅读项目的贡献指南：** 许多开源项目都有自己的贡献指南，请务必阅读并遵守。

## git 回退
 Git 中回滚代码的几种常见方法，以及详细的教程：

**场景 1：回滚到之前的某个提交（commit）**

这种方法会撤销你指定的提交之后的所有提交，并将你的代码库恢复到那个提交的状态。

1.  **查看提交历史：**

    ```bash
    git log --oneline
    ```

    *   找到你想要回滚到的目标提交的 commit ID（一串短哈希值）。
2.  **使用 `git reset` 命令进行回滚：**

    *   **`git reset --hard <commit_id>`**：这是最常用的方式。它会完全移除指定 commit 之后的所有 commit，并且会修改你的工作目录和暂存区。**请谨慎使用，因为这会丢失你的更改。**

        ```bash
        git reset --hard <commit_id>
        ```

    *   **`git reset --mixed <commit_id>`**：这个命令会将 HEAD 指向指定的 commit，并且会重置暂存区，但是会保留工作目录中的更改。这意味着你的更改还在，但是你需要重新 `add` 和 `commit` 它们。这是默认行为，如果不指定 `--hard`，则默认使用 `--mixed`。

        ```bash
        git reset --mixed <commit_id>
        ```

    *   **`git reset --soft <commit_id>`**：这个命令会将 HEAD 指向指定的 commit，并且会保留暂存区和工作目录中的更改。这意味着你的更改还在，并且已经暂存，你只需要重新 `commit` 它们。

        ```bash
        git reset --soft <commit_id>
        ```
3.  **强制推送到远程仓库（如果需要）：**

    *   如果你已经将更改推送到了远程仓库，你需要强制推送才能使远程仓库也回滚到相同的状态。**请谨慎使用，因为这会覆盖远程仓库的历史记录，可能会影响其他人的工作。**

        ```bash
        git push origin <branch_name> --force
        ```

**场景 2：撤销最近的一次提交（commit）**

如果你只是想撤销最近的一次提交，可以使用 `git revert` 命令。

1.  **使用 `git revert HEAD` 命令：**

    ```bash
    git revert HEAD
    ```

    *   这会创建一个新的提交，该提交会撤销最近一次提交的更改。
    *   `git revert` 不会修改历史记录，而是通过创建一个新的提交来撤销之前的提交。
2.  **推送到远程仓库：**

    ```bash
    git push origin <branch_name>
    ```

**场景 3：撤销对某个文件的修改**

如果你只是想撤销对某个文件的修改，可以使用 `git checkout` 命令。

1.  **使用 `git checkout <file_name>` 命令：**

    ```bash
    git checkout <file_name>
    ```

    *   这会将文件恢复到最近一次提交的状态。
    *   **注意：** 这会覆盖你对该文件的所有未提交的更改。

**场景 4：放弃暂存区的更改**

如果你只是想放弃暂存区的更改，可以使用 `git restore --staged` 命令。

1.  **使用 `git restore --staged <file_name>` 命令：**

    ```bash
    git restore --staged <file_name>
    ```

    *   这会将文件从暂存区移除，但会保留工作目录中的更改。

**总结：**

*   `git reset`：用于回滚到之前的某个提交，会修改历史记录。
*   `git revert`：用于撤销最近的一次提交，会创建一个新的提交来撤销之前的提交，不修改历史记录。
*   `git checkout`：用于撤销对某个文件的修改。
*   `git restore --staged`：用于放弃暂存区的更改。

**选择哪种方法取决于你的具体需求：**

*   如果你想完全移除一些提交，并且不介意修改历史记录，可以使用 `git reset --hard`。
*   如果你想撤销最近的一次提交，并且不想修改历史记录，可以使用 `git revert`。
*   如果你只是想撤销对某个文件的修改，可以使用 `git checkout`。
*   如果你只是想放弃暂存区的更改，可以使用 `git restore --staged`。

**重要提示：**

*   在执行任何回滚操作之前，请务必备份你的代码。
*   在强制推送之前，请务必与团队成员沟通，确保不会影响其他人的工作。
*   理解每种回滚方法的含义和影响，选择最适合你的方法。

## git 分支管理

 Git 分支管理的详细说明：

**什么是分支？**

在 Git 中，分支是指向提交历史中某个特定提交的可变指针。可以把分支想象成一条独立的开发线，允许你在不影响主线（通常是 `main` 或 `master` 分支）的情况下进行实验、开发新功能或修复 Bug。

**为什么使用分支？**

*   **并行开发：** 允许多个开发人员同时在不同的功能或修复上工作，而不会相互干扰。
*   **功能开发：** 可以创建一个专门用于开发新功能的分支，完成开发后再合并到主分支。
*   **Bug 修复：** 可以创建一个专门用于修复 Bug 的分支，修复完成后再合并到主分支。
*   **版本控制：** 可以创建不同的分支来维护不同的版本。
*   **实验性开发：** 可以在一个分支上进行实验性开发，如果实验失败，可以轻松地删除该分支，而不会影响主分支。

**常用分支管理命令**

*   **`git branch`**: 列出本地分支。

    *   `git branch -r`: 列出远程分支。
    *   `git branch -a`: 列出所有分支（包括本地和远程）。
    *   `git branch <branch_name>`: 创建一个新分支。
*   **`git checkout`**: 切换到不同的分支。

    *   `git checkout <branch_name>`: 切换到指定的分支。
    *   `git checkout -b <branch_name>`: 创建并切换到新分支（相当于 `git branch <branch_name>` + `git checkout <branch_name>`）。
*   **`git merge`**: 将一个分支的更改合并到另一个分支。

    *   `git merge <branch_name>`: 将指定分支的更改合并到当前分支。
*   **`git branch -d <branch_name>`**: 删除本地分支。

    *   `git branch -D <branch_name>`: 强制删除本地分支（即使该分支尚未合并）。
*   **`git push origin --delete <branch_name>`**: 删除远程分支。
*   **`git pull`**: 从远程仓库拉取更新到本地仓库。
*   **`git push`**: 将本地仓库的提交推送到远程仓库。

**分支管理策略**

*   **Git Flow:** 一种流行的分支管理模型，定义了 `main`（或 `master`）、`develop`、`feature`、`release` 和 `hotfix` 等分支的用途和交互方式。
*   **GitHub Flow:** 一种更简单的分支管理模型，只有一个 `main`（或 `master`）分支和多个 `feature` 分支。
*   **GitLab Flow:** 一种更灵活的分支管理模型，可以根据项目的需求进行定制。

**常用分支管理流程**

1.  **创建新分支：**

    *   从 `main`（或 `master`）分支创建一个新的 `feature` 分支。

        ```bash
        git checkout main
        git pull origin main # 确保本地 main 分支是最新的
        git checkout -b feature/new-feature
        ```
2.  **在 `feature` 分支上进行开发：**

    *   修改代码、添加文件、提交更改。

        ```bash
        # 修改代码...
        git add .
        git commit -m "Implement new feature"
        ```
3.  **定期将 `main` 分支的更改合并到 `feature` 分支：**

    *   这可以避免 `feature` 分支与 `main` 分支的差异过大，减少合并冲突的可能性。

        ```bash
        git checkout feature/new-feature
        git pull origin main
        ```

    *   解决可能出现的冲突。
4.  **将 `feature` 分支推送到远程仓库：**

    ```bash
    git push origin feature/new-feature
    ```
5.  **创建 Pull Request：**

    *   在 GitHub 上创建一个 Pull Request，请求将 `feature` 分支合并到 `main` 分支。
    *   团队成员进行代码审查。
    *   根据审查意见进行修改。
6.  **合并 Pull Request：**

    *   如果代码审查通过，将 `feature` 分支合并到 `main` 分支。
7.  **删除 `feature` 分支：**

    *   合并完成后，可以删除 `feature` 分支。

        ```bash
        git branch -d feature/new-feature # 删除本地分支
        git push origin --delete feature/new-feature # 删除远程分支
        ```

**解决冲突**

当多个分支修改了同一文件的同一部分时，就会发生冲突。解决冲突的步骤如下：

1.  **查看冲突文件：**

    *   使用 `git status` 命令查看哪些文件存在冲突。
2.  **手动解决冲突：**

    *   打开冲突文件，找到包含 `<<<<<<<`、`=======` 和 `>>>>>>>` 的部分。
    *   手动编辑文件，选择要保留的更改，删除冲突标记。
3.  **将解决后的文件添加到暂存区：**

    ```bash
    git add <file_name>
    ```
4.  **提交更改：**

    ```bash
    git commit -m "Resolve conflict"
    ```

**总结**

分支管理是 Git 中非常重要的一个概念，它可以帮助你更好地组织和管理你的代码。通过合理地使用分支，你可以提高开发效率、降低风险，并更好地进行团队协作。


