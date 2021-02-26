# git学习笔记

## 基本命令

1. 下载并安装git，==git config --list==查看基本配置
2. 配置基本信息（用户名和密码）：==git config --global user.name="rostiute"== / ==git config --global user.email "179730897@qq.com"==
3. 初始化仓库：==git init==
4. 查看仓库状态：==git status==
5. 把文件放入暂存区 ==git add 文件名==或者==git add .==，点表示把当前文件夹下的所有问价都放入暂存区。
6. 提交版本：==git commit -m "描述"==
7. 查看日志：==git log==  查看全部日志：==git log -p==,按Q退出编辑状态。
8. 退回一步：==git reset==
9. 回退到某一个版本：==git reset 62e57ccd043aa6d4d01097e974f850315c1a0989 --hard==
10. 退后到某一个版本后,最初的版本：==git reflog 哈希值 --hard==
11. 比较工作区与暂存区文件状态的差异： ==git diff==

## 分支

1. ==git checkout -d== '分支名称'： 创建并切换到新的分支
2. ==git checkout== '分支名称'：切换分支
3. ==git branch== :查看分支
4. ==git checkout -b 'developer' 'master'==： 创建一个跟master一样的分支，取名为developer
5. ==git merge '分支名称'==：合并分支
6. ==git branch '分支名称'==：创建新的分支
7. 暂存区的意义：创建索引、文件分类

## 工作流程

1. 开工前在自己对应的分支下pull（拉取主分支的代码）
2. 当天结束之后push（推送）到自己对应的远程分支