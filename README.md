
# 实验2 git使用

------

## 一、实验目的

1. 掌握git使用
2. 掌握使用Github作为元策划那个仓库

------

## 二、实验任务

1. 练习本地git操作
2. 用SSH同步本地与Github仓库

------

## 三、实验步骤与结果

要求一下结果截图

1. 本地操作log截图
2. Github上commits截图

### 一、实验步骤

1. 安装git（在安装的最后一步设置时，输入 

   `git config-global user "HQIZCC"`							               

   `git config-global email "1358805979@qq.com"`

2. 创建一个本地版本库，依次输入如下命令：

   `cd /d d:`

   `mkdir CodeKu`

   `cd CodeKu`

   `git init`

3. 创建一个CodeD.txt代码详情.txt文件

   用命令 `git add CodeD.txt` 将文件添加到仓库CodeKu								   

   用命令 `git commit -m "a code ku"`将文件提交到仓库CodeKu

4. 本地版本管理测试

   1. 首先修改CodeD.txt文本内容(此处增加：功能：1.介绍代码模块) 并保存。

      使用命令 `git status` 查看CodeKu库当前状态：结果显示如图：

      ![4.1](http://wx4.sinaimg.cn/mw690/006tbMMVgy1fe1cwjg9pwj30db03g0si.jpg)

      运行结果说明：CodeD.txt文本被修改过，但是没有提交。

   2. 确认无误后，使用命令 

      `git add CodeD.txt`

      `git commit -m "add fuction 1`

   3. 连续进行两次修改CodeD.txt文件内容，以增加更多的版本完成本次测试。

      依次添加，内容如下：

      ![4.3.1](http://wx1.sinaimg.cn/mw690/006tbMMVgy1fe1cwjui0uj306l00q0gi.jpg)

      ![4.3.2](http://wx1.sinaimg.cn/mw690/006tbMMVgy1fe1cwkl6v9j306900k0ga.jpg)

      注意：每次提交完成后记得使用 `git add CodeD.txt` 和` git commit -m "修改内容” `提交到本地仓库

      使用命令 `git log --pretty=oneline` 查看最近提交的日志，如下图：

      ![4.3.3](http://wx1.sinaimg.cn/mw690/006tbMMVgy1fe1cwll2wwj309t020t8h.jpg)

      由此可见我们一个有了四次修改，也就是四个版本，接下来进行版本控制实验。

   4. 版本回退操作，使用`git reset --hard HEAD~1` 可以将版本回退到上一个版本，并且打开CodeD.txt文件查看该操作是否有效：实验截图如下：

      ![4.4.1](http://wx1.sinaimg.cn/mw690/006tbMMVgy1fe1cwltq88j306l00y0g3.jpg)

      文本内容：

      ​		![4.4.2](http://wx2.sinaimg.cn/mw690/006tbMMVgy1fe1cwlwtzij306d0220nz.jpg)

   5. 接下来，使用reset 加commit id 回到某一版本实验。

      1. 首先查看将要回退的版本的commit id，比如说我们现在要回退到add functions 3 这个版本。步骤3 的git log 结果图，可以得到add function 3 的commit id 为3ca1d2a。

      2. 结合命令 `git reset --hard 3ca1d2a`即可回退到版本3，实验截图如下：

         ![5.2](http://wx2.sinaimg.cn/mw690/006tbMMVgy1fe1cwmlbhdj306p0140hi.jpg)

         ![5.3](http://wx3.sinaimg.cn/mw690/006tbMMVgy1fe1cwn9oiuj307m02f0qb.jpg)

   6. 当我们在修改文件时，如果进行了连续修改，在某一次修改完成后，执行了`git add` 添加到仓库操作后，接下来又进行了修改，但是没有执行`git add` 添加到仓库修改，那么在下次的`git commit -m“”`提交到仓库操作，只会把第一次的内容提交上去，而第二次仍会处在暂存区：

      1. 第一次修改，并执行了`git add` 添加命令。

         ![6.1](http://wx4.sinaimg.cn/mw690/006tbMMVgy1fe1cwnpjwdj307i02t0sh.jpg)

         执行 `git add CodeD.txt`操作：

         ![6.2](http://wx1.sinaimg.cn/mw690/006tbMMVgy1fe1cwnzb26j305000x099.jpg)

      2. 第二次修改，不执行` git add` 添加命令：

         ![6.3](http://wx2.sinaimg.cn/mw690/006tbMMVgy1fe1cwoldowj307p03jjr5.jpg)

      3. 执行 `git commit -m "panduan git  add funtion"`,执行完毕后，使用 `git status` 查看状态：

         ![6.4](http://wx4.sinaimg.cn/mw690/006tbMMVgy1fe1cwpdbgpj30d403bmwx.jpg)

         由此可看出，每次确认好的修改一定要做，git add 添加操作。

   7. 测试：撤销修改。

      1. 未`git add` 到暂存区：现在CodeD.txt中添加一句话：

         ![7.1](http://wx4.sinaimg.cn/mw690/006tbMMVgy1fe1cwqxv2dj307s04aq2q.jpg)

         只保存，不`git add` ,现在我不想把6.photo按钮放在这个内容中，直接执行`git checkout --CodeD.txt`.

         执行收观察：

         ![7.1.1](http://wx2.sinaimg.cn/mw690/006tbMMVgy1fe1cwq4hdcj306k00l0ay.jpg)

         ![7.1.2](http://wx4.sinaimg.cn/mw690/006tbMMVgy1fe1cwqxv2dj307s04aq2q.jpg)

         由此可见，6.photo按钮，已经被撤回，因为5.txt按钮没有git add 过，所以也一起撤回了。

      2. 已经`git add dao `缓冲区，现在在CodeD.txt中添加一段文字，并且执行git add：

         ![7.2.1](http://wx2.sinaimg.cn/mw690/006tbMMVgy1fe1cwramldj307z03ldfl.jpg)

         ![7.2.2](http://wx1.sinaimg.cn/mw690/006tbMMVgy1fe1cwrxczpj305500v088.jpg)

         首先执行`git status` 查看状态：

         ![7.2.3](http://wx2.sinaimg.cn/mw690/006tbMMVgy1fe1cwsfa69j30ad0283y9.jpg)

         可以看出该操作已经添加到了暂存区，

         执行 `git reset HEAD CodeD.txt`就可以将已经放在缓冲区的文件放回到工作区中：

         ![7.2.4](http://wx4.sinaimg.cn/mw690/006tbMMVgy1fe1cwtbw4aj306k0130fu.jpg)

         ![7.2.5](http://wx1.sinaimg.cn/mw690/006tbMMVgy1fe1cwtha78j30d503bmwx.jpg)

         可以看出上诉添加txt按钮操作已经放回到了工作去，接下来可以使用`git checkout -- file`操作撤回5.txt按钮。

   8. 删除文件实验

      1. 首先在CodeKu中创建一个test.txt测试文本文件。

         ![8.1](http://wx3.sinaimg.cn/mw690/006tbMMVgy1fe1cwulsahj30540240lk.jpg)

         并执行 `git add test.txt `和`git commit -m "add test"`

      2. 执行删除操作。

         执行`git rm test.txt`

         执行`git commit -m "remove test`

         ![1](http://wx4.sinaimg.cn/mw690/006tbMMVgy1fe1e24nm0zj309905hq2p.jpg)

         ​

         ![8.2.2](http://wx4.sinaimg.cn/mw690/006tbMMVgy1fe1cwvjomrj304s01i0dk.jpg)

         删除文件成功。

         但如果我们删错了，可以执行` git checkout -- test.txt`.恢复。

5. 远程仓库（在Github上同步一个仓库）

   1. 打开`git bash here`，执行`ssh-keygen -t rsa -C "1358805979@qq.com"`

      ![9.1](http://wx1.sinaimg.cn/mw690/006tbMMVgy1fe1cww52oxj30fy08eglk.jpg)

   2. 在C盘中Administrator中会出现ssh文件夹。内容如下：

      ![9.2](http://wx2.sinaimg.cn/mw690/006tbMMVgy1fe1cwwlvcqj305c0240q8.jpg)

   3. 登录个人github，在Edit profile中，选择SSH and GPG keys.添加新的ssh公钥。

      ![9.3](http://wx1.sinaimg.cn/mw690/006tbMMVgy1fe1cwx4p8qj30lk0ag3yi.jpg)

   4. 在github中新建新的仓库CodeKu,按照如下操作。

      ![9.5](http://wx1.sinaimg.cn/mw690/006tbMMVgy1fe1cwycpvzj30j80drglr.jpg)

      ![9.4](http://wx1.sinaimg.cn/mw690/006tbMMVgy1fe1cwxgpizj30nm0bmt8w.jpg)

   5. 推送本地库中文件到github-CodeKu中。

      执行`git remote add origin git@github.com:HQIZCC/CodeKu.git`

      ​        `git push -u origin master`   推送命令。

      ![10.1](http://wx1.sinaimg.cn/mw690/006tbMMVgy1fe1cwydwgkj30bh03jgle.jpg)

      ![10.2](http://wx4.sinaimg.cn/mw690/006tbMMVgy1fe1cwyyxt6j30j509r3yi.jpg)

6. 分支

   1. 创建和合并分支。

      执行 `git checkout -b function`，//-b=git branch 创建分支，`git checkout`此处理解为转换到某分支。所以连接到一起，则为创建function分支，并转换到到该分支。

      ![11.1](http://wx4.sinaimg.cn/mw690/006tbMMVgy1fe1cwzvbfoj30710180ga.jpg)

      查看当前分支：`git branch`

      ![11.2](http://wx4.sinaimg.cn/mw690/006tbMMVgy1fe1cx0a0hsj304b01e0fc.jpg)

      修改CodeD.txt内容：

      ![11.3](http://wx3.sinaimg.cn/mw690/006tbMMVgy1fe1cx0vnluj307u05bq2p.jpg)

      切换到master分支，`git checkout master`，并查看此时CodeD.txt内容：

      ![11.4](http://wx3.sinaimg.cn/mw690/006tbMMVgy1fe1cx1fc6dj308501d0jn.jpg)

      ![11.5](http://wx2.sinaimg.cn/mw690/006tbMMVgy1fe1cx1nyl6j308h0360sh.jpg)

      我在funciton分之下写了txt按钮功能描述。。。在切换到master后再打开CodeD.txt文件，刚才的内容没有显示。接下来执行合并分支。

   2. 合并分支

      将5.1的function分支合并到master上。执行 `git merge function`

      ![11.6](http://wx3.sinaimg.cn/mw690/006tbMMVgy1fe1cx2xm00j308c0200sf.jpg)

      查看CodeD.txt内容：

      ![11.7](http://wx2.sinaimg.cn/mw690/006tbMMVgy1fe1cx36uzpj307t055gld.jpg)

      执行 `git branch` 查看当前分支情况，执行`git branch -b function`删除function分支，执行

      `git branch` 查看当前分支情况。

      ![11.8](http://wx1.sinaimg.cn/mw690/006tbMMVgy1fe1cx3pvtyj306m03f0o0.jpg)

7. 标签

   1. 创建标签

      在master目录下，创建第一个标签

      执行`git tag t1.0`

      执行`git tag` 查看标签

      ![12.1](http://wx3.sinaimg.cn/mw690/006tbMMVgy1fe1cx43pr7j304701m0a6.jpg)

   2. 在`git log `目录下添加标签

      执行`git log --pretty=oneline --abbrev-commit`

      ![12.2](http://wx1.sinaimg.cn/mw690/006tbMMVgy1fe1cx4x086j309l040q2p.jpg)

      我打算在add function 3 上打一个说明标签“add 3th function"

      执行`git tag -a t1.1 -m "add 3th function" 3ca1d2a`

      ![12.3](http://wx4.sinaimg.cn/mw690/006tbMMVgy1fe1cx5qhe0j30a000o0bq.jpg)

      查看当前tag，执行`git tag`，

      ![12.5](http://wx2.sinaimg.cn/mw690/006tbMMVgy1fe1cx6vs16j303x01d09t.jpg)

      查看tag t1.1详细情况，执行`git show t1.1`

      ![12.4](http://wx2.sinaimg.cn/mw690/006tbMMVgy1fe1cx5pt32j30dc021a9t.jpg)

   3. 操作标签

      1. 将标签推送到github上

         仅推送一个，执行 `git push origin t1.0`

         ![13.1](http://wx3.sinaimg.cn/mw690/006tbMMVgy1fe1cx6sic3j30cm03ht8h.jpg)

         ![13.2](http://wx3.sinaimg.cn/mw690/006tbMMVgy1fe1cx7hi3qj30dj03ma9u.jpg)

         推送全部tag，执行`git push origin --tags`

         ![13.3](http://wx2.sinaimg.cn/mw690/006tbMMVgy1fe1cx7r548j30a002aa9t.jpg)

         ![13.4](http://wx4.sinaimg.cn/mw690/006tbMMVgy1fe1cx8boynj30fj03fwea.jpg)

      2. 删除本地标签

         执行 `git tag -d t1.0`

         查看现有标签` git tag`

         ![13.5](http://wx3.sinaimg.cn/mw690/006tbMMVgy1fe1cx8s9uqj306601w0hx.jpg)

      3. 删除远程标签，首先删除本地标签，如上述第二步

         然后执行`git push origin :refs/tags/t1.0`

         ![13.6](http://wx2.sinaimg.cn/mw690/006tbMMVgy1fe1cx9wzw4j307k01g0jj.jpg)

         ![13.7](http://wx2.sinaimg.cn/mw690/006tbMMVgy1fe1cx9x7pcj30dq04k742.jpg)

### 二、深入学习标签与分支

1. 开发分支develop，临时分支：功能分支：fearture，预发布分支：release，Bug分支：fixbug分支

   1. 开发分支develop学习：

      执行`git checkout -b develop` ，创建开发分支

      ![20.1](http://wx3.sinaimg.cn/mw690/006tbMMVgy1fe1cxfy4wej306p01f0gn.jpg)

      对CodeD.txt进行修改

      ![20.1.1](http://wx3.sinaimg.cn/mw690/006tbMMVgy1fe1cxdobclj30f7077743.jpg)

      执行`git add CodeD.txt`

      执行`git commit -m “add develop branch”`

      ![20.1.2](http://wx3.sinaimg.cn/mw690/006tbMMVgy1fe1cxeck6qj308j0230ot.jpg)

      采用--no-ff参数合并到主分支master，参数--no-ff会在master生成一个新街点，可以保证版本演进的清晰度。

      执行`git merge --no-ff develop`

      ![20.1.3](http://wx4.sinaimg.cn/mw690/006tbMMVgy1fe1cxeut2dj306p00x0bz.jpg)

      查看CodeD.txt内容

      ![20.1.1](http://wx3.sinaimg.cn/mw690/006tbMMVgy1fe1cxdobclj30f7077743.jpg)

      发布到github仓库

      执行`git push origin master`

      ![20.1.4](http://wx1.sinaimg.cn/mw690/006tbMMVgy1fe1cxfjq9hj30ff0bijra.jpg)

   2. release预发布分支

      ***什么是预发布分支？***

      答：在发布正式版本前，也就是合并到mster分支之前，我们可以创建一个预发布版本进行测试。预发布版本是从develop分支上分出来的。预发布结束之后，也就是版本测试成功之后，我们必须要合并到develop和master分支。他的命名可以采用releas-版本号的形式

      ​

      执行命令`git checkout -b release-1.1 develop`创建分支

      ![21.1.1](http://wx1.sinaimg.cn/mw690/006tbMMVgy1fe1cxh6aboj30af0120hh.jpg)

      执行`git branch`查看分支

      ![21.1.2](http://wx3.sinaimg.cn/mw690/006tbMMVgy1fe1cxh84rcj304l0230f4.jpg)

      确认没问题，合并到master，并创建一个合并节点（先转到master分支）

      ![21.1.3](http://wx3.sinaimg.cn/mw690/006tbMMVgy1fe1cxhtpn1j30al03ba9t.jpg)

      查看标签D1.1及详细信息

      ![img](http://wx2.sinaimg.cn/mw690/006tbMMVgy1fe1cxiucmuj307u01y0d4.jpg)

      ![img](http://wx4.sinaimg.cn/mw690/006tbMMVgy1fe1cxj6s30j308i04wq2p.jpg)

      再合并到develop分支（先转到develop分支）

      ![合并到develop](http://wx3.sinaimg.cn/mw690/006tbMMVgy1fe1cxjmpy3j307502h0mt.jpg)

      然后删除预发布分支

      ![创建预发布版本release-1.1](http://wx2.sinaimg.cn/mw690/006tbMMVgy1fe1cxknahmj307u0100fc.jpg)

      ![查看现有分支](http://wx3.sinaimg.cn/mw690/006tbMMVgy1fe1cxk32ssj304i01q0dm.jpg)

   3. Bug分支

      ***为什么需要bug分支，bug分支怎么工作***

      答：在正式版本发布之后，也许会出现bug，此时就需要一个专用的bug分支，进行修补bug。bug分支是从master分支上分出来的，修补结束之后，在合并到master分支和develop分支。格式可以采用

      fixbug-版本号的形式。

      执行`git checkout -b fixbug-1.0 master`，创建标签为1.0的fixbug

      ![创建fixbug-1.0](http://wx3.sinaimg.cn/mw690/006tbMMVgy1fe1cxl517wj30890160h5.jpg)

      修补结束之后（改变CodeD.txt些许内容，以便观察），执行`git add CodeD.txt`

      ​											       执行`git commit-m“fixbug function“`提交到版本库，执行`git checkout maste`r，查看CodeD.txt内容。

      ![bug-CodeD](http://wx2.sinaimg.cn/mw690/006tbMMVgy1fe1cxljcqpj30er071743.jpg)

      ![提交到版本库](http://wx2.sinaimg.cn/mw690/006tbMMVgy1fe1cxma60pj308h0240p8.jpg)

      ![CodeD.txt-master](http://wx4.sinaimg.cn/mw690/006tbMMVgy1fe1cxmv9chj30ex06v0sj.jpg)

      确认无误之后合并到master分支，并创建标签，并查看标签详细情况。

      ![合并到master](http://wx2.sinaimg.cn/mw690/006tbMMVgy1fe1cxnhu5lj309h03emwx.jpg)

      ![创建bug标签并查看](http://wx4.sinaimg.cn/mw690/006tbMMVgy1fe1cxnqbmtj307j02o0g5.jpg)

      ![显示bug B-1.1](http://wx1.sinaimg.cn/mw690/006tbMMVgy1fe1cxo4gyqj30c404ht8h.jpg)

      再合并到develop分支

      ![合并到develop分支](http://wx3.sinaimg.cn/mw690/006tbMMVgy1fe1cxozpugj308v02w741.jpg)

      最后删除fixbug分支

      ![删除fixbug-1.0](http://wx4.sinaimg.cn/mw690/006tbMMVgy1fe1cxpkfkbj307p02s0n9.jpg)

2. 本地实验 `git log --pretty=oneline`截图，网站commits&branch截图

   ![本地操作git log](http://wx1.sinaimg.cn/mw690/006tbMMVgy1fe1cxpw6fmj30e909f3yi.jpg)

   ![commits&branchs](http://wx2.sinaimg.cn/mw690/006tbMMVgy1fe1cxqahyyj30kg0c1aa4.jpg)

   ![branch](http://wx1.sinaimg.cn/mw690/006tbMMVgy1fe1cxqvug7j30ku0e9t8r.jpg)

3. 后续进一步学习，可以阅读博客<https://HQIZCC.github.io>

------

## 四、实验小结

1. 对于本次的git版本库学习，有了初步的认识与理解。对于简单的指令已初步掌握，并学会了与远程仓库的联系。

2. 通过多次的git练习，已基本掌握了版本库的各版本管理。

3. 深入学习了分支，以及标签的运用。

   ​

------

## 五、参考资料

1. [廖雪峰的git教程](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000 "廖雪峰的git教程")
2. [Markdown语法手册](http://blog.leanote.com/post/freewalk/Markdown-%E8%AF%AD%E6%B3%95%E6%89%8B%E5%86%8C#title-31 "Markdown学习手册")
3. <https://zhushaojun.github.io>
