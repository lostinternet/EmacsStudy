* 2017/05/20
** Install ubuntu

** Retset root password

** Control Terminal Font size
   终端下可以快速控制字体的大小，
   + C - 缩小字体
   + C S + 放大字体
   + C 0 恢复字体

** Finding
   + whereis 只能查打文件，并且是模糊查找
   + find查找精确，但速度慢
   + locate 最高效
   
** Setting APT proxy
   Ubuntu16.04以前的版本在AllSettings->Network->Network proxy中设置代
   理时，是可以在detail中输入用户名和密码的。
   但是16.04版本中不进行detail设置。
   而apt使用时又不会要求输入用户名密码，因此不能使用apt安装应用。
   
   解决办法是，在/etc/apt/下编辑apt.conf(如果没有这个文件，就新建一下)。
   
   在里面输入：
   
   Acquire::http::proxy "http://username:password@proxy.neu.com:8080/";
   其中的proxy.neusoft.com是东软的代理，可以根据情况改变。
   设置后，再次使用sudo apt update进行验正。
   这种方式只能设置APT的代理，并不能应用于其它，下面还将介绍两中代理的
   设置。
   
** Setting FireFox proxy
   firefox的代理可以单独设置，尤其是在有代理服务器的情况下，因为某此站
   点不能使用代理服务器连接。所以，可以手工设置代理服务器，并排除一些
   不需要代理的站点。

** Setting System proxy
   前面两个之是单独的用与设置APT proxy与FireFox proxy,如果想要让其它应用使用代理，还需要进入用户根目录下，即~/。
   编辑.bashrc，在文件的最后加下面的内容。
   http_proxy=http://yourproxyaddress:proxyport
   export http_proxy
   注意，把yourproxyaddress换成你的代理IP,把proxyport换成代理端口。

** Setting source list
   在国内要使用一些软件还是换成国内的源比较好，可以在网上找一些与自已
   版本匹配的源。
   使用root权限打开etc/apt/source.list，把内容更换为国内的源，并保存。
   使用apt update更新源。
   再使用apt -f install配置一下依赖就可以正常安装其它软件了。

** install software
   ubuntu下安装软件有多种方式，可以使用ubuntu software搜索应用进行安装，
   也可以在网站上下载安装包或压缩包进行安装。
   使用ubuntu software进行安装比较简单，这里就不记录，这一节说一下使用
   安装包安装应用软件，以网易云音乐为例，下一节介绍使用压缩包安装Emacs。
   + 在网易云音乐的网站上下载与操作系统匹配的安装包
   + 执行dpkg -i netease***.deb
     如果前面更新了软件源，则这里安装是没有问题的，如果安装不成功，请
     参照前面更新源的方法操作后，再次尝试安装。



** Install Emacs
*** gnu网站下载Emacs最新版
*** 执行./configure
    如果执行这一步时出现了错误，一般都是本地缺少一些库导致的，根据提示，
    安装相应的库文件即可。
    通常会缺少gtk, 安装方法：sudo apt-get install libgtk2.0-dev, 在使
    用./configure时使用--with-x-toolkit=gtk即可。
    如果缺少xpm, jpeg, tiff, gif, 则分别安装。
    libjpeg9
    libxpm4
    libgif7
    libtiff5
    如果版本使用不对，还是不能正确安装，但如何选择正确的版本是个问题，我现在也不清楚要如何选择。
    再次configure。
    通过后，执行sudo make, sudo make install
* 2017/05/28
** 安装五笔输入法
   Linux下的Emacs并不能使用系统自带五笔输入法，因此必须安装Emacs插件来
   实现。
   ubuntu下的中文输出法，我只用了fcitx，并没有感觉不方便，先这么用着吧。
   sudo apt-get install fcitx-table-wbpy
   在语言与支持设置项中，把键盘输入方式修改为fcitx.
   重启电脑
   在导盘栏中点击小键盘图标，选择配置，添加五笔拼音输入法。
   
** SVN的使用
   svn add:
   svn co:checkout file
   svn up:update
   svn ci:commit
   svn del:delete
   svn log:show log
   svn revert: revert
   svn st: status
   svn di:diff
   svn merge:merge
