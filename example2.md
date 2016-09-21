##7.2 应用场景一 ： 发布数据
<hr style=" border:4px solid #A9A9A9;" />
下面介绍从 广数DataHub 网站发布名为 datahubrepo1 的数据主题，在客户端发布名为 datahubitem1 的数据集、名为 datahubtag1 的数据包。

###第一步 在 广数DataHub 网站发布名为 datahubrepo1 的数据主题
在网站上发布名为 datahubrepo1 的数据主题  

* 在 广数DataHub 网站（ http://www.gzbdex.com ）上我的发布 中查看，确认 datahubrepo1 的发布状态。  

###第二步 通过 longin 命令登录 Client 端
#####输入
	datahub login
#####输出	  
	login as: ********@*******.com
	password: ******
	DataHub : login success.  
	
###第三步 设置端口
端口（ Entry Point ）需要在发布数据时设置，供后续数据需求方在得到认证和鉴权后获得下载数据的入口。端口包括协议、ip 、port 三部分。设置协议为 http、 ip 为192.168.3.255、端口为1000。
#####输入（设置端口）  
	datahub ep http://192.168.3.255:1000
#####输出
 	OK. your entrypoint is: http://192.168.3.255:1000
	The entrypoint is setted successfully.  You can check whether it is available in one minute.
#####输入（确认端口有效性）
	datahub ep
#####输出
	http://192.168.3.255:8088 available。

	
  

###第四步 指定数据的存放目录（数据池， datapool ）
在本地创建一个名叫 datahubdp1 的数据池，指定存储类型为文件（ file ），路径为 /var/lib/datahub 。 

* 对于新用户，若无数据池，先创建数据池，现支持  file 、 S3 、 HDFS  等三种类型。对于已经创建过数据池的用户，可直接进入到第五步。  


#####输入  

	datahub dp create datahubdp1 file:///var/lib/datahub
#####输出
	DataHub : Datapool has been created successfully. 	Name:datahubdp1 Type:file Path:/var/lib/datahub. 

###第五步 在客户端发布名为 datahubitem1 的数据集
在客户度端发布名为 datahubitem1 的数据集，指定发布在数据主题datahubrepo1下，存放目录为数据池 datahubdp1 下的 decitem1 ，描述为"帮助文档样例 item 描述"，属性为私有，类型为批量（ batch ）类型。
#####输入
	datahub pub datahubrepo1/datahubitem1 datahubdp1://decitem1 -m="帮助文档样例item描述" -t=private -s=batch
#####输出
	Successed in publishing.
   
######说明：在发布 DataItem 之前，可以在其对应的目录里创建、编译三个文件： sample.md 、 eta.md 、price.cfg ，这三个文件的作用分别是：

 - sample.md 用于保存 Markdown 格式的样例数据，如果没有此文件，程序会读取此目录下的第一个 Tag 文件的前十行，作为样例数据，发布到 Item 的详情里。

 - meta.md 用于保存 Markdown 格式的元数据。元数据在 DataHub 页面进行编辑和保存。

 - price.cfg 用于保存 JSON 格式的资费计划，用来明确此 DataItem 的资费。资费在 DataHub 页面进行编辑和保存。

格式如下：

    {
    	"price":[
    				{
                    	"times":10,
                        "money": 5,
                        "expire":30
                    },
                    {I
                    	"times": 100,
                        "money": 45,
                        "expire":30
                    },
                    {
                    	"times":500,
                        "money": 400,
                        "expire":30
                    }
                ]
    }


其中 times 代表可 pull 次数， money 代表价格， expire 代表有效期。
   
   
   
###第六步 在客户端发布名为 datahubtag 的数据包
在客户端指定发布名为 datahubtag1 的 tag 。 tag 的存放地址在其对应的 item 目录 datahubdp1://decitem1 下，文件名为 datahubtag.png ，发布时将其描述设置为帮助文档样例描述。
#####输入
	datahub pub datahubrepo1/datahubitem1:datahubtag1 datahubtag.png -m=“帮助文档样例tag描述”
#####输出
	 Successed in publishing.

####备注
至第六步完成，一个完整的数据发布过程就结束了。发布的结果后续查看 ：  
  
* 可通过命令行 datahub repo datahubrepo1/datahubitem1 查看。  
* 或者到 DataHub 网站 hub.dataos.io ，“我的发布”中查看。