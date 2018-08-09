Install Mongo-cluster with docker-compsoe
======
Mongo 的群集安裝
------
目前分成兩個部分
1. docker-compose : 這個資料夾放docker-compose的yml檔
2. image-build : docker image 的Dockerfile

                附註 : 未來會放上以kubernetes平台上的mongocluster

docker-compose運行部分
------
1. 選擇host-architecture
2. 分別到你要安裝mongo的安台機器運行host1 , host2 , host3底下的docker-compose-hostX-total.yaml <br>
                docker-compose -f docker-compose-hostX-total.yaml up -d
3. 運行host-architecture/docker-compose-cluster-init.yaml (只要能連到步驟2的任一機器都可運行這初始化容器)<br>
                docker-compose -f docker-compose-cluster-init.yaml up -d

Mongo cluster 的實現目前是以shard cluster
------
每台機器上都會有mongos , mongo-config , mongo-shard三個容器運行
初始化的3個容器會需約20秒的時間運行完畢 , 運行完畢後會自動關閉
