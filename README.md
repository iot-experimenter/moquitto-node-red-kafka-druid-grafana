# install mosquito - node-red - kafka - druid - grafana - portainer - kafka manager - turnilo with docker on a synology 

thanks to piwi's tech talk `Docker 101: Docker on Synology and Portainer`


* first install portainer... see great video https://www.youtube.com/watch?v=ToL5SPFUPaQ&t=2s`
* then make next directory's under docker directory :
    *  /mosquitto/config
    *  /node-red
    *  /node-red/data
    *  /kafka/logs
    *  /kafka/data
    *  /kafka-manager/conf
    *  /druid/storage
    *  /grafana/data
    *  /enviroment
    * / turnilo
    
* change ip adress in docker-compose to the ip of your NAS : `KAFKA_ADVERTISED_HOST_NAME: 192.168.1.201` 
* then run docker-compose with `sudo docker-compose up -d --build`

Connect on your local network to the dashboards with the ip of your NAS; in my case it is `192.168.1.201` :
* http://192.168.1.201:9000/#/containers
* http://192.168.1.201:8888/unified-console.html
* http://192.168.1.201:1880/
* http://192.168.1.201:9999/
* http://192.168.1.201:3000/
* http://192.168.1.201:9090/

-> kafka-manager `http://192.168.1.201:9999/`
create a new cluster...
give it a name 
connect to : `zookeeper:2181`
create a new topic with kafka-manager


-> ingestion of data from kafka in druid :
* bootstrap servers :  `192.168.1.201:9092`
write ingestion spec with wizard

connect grafana to druid :
http - url : 
			http://192.168.1.201:8082
