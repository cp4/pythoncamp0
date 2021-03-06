## 使用Gitbook

### 用gitbook写书

### gitbook的问题
使用gitbook新建一本书，编辑并保存之后，进入My Books，可以在线看到生成的图书。
     
但是，如果在编辑之前，在设置中将书和github进行了关联，则编辑保存之后，发生两件事情：1、编辑产生的变化会提交到github中；2、使用gitbook不能看到在线生成的书了。
     
 使用gitbook进行发布和使用github进行管理变成了鱼和熊掌，不可兼得。
### 绕过问题
gitbook的糟糕表现，可以概括为：不与github关联的图书可以发布，与github关联的图书不能发布。那么，怎么能使用github编辑一本书，却仍然用gitbook发布呢？只要不让gitbook知道它现在正在编辑的图书是用github写出来的不就可以了吗？
     
在gitbook上新建一本书，保存url地址；在github上建立我们想要编辑的图书仓库，保存url地址。现在，即不直接使用github的图书仓库，更不直接使用gitbook的编辑功能。转而在本地编辑，并同时对这二者进行更新。
      
这里的关键是，github与gitbook的双推技巧。
      
### git双推
基本思想是在本地clone上述任意一个git仓库，并在push的时候同时更新到另一个去。
      
假设，clone github的仓库：

      git clone https://...
为了双推，需要修改git本地的origin文件。
在.git/config中的[remote origin]下增加另一个url地址，即，gitbook的地址：
      。。。
修改之后，执行：

      git push -u origin master
会依次push github和gitbook，并分别要求输入二者的username和password[^1]（参考注意事项1）。  
该操作会报错：
      。。。。
原因是我们上传的版本与gitbook的本地版本不一致，因此无法更新成功。这个没有别的办法，只能用暴力覆盖原有的版本，使用+标志[^2]。

      git push -u gitbook +master（参考事项2）
该操作成功后，gitbook上的版本就与本地版本完全一样了。
以后，直接使用git push origin master就可以同时更新两地仓库了。

注1：gitbook的username, password设置。

注2：如果该命令报错，并提示gitbook不是一个仓库，可以直接使用之前保存的gitbook的url进行push。
      
