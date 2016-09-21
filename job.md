##6.3 job	任务管理
<hr style=" border:4px solid #A9A9A9;" /> 
数据下载任务的执行情况，可以通过job命令来查看。  
###6.3.1 查看正在执行的任务  
查看正在执行的任务，可以看到任务 id 、任务状态、任务完成 百分比等等。
#####输入
	datahub job 
#####输出  
	%JOBID   %STATUS  %DOWN   %TOTAL    %PERCENT   %TAG       	
#####例子  
	bash-3.2# datahub job 
	JOBID   	STATUS      DOWN      	TOTAL     	PERCENT   	TAG       
	------------------------------------------------------------------------------------------------
	ebcda4c5	downloading   77610400  	443004623 	17.5%	Location_information/Cell03:gt20160615
	35ba309b	downloading   10218600  	374033595 	2.7%	Location_information/Cell03:gt20160620   
###6.3.2 查看某个具体的任务    
查看具体任务（ jobid ）的执行情况。
#####输入  
	datahub job $jobid  
#####输出
	%JOBID   %STATUS  %DOWN   %TOTAL    %PERCENT   %TAG
#####例子s
	bash-3.2#  datahub job ebcda4c5
	JOBID   	STATUS      	DOWN      	TOTAL     	PERCENT   	TAG       
	--------------------------------------------------------------------------------------------------
	ebcda4c5	downloading    226542400 	443004623 	51.1%	Location_information/Cell03:gt20160615  
###6.3.3 查看全部任务  
查看全部任务，包括执行完成和未完成的。
#####输入  
	datahub job --all   
#####输出
	%JOBID   %STATUS  %DOWN   %TOTAL    %PERCENT   %TAG
#####例子s
	
	bash-3.2#  datahub job --all
	JOBID   	STATUS        DOWN      	TOTAL     	PERCENT   	TAG       
	--------------------------------------------------------------------------------------------------
	9218bec7	downloaded          	972       	972       	100.0%	Hot_searches/Hot_words:Search_popular_vocabulary
	7b045fc5	downloaded          	972       	972       	100.0%	Hot_searches/Hot_words:Search_popular_vocabulary
	57deff09	downloaded          	972       	972       	100.0%	Hot_searches/Hot_words:Search_popular_vocabulary
	15fed8ad	downloaded          	972       	972       	100.0%	Hot_searches/Hot_words:Search_popular_vocabulary
	ebcda4c5	downloaded          	443004623 	443004623 	100.0%	Location_information/Cell03:gt20160615
	35ba309b	downloaded          	374033595 	374033595 	100.0%	Location_information/Cell03:gt20160620   
###6.3.4 删除全部未完成任务   
 删除全部任务。此处的删除未逻辑删除。
#####输入  
	datahub job rm --all   
#####输出
	%msg
#####例子  
	bash-3.2# datahub job rm --all
	DataHub : Remove all jobs OK.
 
###6.3.5 删除某个具体任务  
删除某个（ jobid ）任务。
#####输入  
	datahub job rm $jobid   
#####输出
	%msg
#####例子
	bash-3.2# datahub job rm 7aae6a24
	DataHub : job 7aae6a24 deleted.