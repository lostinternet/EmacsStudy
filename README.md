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
