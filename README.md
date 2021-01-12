# Docker-spark-python-buster
![GitHub repo size](https://img.shields.io/github/repo-size/itertop/docker-spark-python-buster)

Docker [Apache Spark](https://spark.apache.org) base image for Machine Learning with Python 3, Hadoop and PySpark.

The repo allows you to build a docker image and to start two containers with standalone Spark cluster  - one master and one slave.
There's also an option to run a container with Spark worker attached to the existing master. 

## Prerequisites
*   Docker. Has been tested on Linux, macOS, or Windows (with WSL2).
*   The out-of-the-repo configuration uses the following ports, so make sure they are free or update configuration files once cloned.
    *   For both images: 4040, 6066, 7077, 8080.
    *   Master: 7001, 7002, 7003, 7004, 7005.
    *   Slave: 7012, 7013, 7014, 7015.

## Installation 
Clone this repo to get the Dockerfile, composer and configuration files. 
```bash
git clone https://github.com/itertop/docker-spark-python-buster.git &&
cd docker-spark-python-buster
```

## Running slave
This option is a nice kickstarter if you got a machine with Docker and want to get a Spark worker running on it without spending time on the installation.
  
Once you got a master running at `spark://spark-master:7077` run a Spark slave in a container:
```bash
docker-compose -f docker-compose-slave.yml up
```
That will pull a Docker image [itertop/spark from Docker Hub](https://hub.docker.com/repository/docker/itertop/spark), which is being built automatically from this repo and start a container `spark-slave-2`.

If your master is running not at `spark://spark-master:7077`, run the Spark slave with the right address executing the following command:
```bash
docker exec spark-slave-2 bin/spark-class org.apache.spark.deploy.worker.Worker spark://<correct address>:<correct port>
``` 

## Bulding the Docker image on your own and running both Spark Master and Slave

Once cloned, get both containers up and running with docker-compose:
```bash
docker-compose up
```
That's it! 
That will take some time to build, though.

## Monitoring
Monitor your Spark cluster using standard Apache Spark web UI:
http://localhost:8080/
