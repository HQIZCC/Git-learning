# 实验2 Git的使用
>
## 一、实验目的
1. 掌握git使用
2. 掌握使用Github作为元策划那个仓库

---

## 二、实验任务

1. 练习本地git操作
2. 用SSH同步本地与Github仓库

---

## 三、实验步骤与结果

要求一下结果截图

1. 本地操作log截图
2. Github上commits截图

### 一、实验步骤

1. 安装git（在安装的最后一步设置时，输入 
   git config-global user "HQIZCC"							               
   git config-global email "1358805979@qq.com"
2. 创建一个本地版本库，依次输入如下命令：
   cd /d d:
   mkdir CodeKu
   cd CodeKu
   git init
3. 创建一个CodeD.txt代码详情.txt文件
   用命令 git add CodeD.txt 将文件添加到仓库CodeKu								   
   用命令 git commit -m "a code ku"将文件提交到仓库CodeKu
4. 本地版本管理测试
   1. 首先修改CodeD.txt文本内容(此处增加：功能：1.介绍代码模块) 并保存。
      使用命令 git status 查看CodeKu库当前状态：结果显示如图：
      
      运行结果说明：CodeD.txt文本被修改过，但是没有提交。
   2. 确认无误后，使用命令 
      git add CodeD.txt
      git commit -m "add fuction 1
   3. 连续进行两次修改CodeD.txt文件内容，以增加更多的版本完成本次测试。
      依次添加，内容如下：
      
      
      注意：每次提交完成后记得使用 git add CodeD.txt 和git commit -m "修改内容”提交到本地仓库
      使用命令 git log --pretty=oneline 查看最近提交的日志，如下图：
      
      由此可见我们一个有了四次修改，也就是四个版本，接下来进行版本控制实验。
   4. 版本回退操作，使用git reset --hard HEAD~1 可以将版本回退到上一个版本，并且打开CodeD.txt文件查看该操作是否有效：实验截图如下：
      
      文本内容：
      		
   5. 接下来，使用reset 加commit id 回到某一版本实验。
      1. 首先查看将要回退的版本的commit id，比如说我们现在要回退到add functions 3 这个版本。步骤3 的git log 结果图，可以得到add function 3 的commit id 为3ca1d2a。
      2. 结合命令 git reset --hard 3ca1d2a即可回退到版本3，实验截图如下：
         
         
   6. 当我们在修改文件时，如果进行了连续修改，在某一次修改完成后，执行了git add 添加到仓库操作后，接下来又进行了修改，但是没有执行git add 添加到仓库修改，那么在下次的git commit -m“”提交到仓库操作，只会把第一次的内容提交上去，而第二次仍会处在暂存区：
      1. 第一次修改，并执行了git add 添加命令。
         
         执行 git add CodeD.txt操作：
         
      2. 第二次修改，不执行git add 添加命令：
         
      3. 执行 git commit -m "panduan git  add funtion",执行完毕后，使用 git status 查看状态：
         
         由此可看出，每次确认好的修改一定要做，git add 添加操作。
   7. 测试：撤销修改。
      1. 未git add 到暂存区：现在CodeD.txt中添加一句话：
         
         只保存，不git add ,现在我不想把6.photo按钮放在这个内容中，直接执行git checkout --CodeD.txt.
         执行收观察：
         
         
         由此可见，6.photo按钮，已经被撤回，因为5.txt按钮没有git add 过，所以也一起撤回了。
      2. 已经git add dao缓冲区，现在在CodeD.txt中添加一段文字，并且执行git add：
         
         
         首先执行git status 查看状态：
         
         可以看出该操作已经添加到了暂存区，
         执行 git reset HEAD CodeD.txt就可以将已经放在缓冲区的文件放回到工作区中：
         
         
         可以看出上诉添加txt按钮操作已经放回到了工作去，接下来可以使用git checkout -- file操作撤回5.txt按钮。
   8. 删除文件实验
      1. 首先在CodeKu中创建一个test.txt测试文本文件。
         
         并执行 git add test.txt和git commit -m "add test"
      2. 执行删除操作。
         执行git rm test.txt
         执行git commit -m "remove test
         
         
         
         删除文件成功。
         但如果我们删错了，可以执行git checkout -- test.txt.恢复。
5. 远程仓库（在Github上同步一个仓库）
   1. 打开git bash here，执行ssh-keygen -t rsa -C "1358805979@qq.com"
      
   2. 在C盘中Administrator中会出现ssh文件夹。内容如下：
      
   3. 登录个人github，在Edit profile中，选择SSH and GPG keys.添加新的ssh公钥。
      
   4. 在github中新建新的仓库CodeKu,按照如下操作。
      
      
   5. 推送本地库中文件到github-CodeKu中。
      执行git remote add origin git@github.com:HQIZCC/CodeKu.git
              git push -u origin master   推送命令。
      
      
