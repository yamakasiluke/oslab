# oslab
Docker image to run hit-oslab on Linux, Windows, Mac os X

##项目缘起

哈尔滨工业大学《操作系统》课程实验指导手册、实验环境（64位支持）及源码<br>
https://github.com/DeathKing/hit-oslab<br>
操作系统之基础<br>
http://mooc.study.163.com/course/HIT-1000002004#/info<br>
实验楼操作系统原理与实践<br>
https://www.shiyanlou.com/courses/115<br>

##项目原理
关键就是保住hit-oslab,hit-oslab建立在ubuntu上,我选择是用docker虚拟机包住ubuntu<br>
最后用ssh连接docker里的ubuntu,建立和实验楼一致命令行环境<br>

##具体步骤

###1.安装docker,并下载oslab的docker镜像
国内用户也可以痛快使用docker,速度很棒.<br>  
进入https://www.daocloud.io/,<br>
下载相应的docker版本.<br> 
window10安装docker可能出现问题,需要在bios里开启虚拟化,没有遇到就不用管了.<br>  
之后安装docker hub加速器<br>
https://dashboard.daocloud.io/mirror<br>
按照步骤,通过docker hub使用 dao pull yamakasiluke/oslab:oslab 速度很快<br>

以下是oslab的docker镜像地址<br>  
https://hub.docker.com/r/yamakasiluke/oslab/<br>  

###2.下载安装可视化窗口程序和ssh程序
windows<br><br>
xming http://sourceforge.net/projects/xming/files/Xming/<br>
windows要安装putty http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html<br>

mac os x<br>
mac要安装xquartz http://www.xquartz.org/<br>
ssh要打开选项叫做xforwarding yes<br>

linux<br><br>
您都用linux了,肯定很清楚.<br>
下载X11和openssh<br><br>

###3.配置docker端口,启动oslab,并用命令行连接<br>

配置docker端口<br>

windows 和 mac os x<br>
打开virtalbox,选中虚拟机->设置->网络->端口转发,修改主机端口和子系统端口,主机ip和子系统ip可以都为127.0.0.1<br>
主机端口和系统端口都不能被占用,可以随意设置,我设置的主机端口为50183,子系统端口为1234<br>
http://jingyan.baidu.com/article/414eccf67298a16b421f0a6d.html<br>
http://unmi.cc/mac-os-x-experience-docker/<br>

启动oslab,并默认打开容器的sshd服务<br>
docker run -it -p 1234:22 -d yamakasiluke/oslab:oslab /usr/sbin/sshd -D<br>

命令行连接<br>
windows<br>
用putty和xming连接自己的实验环境<br>
http://david-je.iteye.com/blog/1847417<br>
需要设置好putty的参数<br>
ssh -X root@127.0.0.1 -p 50183<br>
登录密码为oslab<br>

mac os x<br>
设置好ssh_config<br>
http://apple.tgbus.com/news/class/200901/20090110095747.shtml<br>
ssh -X root@127.0.0.1 -p 50183<br>
登录密码为oslab<br>

linux<br>
oslab镜像e里已经打开了sshd的22端口<br>
ssh_config添加port 1234<br>
请确保容器暴露的端口没有被占用,我这里是1234<br>


启动oslab,并默认打开容器的sshd服务<br>
docker run -it -p 1234:22 -d yamakasiluke/oslab:oslab /usr/sbin/sshd -D<br>

命令行连接<br>
ssh -X root@127.0.0.1 -p 1234<br>
登录密码为oslab<br>

我自己看了看下面的步骤,虽然繁琐,但是可控,网上文章较多,相比去自己编译bochs和配置.bxrc文件还是比较简单的<br>
那我的mac电脑来说,遇到了不少问题,编译失败和repeat call floppy还有vga images wrong的还有bxrc问题的<br>
用docker可以使用老师配置好的环境,这个与课程一致的,很重要.<br>
用了这个方法至少可以保证可用<br>


一切顺利就可以调试了,docker很好用,rtfsc<br>

致谢<br>
感谢李治军老师的付出



