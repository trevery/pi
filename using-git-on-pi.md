# using-git-on-pi


## 将本地仓库与远程仓库连接起来



### clone模式：从github上克隆一个仓库到本地

### push模式：将本地仓库连接到github同名仓库

clone模式虽然简单，但需要连接网络，登陆github。 push模式稍微有点麻烦，但是可以在没有网络的情况下，在本地事先建立git仓库，之后在有网络的条件下，将本地仓库连接到Github上。

假如，你在写一本小说，你很先进，用git来管理你的写作进程，仓库名为 myNovel。小说写了开头，你想把自己电脑上的小说库放到Github上，进行社会化写作，让别人给你更多的建议。

1. 登陆Github，创建同名仓库，myNovel。注意，一定不要勾选`Initialize this repository with a README`选项。 避免Gihub端的仓库从创建之初便与本地仓库失去了整合性。

2. 复制获取Github 端的仓库地址 `git@github.com:your-user-name/myNovel.git`。其中your-user-name为你的Github用户名。之后在本地myNovel下，使用如下命令

```bash
$ git remote add origin git@github.com:your-user-name/myNovel.git
```
其中origin是该远程仓库的名称（标识符），按理说origin可以随意取名，比如github-origin，或者gitlab-origin。这样，假如你添加了不止一个远程仓库，可以使用远程仓库的名称来区分。不过，按照习惯，一般在远程仓库只有一个的情况下，将其命名为`origin`。

3. 当想要将本地内容推送到远程仓库的时候，使用以下命令

```bash
$ git push -u origin master
```

该命令将本地库的内容，推送到名为远程仓库origin的master分支下。-u 参数可以将远程仓库origin 的master分支设置为本地仓库当前分支的上游（upstream）。这样在以后使用git pull命令从远程仓库获取内容时，可以免去另外添加参数的麻烦，直接从远程仓库origin 的master 分支获取内容。

