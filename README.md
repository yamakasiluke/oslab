# oslab
我自己看了看下面的步骤,虽然繁琐,但是可控,网上文章较多,相比去自己编译bochs和配置.bxrc文件还是比较简单的<br>
那我的mac电脑来说,遇到了不少问题,编译失败和repeat call floppy还有vga images wrong的还有bxrc问题的<br>
用docker可以使用老师配置好的环境,这个与课程一致的,很重要.<br>
用了这个方法至少可以保证可用<br>

Docker image to run hit-oslab on Linux, Windows, Mac os X<br>  
以下是docker镜像地址<br>  
https://hub.docker.com/r/yamakasiluke/oslab/<br>  
国内用户也可以痛快使用docker,速度很棒.<br>  
进入https://www.daocloud.io/,点击下载,下载相应的docker版本.<br>  
window10安装docker可能出现问题,需要在bios里开启虚拟化,没有遇到就不用管了.<br>  
之后安装docker hub加速器<br>
按照步骤,在docker使用 dao pull yamakasiluke/oslab:oslab 速度很快<br><br>
下载完成后使用 docker run -it -p 1234:22 -d yamakasiluke/oslab:workwell /usr/sbin/sshd -D<br>
你的本地ubuntu和sshd已经打开
mac和windows请再virtalbox里把端口配置一下
http://jingyan.baidu.com/article/414eccf67298a16b421f0a6d.html
外面配置成50183<br>
配置成1234<br>

windows要安装putty http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html <br>
xming http://sourceforge.net/projects/xming/files/Xming/<br>
用putty和xming连接自己的实验环境<br>
http://david-je.iteye.com/blog/1847417<br>
ssh -X root@127.0.0.1 -p 50183<br>
password is :oslab<br>

mac要安装xquartz http://www.xquartz.org/<br>
ssh要打开选项叫做xforwarding yes<br>
ssh -X root@127.0.0.1 -p 50183<br>
password is :oslab<br>

linux用户要ssh_config添加port 1234<br>
ssh -X root@127.0.0.1 -p 1234<br>
password is :oslab<br>

一切顺利就可以调试了,docker很好用,rtfsc<br>



