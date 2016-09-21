##6. Client端命令
<hr style=" border:4px solid #A9A9A9;" /> 
客户端共包含10个常用命令。目前有 Linux 、 window 、 os 三个操作系统版本客户端，具体获取方式见 [http://www.gzbdex.com/clientDownload](http://www.gzbdex.com/clientDownload).    
<br></br>
DataHub 的数据结构由数据主题（ Repository ,简称 repo ）、数据项（ DataItem ，简称 item ）、数据包（ Tag ）三级结构构成，数据主题在 DataHub 网站创建，数据项、数据包在 Client 端发布。     
 
###命令介绍
#####[6.1 dp 数据池管理](dp.md)
#####[6.2 ep 端口管理](ep.md)
#####[6.3 job 任务管理](job.md)
#####[6.4 login 登录](login.md)
#####[6.5 logout  退出](logout.md)
#####[6.6 pub  发布数据](pub.md)
#####[6.7 pull 获取数据](pull.md)
#####[6.8 repo  数据主题管理](repo.md)
#####[6.9 subs 订购管理](subs.md)
#####[6.10 version  版本](version.md)
#####[6.11 help  帮助](help.md)    

#####说明
* 如果没有额外说明，所有的命令在没有错误发生时，不在终端输出任何信息，只记录到日志中。错误信息会打印到终端。
* 所有的命令执行都会记录到日志中，日志级别分[TRACE] [INFO] [WARNNING] [ERROR] [FATAL]。日志在 DataHub 网站“监控中心”查看。
* 参数支持全名和简称两种形式，例如--type等同于-t。详情见命令帮助。
* 参数赋值支持空格和等号两种形式，例如 --type = file 等同于 --type file。
