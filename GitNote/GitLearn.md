# Git 版本控制


## Git原理

### Git四个工作区域︰
+ 工作目录(Working Directory ) ：工作空间写代码的地方
+ 暂存区(Stage/Index) ：暂存区是一个文件,用于暂时存储你的改动
+ 资源库(Repository或Git Directory) 
+ 远程Git仓库(Remote Directory)

文件在这四个区域之间的转换关系如下∶

![avatar](/GitNote/Image/Git流程.png)
![avatar](/GitNote/Image/Git流程2.png)

### Git中文件的四种状态

版本控制就是对文件的版本控制，要对文件进行修改、提交等操作，首先要知道文件当前在什么状态，不然可能会提交了现在还不想提交的文件，或者要提交的文件没提交上。

+ **Untracked**：未跟踪,此文件在文件夹中,但并没有加入到git库,不参与版本控制.通过git add状态变为 staged
+ **Unmodify**：文件已经入库,未修改，即版本库中的文件快照内容与文件夹中完全一致.这种类型的文件有两种去处,如果它被修改,而变为_Modified .如果使用git rm移出版本库,则成为untracked文件
+ **Modified**：文件已修改,仅仅是修改,并没有进行其他的操作.这个文件也有两个去处,通过git add可进入暂存staged状态,使用git checkout则丢弃修改过，返回到unmodify状态,这个git checkout即从库中取出文件,覆盖当前修改!
+ **Staged**：暂存状态.执行git commit则将修改同步到库中,这时库中的文件和本地文件又变为一致，文件为unmodify状态.执行git reset HEAD filename取消暂存,文件状态为Modified


### Git中忽略一些文件

有些时候我们不想把某些文件纳入版本控制中，比如数据库文件，临时文件，设计文件等.

可以在主目录下建立 ".gitignore"文件，此文件有如下规则:

1. 忽略文件中的空行或以井号（#）开始的行将会被忽略。
2. 可以使用Linux通配符。例如∶星号(*)代表任意多个字符，问号(？)代表一个字符，方括号([abc])代表可选字符范围大括号( {string1,string2,...})代表可选的字符串等。
3. 如果名称的最前面有一个感叹号(!)，表示例外规则，将不被忽略。
4. 如果名称的最前面是一个路径分隔符(/ )，表示要忽略的文件在此目录下，而子目录中的文件不忽略。
5. 如果名称的最后面是一个路径分隔符(/)，表示要忽略的是此目录下该名称的子目录，而非文件（默认文件或目录都忽略)。

### Git中的免密码登录  使用SSH

1. 首先在git bash 中 输入 ssh-keygen [-t 加密协议(:rsa)] ,然后多按几次回车直到出现一个字符图。
2. 然后去用户目录下找到.ssh文件夹 里面有 id_rsa 和 id_rsa.pub 一个是私钥，一个是公钥，github需要的是公钥
3. 在GitHub上点击账户设置，点击SSH and GPG keys 点击 new SSH key 输入Title(标题) 然后
将.pub文件里的内容复制，然后粘贴到里面。点击完成






---

## 命令
``` bash
# 配置用户名和邮箱
git config --global user.name binbinku
git config --global user.email 2822230340@qq.com

#查看Git配置
git config --global -l; 全局配置
git config --system -l; 系统配置

# Git基础操作

git init 初始化本地仓库

git clone [url] 克隆远程仓库

git add filename | git add .  添加文件到暂存区(Index/Stage)

git commit [-m "message"]  将暂存区的文件提交到本地仓库(Repository),[-m] 表示显示提交信息

git push 将本地仓库的文件推送到远程仓库(Remote:GitHub,Gitee)

git status [filename] 查看某个文件的状态

git status 查看所有文件状态







```