# docker_kafka_demo  
----------------------------------------------------------------------------------  
## pre-requisite  

create two docker nodes  
**$ docker-machine create manager1**  
**$ docker-machine create worker1**  

create swarm node  
**$ docker-machine ssh manager1**  
**$ docker swarm init --advertise-addr <manager1_ip>**  
  
**$ docker-machine ssh worker1**  
**$ docker-machine join-token (worker|manager)**  
  
**$ docker-machine env manager1**  
  
in windows C:\Windows\System32\drivers\etc\hosts  

&lt; manager1_ip &gt; manager1  
&lt; worker1_ip &gt; worker1  
  
-----------------------------------------------------------------------------------  
## deploy the docker file  
  
**$ docker stack deploy --compose-file docker-compose.yaml stacker**  
**$ docker ps -a**  
**$ docker stack services stacker**  
**$ docker stack ps stacker**  
  
-----------------------------------------------------------------------------------  
## ssh into kafka container  

**$ docker exec -it &lt;kafka_container_id&gt; sh**  
**# kafka-console-producer.sh --borker-list localhost:9092 --topic myTopic**  
    **&gt;**  
type in the message it will be seen in the next step from windows command line  
-----------------------------------------------------------------------------------  
  
## from local windows command line  
  
install kafka on windows  
  
**&gt; .\bin\windows\kafka-console-consumer.bat --bootstrap-server manager1:9094 --topic myTopic --from-beginning**  

