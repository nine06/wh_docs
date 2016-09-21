##6.9 subs  订购管理   
<hr style=" border:4px solid #A9A9A9;" />     
用户在 DataHub 网站（ hub.dataos.io ）订购数据后，可登录客户端，通过 subs 命令在客户端查看已经订购的数据。
###6.9.1 查看所有订购的 repo/item
#####输入
	datahub subs
#####输出  
    $REPOSITORY/$ITEM                  $TYPE       	
#####例子   
	bash-3.2#  datahub subs  
	REPOSITORY/ITEM                       TYPE        STATUS     
	Hot_searches/Hot_words                file        online     
	Location_information/Cell03           file        online     
	Internet_stats/Ecommerce_goods        file        online      
	。。。。。。

###6.9.2 查看订购的某个 repo/item 下的 tag
#####输入
	datahub subs $REPOSITORY/$ITEM
#####输出  
    $REPOSITORY/$ITEM:$TAG    $UPDATETIME                            $COMMENT          $STATUS     
其中 status 为 normal 状态的 tag 能正常下载， unnormal 状态的 tag 需数据服务提供方修复该 tag 后方可正常下载。   	
#####例子   
	bash-3.2#  datahub subs Location_information/Cell03  
	REPOSITORY/ITEM:TAG                           UPDATETIME                            COMMENT                STATUS     
    Location_information/Cell03:gt20160220        2016-02-23 11:41:19|5个月前         Size:166.12 MB        NORMAL       
	Location_information/Cell03:gt20160221        2016-02-23 10:43:22|5个月前         Size:599.69 KB        NORMAL     
	Location_information/Cell03:gt20160223        2016-04-11 10:51:58|3个月前         Size:147.89 MB        NORMAL     
	Location_information/Cell03:gt20160224        2016-04-11 10:51:58|3个月前         Size:141.83 MB        NORMAL     
	Location_information/Cell03:gt20160225        2016-04-11 10:51:58|3个月前         Size:144.99 MB        NORMAL     
	Location_information/Cell03:gt20160226        2016-04-11 10:51:58|3个月前         Size:155.29 MB        NORMAL     
	Location_information/Cell03:gt20160227        2016-04-11 10:51:58|3个月前         Size:179.23 MB        NORMAL     
	Location_information/Cell03:gt20160228        2016-04-11 10:51:59|3个月前         Size:174.44 MB        NORMAL     
	Location_information/Cell03:gt20160229        2016-04-11 10:51:59|3个月前         Size:179.45 MB        NORMAL     
	Location_information/Cell03:gt20160301        2016-04-11 10:51:59|3个月前         Size:173.52 MB        NORMAL   	  
	。。。。。。