6. 分支
   1. 创建和合并分支。
      执行 git checkout -b function，//-b=git branch 创建分支，git checkout此处理解为转换到某分支。所以连接到一起，则为创建function分支，并转换到到该分支。
      
      查看当前分支：git branch
      
      修改CodeD.txt内容：
      
      切换到master分支，git checkout master，并查看此时CodeD.txt内容：
      
      
      我在funciton分之下写了txt按钮功能描述。。。在切换到master后再打开CodeD.txt文件，刚才的内容没有显示。接下来执行合并分支。
   2. 合并分支
      将5.1的function分支合并到master上。执行 git merge function
      
      查看CodeD.txt内容：
      
      执行 git branch 查看当前分支情况，执行git branch -b function删除function分支，执行
      git branch 查看当前分支情况。
      
7. 标签
   1. 创建标签
      在master目录下，创建第一个标签
      执行git tag t1.0
      执行git tag 查看标签
      
   2. 在git log目录下添加标签
      执行git log --pretty=oneline --abbrev-commit
      
      我打算在add function 3 上打一个说明标签“add 3th function"
      执行git tag -a t1.1 -m "add 3th function" 3ca1d2a
      
      查看当前tag，执行git tag，
      
      查看tag t1.1详细情况，执行git show t1.1
      
   3. 操作标签
      1. 将标签推送到github上
         仅推送一个，执行 git push origin t1.0
         
         
         推送全部tag，执行git push origin --tags
         
         
      2. 删除本地标签
         执行 git tag -d t1.0
         查看现有标签git tag
         
      3. 删除远程标签，首先删除本地标签，如上述第二步
         然后执行git push origin :refs/tags/t1.0
         
         

### 二、深入学习标签与分支

1. 开发分支develop，临时分支：功能分支：fearture，预发布分支：release，Bug分支：fixbug分支
   1. 开发分支develop学习：
      执行git checkout -b develop ，创建开发分支
      
      对CodeD.txt进行修改
      
      执行git add CodeD.txt
      执行git commit -m “add develop branch”
      
      采用--no-ff参数合并到主分支master，参数--no-ff会在master生成一个新街点，可以保证版本演进的清晰度。
      执行git merge --no-ff develop
      
      查看CodeD.txt内容
      
      发布到github仓库
      执行git push origin master
      
   2. release预发布分支
      什么是预发布分支？
      答：在发布正式版本前，也就是合并到mster分支之前，我们可以创建一个预发布版本进行测试。预发布版本是从develop分支上分出来的。预发布结束之后，也就是版本测试成功之后，我们必须要合并到develop和master分支。他的命名可以采用releas-版本号的形式
      
      执行命令git checkout -b release-1.1 develop创建分支
      
      执行git branch查看分支
      
      确认没问题，合并到master，并创建一个合并节点（先转到master分支）
      
      查看标签D1.1及详细信息
      
      
      再合并到develop分支（先转到develop分支）
      
      然后删除预发布分支
      
      
   3. Bug分支
      为什么需要bug分支，bug分支怎么工作
      答：在正式版本发布之后，也许会出现bug，此时就需要一个专用的bug分支，进行修补bug。bug分支是从master分支上分出来的，修补结束之后，在合并到master分支和develop分支。格式可以采用
      fixbug-版本号的形式。
      执行git checkout -b fixbug-1.0 master，创建标签为1.0的fixbug
      
      修补结束之后（改变CodeD.txt些许内容，以便观察），执行git add CodeD.txt
      											       执行git commit-m“fixbug function“提交到版本库，执行git checkout master，查看CodeD.txt内容。
      
      
      
      确认无误之后合并到master分支，并创建标签，并查看标签详细情况。
      
      
      
      再合并到develop分支
      
      最后删除fixbug分支
      
2. 本地实验 git log --pretty=oneline截图，网站commits&branch截图
   
   
   
3. 后续进一步学习，可以阅读博客https://HQIZCC.github.io

---

## 四、实验小结

1. 对于本次的git版本库学习，有了初步的认识与理解。对于简单的指令已初步掌握，并学会了与远程仓库的联系。
2. 通过多次的git练习，已基本掌握了版本库的各版本管理。
3. 深入学习了分支，以及标签的运用。
   

---

## 五、参考资料

1. 廖雪峰的git教程
2. Markdown语法手册
3. https://zhushaojun.github.io
