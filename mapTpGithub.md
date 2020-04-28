# Map to github

## 将本地项目映射到 Github 仓库。



### 创建 github 远程仓库

- 登录 github 账户
- 填写信息(Reposotory name, description, public|private, init README.md)



### 创建工作区(电脑下的文件夹)

在(自己)指定位置下创建 git 项目。例如我在桌面创建 git 项目

```js
cd ~/desktop
// project_name (自己命名)项目名
mkdir <project_name>
```



我的 git 项目名为 git, 故 mkdir git



进入项目 git

```js
cd git
```



初始化 git 仓库(主要是形成 暂存区)

```js
git init
```



**理解下我们的提交与拉取流程**

```
(在电脑下编辑 =》 工作区) -(提交 commit)> (.git 记录列表)暂存区 -(push)> git 远程仓库

git 远程仓库 -(pull)> (.git 暂存区) -()> (电脑文件 merge)
```



创建新文件并编辑内容

```js
touch git/demo.js

// git/demo.js
// content: hello wolrd
```



查看 git 项目内部文件状态

```js
git status

// 由于我们新增 emo.js, 会出现以下提示
/*
  Untracked files
    use git add <file>
  demo.js
*/

```



提交并备注信息到暂存区(.git)

```js
// 提交到暂存区
git add .
// 或者 
git add demo.js 

// 备注信息
git commit -m '<info-desc>'
```



实现本地 git 项目与远程 git 仓库映射关系

```js
// git-package.git 远程仓库地址
git remote -u origin <git-package.git>
```



将本地 git 项目推送到 git 远程仓库

```js
git push -u origin master

// 可能出现的问题
// 1. git 远程存在 README.md 文件,而本地没有;两者存在差异导致以下提示

To https://github.com/XiaoYimi/git.git
 ! [rejected]        master -> master (fetch first)
error: failed to push some refs to 'https://github.com/XiaoYimi/git.git'

// 解决方案: 执行以下命令拉取远程仓库并合并文件
git pull --rebase origin master
// 再次推送到远程仓库
git push -u origin master

// 1. git 远程存在 README.md 文件,而本地也有 README.md 文件;两者内容存在差异导致以下提示

// 解决方案: 暂未遇到

```



