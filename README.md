# images-garbage-cleaner-k8s

The deployment is used to remove all the untagged images on Kubernates Cluster.

``` yml
git clone https://github.com/kumargaurav522/images-garbage-cleaner-k8s.git/
cd images-garbage-cleaner-k8s
kubectl apply -f deployment.yaml
```

Create Docker Image;
1) Make Dockerfile

The Docker image is created with instructions written in the Dockerfile. So we use official ubuntu:18.04 base image, install docker.io package, copy dockerimages-cron and script.sh files to cron.d directory and root directory respectively. Then we give execution rights on the cron job and apply cron job and on last line Run the command on container startup.

``` yml
docker build -t kumar/docker_cleanup:latest .
```
Push Docker Image
``` yml
docker push kumar/docker_cleanup:latest
```

Apply on k8s cluster

``` yml
kubectl apply -f  deployment.yaml
```
