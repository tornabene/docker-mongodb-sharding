docker-mongodb-sharding
=======================
### Learning Docker http://docker.io/ by creating a mongodb sharding container.

### To build:
	sudo docker build -t tornabene/docker-mongodb-sharding .

### To run:



	sudo docker run  -P --name cfg1 -d tornabene/docker-mongodb  --noprealloc --smallfiles --configsvr --dbpath /data/db --port 27017
	sudo docker run  -P --name cfg2 -d tornabene/docker-mongodb  --noprealloc --smallfiles --configsvr --dbpath /data/db --port 27017
	sudo docker run  -P --name cfg3 -d tornabene/docker-mongodb  --noprealloc --smallfiles --configsvr --dbpath /data/db --port 27017
	
	 sudo docker inspect cfg1
    sudo docker inspect cfg2
    sudo docker inspect cfg3

    sudo docker  run -d --name mongo.ntipa.it  -p 27017:27017 tornabene/docker-mongodb-sharding  --port 27017 --configdb  "<IP_of_container_cfg1>:27017,<IP_of_container_cfg2>:27017,<IP_of_container_cfg3>:27017"
    
    *** ATTENZIONE <IP_of_container_cfg1>:27017,<IP_of_container_cfg2>:27017,<IP_of_container_cfg3>:27017 non deve contenere spazi
  
    mongo --port 
    sh.addShard("rs1/<IP_of_rs1_srv1>:27017")
    sh.addShard("rs2/<IP_of_rs2_srv1>:27017")
    sh.status()

	