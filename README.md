Docker [Apache Spark](https://spark.apache.org) base image optimized for Machine Learning with Python and PySpark

spark
A debian:stretch based Spark container. Use it in a standalone cluster with the accompanying docker-compose.yml, or as a base for more complex recipes.


Standalone Spark cluster running one Spark Master and two Spark workers

Build Spark applications in Python to run on a Spark cluster


## Spark Docker

This repo 
 - python: pyspark +
 - sd
Spark 3.0.1 for Hadoop 3.2 with OpenJDK 8 


 ## Howto

 The image 

 The script will finish displaying the Hadoop and Spark admin URLs:
Hadoop info @ nodemaster: http://172.18.1.1:8088/cluster
Spark info @ nodemaster : http://172.18.1.1:8080/
DFS Health @ nodemaster : http://172.18.1.1:9870/dfshealth.html

## Spark Docker
To create a simplistic standalone cluster with docker-compose:

docker-compose up
The SparkUI will be running at http://${YOUR_DOCKER_HOST}:8080 with one worker listed. To run pyspark, exec into a container:

docker exec -it docker-spark_master_1 /bin/bash
bin/pyspark


 ## Spark standalone 
 ```
 docker run
 ```
