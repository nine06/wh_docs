##6.6 pub  发布数据   
<hr style=" border:4px solid #A9A9A9;" />    
在 DataHub 网站发布数据主题（ repo ）后，可通过 pub 命令在客户端发布数据集（ item ）、发布数据包（ tag ）。
###6.6.1 发布item
在发布 item 时需要指定在哪个 repo 下发布，item 所在的 datapool ，以及 datapool 下的目录，item 的接入属性  （ accesstype ） ，item 描述（ comment ），数据类型（ supplystyle）。

* accesstype 可为 private 或者 public 。默认为 private。
* supplystyle 可为流式（ flow ）、 api 、批量（ batch ）中的一种。默认为批量类型。

 
#####输入
	datahub pub $REPOSITORY/$DATAITEM $DATAPOOL://$LOCATION --accesstype=[ public、 private]  --comment=$comment   --supplystyle=[ flow、 api、batch]
#####输出  
    %msg       	
#####例子  
    bash-3.2#datahub pub datahubrepo1/datahubitem1 datahubdp1://decitem1 --comment="帮助文档样例item描述" --supplystyle=private --accesstype=batch
	DataHub : Successed in publishing.  


###6.6.2 发布tag
在发布 tag 时需要指定在哪个 repo/item 下发布 tag ，源文件名称， tag 描述（  comment ）。描述若未指定，则默认为空。      

* tag 源文件必须位于 item 目录下。  
* 每个 item 下的 tag 必须为同一种类型，且必须为 item 发布时指定的 supplystyle ，可以为流式（ flow ）、 api 、批量（ batch ）中的一种。
 

#####输入
	datahub pub $REPOSITORY/$DATAITEM:$Tag $TAGDETAIL --comment=$comment
#####输出  
    %msg       	
#####例子  
    bash-3.2# datahub pub datahubrepo1/datahubitem1:datahubtag1 datahubtag --comment=帮助文档样例tag描述
	DataHub : Successed in publishing.  

