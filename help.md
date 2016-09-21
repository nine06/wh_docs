##6.11 help 帮助  
<hr style=" border:4px solid #A9A9A9;" />
查看客户端命令的帮助。
###6.11.1 查看帮助
#####输入
	datahub $command --help  
	或者  
	datahub $command -h
	 
#####输出  
    %msg       	
#####例子  
    bash-3.2# datahub pull -h
	Usage:
	datahub pull [REPO]/[ITEM][:TAG]  DATAPOOL[://LOCATION]  [OPTION]

	Pull a tag from the provider.

	Option:

	--destname, -d        Indicate the name that tag will be stored as

	datahub pull [REPO]/[ITEM] DATAPOOL [OPTION]

	set or cancel the automatical pulling of tags.

	Options:

	--automatic, -a        Pull the new tags of a dataitem automatically
	--cancel, -c           Cancel the automatical pulling of a dataitem