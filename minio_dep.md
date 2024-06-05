
1.进入到/opt目录，创建minio文夹

	cd /opt
	mkdir minio   # 创建minio文件夹
	cd minio      # 进入到目录



2.下载minio
	wget https://dl.minio.io/server/minio/release/linux-amd64/minio

3.创建minio.log文件
	touch minio.log

4.授权minio
	touch minio.log

6.修改环境变量
	vim /etc/profile
	最后添加两行内容：
		export MINIO_ROOT_USER=lch
		export MINIO_ROOT_PASSWORD=fuckworld

7.刷新环境遍量
	source /etc/profile  # 编辑完记得刷新

8.配置minio启动脚本
	vim start.sh
		nohup /opt/minio/minio server  /opt/minio/data --console-address ":62222" > /opt/minio/minio.log 2>&1 &

9.关闭防火墙或者开放62222和9000端口

10.执行启动脚本

13.打开minio  浏览器输入ip:62222即可    或者linux下载minio客户端

13分支
	wget https://dl.min.io/client/mc/release/linux-amd64/mc    下载minio客户端（mc）
	chmod +x mc	 给执行权限
	mc alias set myminio http://minio-server:9000 ACCESS_KEY SECRET_KEY    配置 MinIO 客户端
	myminio是客户端这里设置的一个别名	
	
	一些操作
	mc ls myminio  			列出所有存储桶
	mc mb myminio/mybucket          创建一个新的存储桶
 	mc cp myfile.txt myminio/mybucket    上传文件到存储桶
	mc cp myminio/mybucket/myfile.txt .   下载文件从存储桶
	mc rm myminio/mybucket/myfile.txt     删除存储桶中的文件
	mc ls myminio/mybucket      		列出存储桶中的文件
	




