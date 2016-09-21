##6.2 ep	端口管理
<hr style=" border:4px solid #A9A9A9;" />  
端口（ Entry Point ）需要在发布数据时设置，供后续数据需求方在得到认证和鉴权后获得下载数据的入口。端口包括协议、 ip 、 port 三部分。特别注意 ep 需是数据提供方从外网可访问公网端口。 
###6.2.1 查看端口  
#####输入
	datahub ep 
#####输出  
	%msg	
#####例子  
	bash-3.2# datahub ep
	DataHub : you don't have any entrypoint.    
###6.2.2 设置端口  
#####输入  
	datahub ep http://$ip:$port  
#####输出
	%msg  
#####例子s
	bash-3.2# datahub ep http://192.168.2.255:2323
	DataHub : OK. your entrypoint is: http://192.168.2.255:2323
	The entrypoint is setted successfully.  You can check whether it is available in one minute.