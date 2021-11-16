# IBMMQ-Prometheus-Sample-Env
IBM MQ Test environment exposing prometheus metrics

These steps allow you to spin up a test environment with a container running an IBM MQ developer instance and a MQ prometheus exporter running on a second container.

1. Creating the Exporter container image:

```shell
# Create a directory to host the GitHub repo if you don’t have one already
cd my-workspace
mkdir ibm-messaging
cd ibm-messaging

# Clone the metrics repo onto your local machine
git clone git@github.com:ibm-messaging/mq-metric-samples.git

# Building the image
cd mq-metric-samples/scripts
./buildRuntime.sh mq_prometheus

Building container mq-metric-samples-gobuild:5.2.3
...
Building mq_prometheus

Compiled programs should now be in /Users/myuser/tmp/mq-metric-samples/bin
...
=> exporting to image 
=> => exporting layers         
=> => writing image sha256:1333ef...69d7c                     
=> => naming to docker.io/library/mq-metric-prometheus:5.2.3
```

The image is now created locally:

```shell
docker images 

REPOSITORY                TAG     IMAGE ID       CREATED         SIZE
mq-metric-prometheus      5.2.0   13332223dbe2   2 minutes ago   202MB
```

Returning to this repo, run

```shell
docker composer up
```

Open a web browser and prometheus metrics are exposed on http://localhost:9157



