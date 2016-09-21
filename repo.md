##6.8 repo  数据主题管理   
<hr style=" border:4px solid #A9A9A9;" />    
用户登录前，可通过 repo 命令查看所有免费的数据，登录后通过 repo 命令可以查看所有具备写权限的数据主题（ repository，简称 repo ）。
###6.8.1 查看免费数据主题（ repo ）
登录前，通过 repo 命令查看免费数据主题。
#####输入
	datahub repo
#####输出  
    $REPOSITORY      	
#####例子   

	bash-3.2#  datahub repo
	REPOSITORY      
	Internet_stats  
	Transportation_of_beijing
	Location_information
	Mobile_phone    
	Education_of_beijing
	guangzhou       
	House_price     
	Ahares_OPC_HDA  
	Base_station_location
	Hot_searches    
	shanghai_soda   
	Health_care_of_beijing
	shipsite_test   
	chinaidea       
	Tourism         
	。。。。。。

###6.8.2 查看某个免费数据主题（ repo ）下的数据集（ ietm ）  
登录前，通过 repo 命令查看某个免费数据主题下的数据集。
#####输入
	datahub repo $REPOSITORY
#####输出  
    $REPOSITORY/$DATAITEM   	
#####例子   

	bash-3.2#  datahub repo Internet_stats
	REPOSITORY/DATAITEM
	Internet_stats/Film_and_television
	Internet_stats/Ecommerce_goods
	Internet_stats/Music
	Internet_stats/Books
	Internet_stats/Cars

###6.8.3 查看具备写权限的数据主题（ repo ）  
登录后，通过 repo 命令查看具备写权限的数据主题。
#####输入
	datahub repo
#####输出  
    $REPOSITORY      	
#####例子   

	bash-3.2#  datahub repo
	REPOSITORY      
	Mobile_APP      
	datahubrepo1      

###6.8.4 查看具备写权限数据主题（ repo ）下的数据集（ ietm ）  
登录后，通过 repo 命令查看具备写权限数据主题下的数据集。
#####输入
	datahub repo $REPOSITORY
#####输出  
    $REPOSITORY/$DATAITEM   	
#####例子   

	bash-3.2#  datahub repo Mobile_APP
	REPOSITORY/DATAITEM
	Mobile_APP/APP_information
   