** tar
   tar只是一个打包工具，把多个文件打包成一个文件，因此tar文件并不比原
   文件少，所以还需要进行压缩，压缩成gzip格式，则扩展名变为.gz

* 2017/05/29
** 当前目录
   Windows应用程序的命令行模式会自动区分当前目录，但linux的命令行不能自动识别当前目录。必须显示的用./表示出来




* 2017/07/01
** 安装JDK
   下载JDK
   JDK下载后，解压完成，将其放到/usr/lib/jvm下；
   编辑~/.bashrc文件，添加环境变量
   export JAVA_HOME=/usr/lib/jvm/jdk1.8.0_131
   export JRE_HOME=${JAVA_HOME}/jre
   export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib
   export PATH=${JAVA_HOME}/bin;$PATH
   
** 安装Android Studio
   下载Android Studio相应版本，并解压到/opt/下，因为这个目录是用来安装
   程序的。
   进入到bin目录下，执行sh studio.sh执行安装。
   如果访问网络时有代理，会出现提示，要求输入代理。
   如果出现下面的提示：
  Unable to run mksdcard SDK tool.
  可以不用管，直接点击地finish.可也可通过下面的命令下载依赖库
  sudo apt-get install lib32z1 lib32ncurses5 lib32stdc++6



* 2017/8/13
** 安装xrdp实现远程桌面连接
   sudo apt install xrdp
   但是对于ubuntu16.04, 在其它机器上使用LinuxStudyRDP连接时，会出现桌面就退出的
   情况。这是在用户目录下，会有.xsession-errors出现。
   现在还没有找到解决方法。

* 2017/12/6
** 安装latex
   latex分为编辑器与tex发行版两部分，编辑器可以使用Emacs+auxtex插件。
   tex发行版在Ubuntu上可以安装texlive.
   texlive可以到阿里云上下载安装iso文件。
   http://mirrors.aliyun.com/CTAN/systems/texlive/Images/
   下载后，挂载iso文件。
   sudo mount -t iso9660 -o ro,loop,noauto /yourISOFileDictory/texlive.iso
   /mnt"
   mount后，进入/mnt目录，使用下面命令安装
   sudo ./install-tl
   也可以使用参数--gui进入图形界面安装方式。
   安装完成后，卸载镜像
   sudo unmount /mnt
   增加环境变量
   可以编辑~/.bashrc文件，通过export设置环境变量，再把环境变量加入到
   PATH中。注意PATH中各路径要有:分隔。

   加入环境变量后，我的Ubuntu还是无法把tex文件变为pdf, 并提示如下内容：
   AUCTeX cannot find a working TeX distribution.
   Make sure you have one and that TeX binaries are in PATH
   environment variable

   天呀，明明已经加入到环境变量中了，在命令行下都可以执行latex
   --version了，为什么还是不能在Emacs中使用呢？
   原来是只把环境变量加到了当前用户下，而Emacs执行时使用的是管理员的环
   境变量，因此，找不到可执行的Tex发行版。
   至此，latex就安装完成了，写一个简单的测试tex, C-c C-c编译，C-c C-v
   查看。
* 2017/12/10
** 使用moderncv制作简历
   有了texlive和emacs就可以编写tex文件并生成pdf了。
   但是自已手动编写简历还是有点力不从心，这时可以使用moderncv制作好的
   模板来编写简历。在CTAN网站上下载moderncv，并解压到任意目录。
   但是Moderncv中提供的四种风格的简历，其中casual风格中，有一些
   section是必须要使用的，不然无法在页脚显示联系信息等内容，这时可以换
   一种风格。

* 2017/12/12
  遇到一个很鬼异的问题，早上路svn自动build脚本时，执行svn log -rHEAD时，
  只能取到-------------------------------------------------------
  而手动使用命令也是这个样子，但是使用svn log -rXXX能取到HEAD信息。
  后来，又有人上传代码后，使用svn log -rHEAD就能正常取到了。

* 2017/12/21
  卸载软件
  sudo apt-get autoremove --purge softwarename
