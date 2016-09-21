##7.1 应用场景一 ： 下载数据
<hr style=" border:4px solid #A9A9A9;" />
下面介绍从 广数DataHub 网站订购网络搜索热词数据（ Hot_searches / Hot_words ） ，并通过客户端下载。
###第一步 在广数DataHub网站订购数据
在网站上订购了网络搜索热词数据（ Hot_searches / Hot_words ）  

* 在 广数DataHub 网站（ http://www.gzbdex.com ）上订购数据。
* 在用户中心->我的订购中查看订单、以及订单状态，对“正在生效中”状态的订单，可通过客户端下载数据包（ Tag ）。   


###第二步 通过longin命令登录Client端
#####输入
	datahub login
#####输出	  
	login as: ********@*******.com
	password: ******
	DataHub : Successed in publishing.
  
###第三步 通过客户端查看有效订单
在客户端通过 subs 命令查看“正在生效中”的订单，且能查看数据的在线状态（ status ）。  对于 online 状态的数据，可以立即进行下载，对于 offline 状态的数据，需数据服务提供方的数据提供服务启动后方能下载。  
#####输入
	datahub subs
#####输出
  	 REPOSITORY/ITEM         TYPE        STATUS     
  	 Hot_searches/Hot_words  file        online   

###第四步 创建数据的存放目录（数据池， datapool ）
在本地创建一个名叫 datahubdp1 的数据池，指定存储类型为文件（ file ），路径为 /var/lib/datahub 。 

* 对于新用户，若无数据池，先创建数据池，现支持 file、S3、HDFS 等三种类型。对于已经创建过数据池的用户，可直接进入到第五步。  


#####输入  

	datahub dp create datahubdp1 file:///var/lib/datahub
#####输出
	DataHub : Datapool has been created successfully. 	Name:datahubdp1 Type:file Path:/var/lib/datahub.  
	  
###第五步 通过 pull 命令下载数据包（ Tag ）
指定订购数据下需要下载的具体数据包名， Search_popular_vocabulary ，指定下载数据包存放数据池 datahubdp2 ,数据池下的存储目录 /hot 、下载后的数据包名称 hotword 。 

* 下载数据包时可以重命名数据包下载后的名称，如若不指定，则默认为网站上的数据包名称。
* 每一个数据项（ item ）下的所有数据包（ tag ）存放在同一个目录下。在第一次下载数据包时指定，后续默认存放与同一目录。  


#####输入  

	datahub pull Hot_searches/Hot_words:Search_popular_vocabulary datahubdp2://hot --destnam=hotword
#####输出
	DataHub : Hot_searches/Hot_words:Search_popular_vocabulary will be pulled soon and can be found as /var/lib/datahub/hot/hotword 

###第六步  通过 job 命令查看下载任务的执行进度
通过 job 命令查看下载任务的执行进度，若执行 100%，则可进入到 /var/lib/datahub/hot 目录下，名称为 hotword 的文件即为本次下载文件。  

* datahub job 显示的是正在执行的任务，所任务已经执行完，则通过 datahub job 命令无法查询到。
* 对于已经执行完成的命令，可用 datahub job -a 命令查询。  

#####输入
	datahub job -a
#####输出
	JOBID   STATUS              	DOWN      	TOTAL     	PERCENT   	TAG       
	-----------------------------------------------------	---------------------------------------------
	9218bec7	downloaded          	972       	972       	100.0%	Hot_searches/Hot_words:Search_popular_vocabulary
###备注
至第六步完成，一个完整的数据下载过程就结束了。下载结果的后续查看途径：  

* 通过 datahub dp datahubdp2 ，查看数据池下的具体的数据文件。  
* 直接下载 tag 时指定的目录 /var/lib/datahub/hot 查看。