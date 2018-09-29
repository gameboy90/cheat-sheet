build vpn server use centos 6.2 via ppp and pptpd

主要步骤按照【linode centos 6 下搭建PPTP VPN 服务器】这篇文章（ url:http://www.360doc.com/content/12/0621/16/2660674_219650596.shtml ）

reboot后出现报错： GRE: read(fd=6,buffer=611860,len=8196) from PTY failed: status = -1 error = Input/output error, usually caused by unexpected termination of pppd, check option syntax and pppd logs

查找网络知识，进行如下操作： 在/etc/ppp/options.pptpd中注释掉下面行

require-mppe-128

then

/etc/pptpd.conf

logwtmp #注释掉这行

then

拨号出现“错误 742：远程计算机不支持所要求的数据加密类型”错误

如果连接的时候出现"错误 742：远程计算机不支持所要求的数据加密类型。"（在Win7下可能提示为"错误628：连接完成前，连接被远程计算机终止。"），在网络邻居里右击此VPN连接，选择"属性"，在"安全"选项卡里，把"要求数据加密（没有就断开）"前面的勾去掉，或者设置成"可选加密（没有加密也可连接）"即可。
