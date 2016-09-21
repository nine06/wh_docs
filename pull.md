##6.7 pull  下载数据   
<hr style=" border:4px solid #A9A9A9;" />   
在 DataHub 网站订购数据（ repo/item ）后，可通过客户端（ Client ）下载数据包（ tag ）。
###6.7.1 下载某个指定 tag
下载 tag 时，需要明确 tag 存放的数据池（ datapool ），以及数据池下的路径，可重命名下载的 tag 。    

* 下载数据包时可以重命名下载后的名称( --destname )，如若不指定，则默认为下载后的名称为 tag 名称。
* 每一个数据项（ item ）下的所有数据包（ tag ）存放在同一个目录下。在第一次下载数据包（ tag ）时指定存放目录，后续默认存放于同一目录下。所以每个 item 下非第一个被下载的 tag ，在下载时可以省略指定数据池下的目录。 

#####输入
	datahub pull $REPOSITORY/$DATAITEM:$TAG $DATAPOOL[://$LOCATION] --destname=$destname
#####输出  
    %msg       	
#####例子  
下载 Location_information/Cell03 下的第一个 tag   

	bash-3.2# datahub pull Location_information/Cell03:gt20160615 datahubdp1://location --destname=0615
	DataHub : Location_information/Cell03:gt20160615 will be pulled soon and can be found as /var/lib/datahub/location/0615  
下载 Location_information/Cell03 下的第二个tag  

	bash-3.2# datahub pull Location_information/Cell03:gt20160620 datahubdp1 --destname=0620
	DataHub : Location_information/Cell03:gt20160620 will be pulled soon and can be found in /var/lib/datahub/Location_information_Cell03/0620 
 

####6.7.2 自动下载某个 item 内的 tag  
在 DataHub 网站订购数据（ repo/item ）后，可在客户端（ Client ）将其设置为自动下载，则后续该 item 内，有增加的数据包（ tag ） 时，会自动下载。      

* 此时需要指定自动下载到那个数据池（ datapull ）内，数据池内的下载名称默认为数据集（ item ）名称。    
* 在设置自动下载后，需保持客户端 （ Client ）为启动状态。

#####输入  
	datahub pull $REPOSITORY/$DATAITEM %DATAPOOL --automatic
#####输出
	%msg  
#####例子
	bash-3.2# datahub pull Meteorological/Synthetic_pollution_index datahubdp1 --automatic
	DataHub : Meteorological/Synthetic_pollution_index will be pulled automatically.


###6.7.3 取消自动下载某个 item 内的 tag
#####输入
	datahub pub $REPOSITORY/$DATAITEM %DATAPOOL --cancel
#####输出  
    %msg       	
#####例子  
    bash-3.2#  datahub pull Meteorological/Synthetic_pollution_index datahubdp1 --cancel
	DataHub : Cancel the automatical pulling of Meteorological/Synthetic_pollution_index successfully.  

