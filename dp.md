##6.1  dp	数据池管理
<hr style=" border:4px solid #A9A9A9;" />  
数据池是存放数据的目录。无论是下载数据、发布数据，均需要指定数据存放的数据池。目前支持 file 、 s3 、 hdfs 三种类型的数据池。    
###6.1.1 查看所有数据池
#####命令  
	datahub dp  
#####输出  
输出datahub数据池名称DPNAME ,每个数据池类型DPTYPE	  
  
	%DPNAME    %DPTYPE
	
#####例子  
	bash-3.2# datahub dp
	DATAPOOL            TYPE    
	------------------------
	datahubdp1          file    
	datahubdp2          file    
	datahubdp3          S3   
	datahubdp3          HDFS  


###6.1.2 查看某个具体数据池详情
#####命令  

	datahub dp  $DPNAME
#####输出	  
	输出datahub数据池名称DPNAME ,每个数据池类型DPTYPE	  
  
		%DPNAME          %DPTYPE        %DPCONN
	%REPOSITORY/%DATAITEM:%TAG  %LOCAL_TIME        %T
	
#####例子  
	bogon:datahub root# datahub dp datahubdp1
	DATAPOOL:datahubdp1      	file            	/var/lib/datahub
	datahubrepo1/datahubitem1:datahubtag1 	2016-07-23T06:55:56Z 	pub   	decitem1                         	datahubtag.png       	 Size:38.14 KB	   
	Hot_searches/Hot_words:Search_popular_vocabulary 	2016-07-22T06:28:33Z 	pull  	hot                              	hotword              	Size:972 Bytes
###6.1.3 创建数据池    
创建数据池时可以设定数据池的类型，目前支持 file 、 s3 、 hdfs 三种类型。
#####命令  

	datahub dp  creat $DPNAME [[file://][ABSOLUTE PATH]] | [[s3://][BUCKET]] | [[hdfs://][USERNAME:PASSWORD@HOST:PORT]]
#####输出	
  
	%msg
	
#####例子  
* 设置file类型的数据池  

		bash-3.2# datahub dp create datahubdp2 file:///var/lib/datahub
		DataHub : Datapool has been created successfully. Name:datahubdp2 Type:file Path:/var/lib/datahub.    
  
* 创建s3类型的数据池。mybucket是s3上已存在的bucket。另外，需要在启动daemon的系统中设置环境变量：AWS_SECRET_ACCESS_KEY， AWS_ACCESS_KEY_ID， AWS_REGION。   

		bash-3.2#  datahub dp create s3dp s3://mybucket
		DataHub : s3dp already exists, please change another name.
* 创建hdfs类型的数据池。hdfs://”后需要接hdfs的连接串。  
		  
		$ datahub dp create hdfsdp hdfs://				user123:admin123@x.x.x.x:9000  
		
###6.1.4 删除数据池
删除数据池是逻辑删除，不会删除数据池所在的目录，以及数据池中的数据。当数据池中有发布的数据项时，不能被删除。
#####命令
	datahub dp rm $DPNAME    
#####输出	
  
	%msg
	
#####例子    
	bash-3.2# datahub dp rm datahubdp2
	DataHub : Datapool datahubdp2 removed successfully!