# Servers Metrics & Logs
## Project Overview:
We have a cluste of 10 servers hosting a cloud storage website where users can upload and store different types of files. Beside these 10 servers we have a load balancer that acts as the main gateway for our website. We have deployed agents to these 10 servers and load balancer to collect metrics and logs.

Design a **Multi Node Kafka Cluster** where you would have two topics. One topic for the agents of the 10 servers which monitor resources consumption, the other topic for the agent of the load balancer which monitor logs. We have provided you with a java program which should simulate the agents sending data to the two topics.

After that, you need to build a consumers - in whatever language you would prefer- for the metrics that should send them to a relational database. For the logs, write a spark application that consumes them and calculate a moving windows count of every operation (no of successful GET operations, no of successful POST operations, no of failed GET operations, no of failed POST operations) every 5 mins and store the result into a hadoop system.

## Resources:
Java program to simulate the agents. You just need to install maven on your system and then run ```mvn exec:java``` to run the program

## Requirements:
1. Create the topics in the kafka cluster
2. Write consumer for the metrics
3. Write Spark application for logs

## Key Deliverables:
-	A document with the configuration of each broker and topic
-	Code for consumer and Spark application

## steps for the approach:
1- run (docker-compose up -d) to create kafka container
2- create the 2 topics (metrics and logs) from file --->creation of topics 
3- go to file App.java and change these 2 lines (Balancer b = new Balancer("logs") (Server s = new Server(i,"metrics") instead of (Balancer b = new Balancer("test-topic3") (Server s = new Server(i,"test-topic4")
4- create mysql container
5- go inside mysql container and create (metrics_logs database) and then create the table (metric)
6- run the producer (mvn exec:java)
7- if you want to see the messages go inside kafka container (docker exec -it kafka bash) then (cd /opt/kafka) then (bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic metrics --from-beginning)
8- install the requirements (pip install -----)
9- run the consumer (which is wrote in jypter-notbook)
10 - go inside the mysql container one more time and you will see the metrics topics is filled with data

