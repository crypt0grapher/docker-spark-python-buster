# Docker-spark-python-buster
![GitHub repo size](https://img.shields.io/github/repo-size/itertop/docker-spark-python-buster)

Docker [Apache Spark](https://spark.apache.org) base image for Machine Learning with Python 3, Hadoop and PySpark
The repo allows you to build a docker image and to start two containers with standalone Spark cluster  - one master and one slave.
There's also an option to run a container with Spark worker attached to the existing master. 

## Prerequisites
*   Docker, has been tested on Linux, macOS, or Windows (with WSL2 Linux).
*   The out-of-the-box configuration uses the following ports, so make sure they are free or update configuration files once cloned.
    *   For both images: 4040, 6066, 7077, 8080.
    *   Master: 7001, 7002, 7003, 7004, 7005.
    *   Slave: 7012, 7013, 7014, 7015.

## Installation 
To get the repository, clone the repo to get the Dockerfile, composer and configuration files. 
```bash
git clone https://github.com/itertop/docker-spark-python-buster.git
cd docker-spark-python-buster
```

## Running slave
> This option is a nice kickstarter if you got a machine with Docker and want to get a Spark worker running on it without spending time on the installation.
  
Then, if you got a master running at `spark://spark-master:7077` and want to run a Spark slave:
```bash
docker-compose -f docker-compose-slave.yml up
```
That will pull a docker image [itertop/spark from Docker Hub](https://hub.docker.com/repository/docker/itertop/spark), which is being built automatically from this repo and start a container `spark-slave-2`.

If you got master running at another address, execute the command with the right address inside a container:
```bash
docker exec spark-slave-2 bin/spark-class org.apache.spark.deploy.worker.Worker spark://spark-master:7077
``` 

## Bulding the image on your own and running maser and slave
> Flexible and configurable 

Get both containers running with docker-compose:
```bash
docker-compose up
```
That's it! 

## Monitoring
Monitor your Spark cluster:
http://localhost:8080/

## Configuration 
The image is suitable both for Master and Workers, and the following commands are executed automatically:

Running master with:
```bash
docker exec spark-master bin/spark-class org.apache.spark.deploy.master.Master -h spark-master
```
Running worker with:
```bash
docker exec spark-slave-1 bin/spark-class org.apache.spark.deploy.worker.Worker spark://spark-master:7077
```