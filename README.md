# JENKINS TO CONNECT WITH DOCKER ON HOST

## Jenkins docker
* Jenkins CI with docker client


Do git clone

```
docker build -t jenkins-docker .
```
## STOP Any other running jenkins container
```
docker stop jenkins
docker rm jenkins
```

List jenkns dir to view content
```
ls /var/jenkins_home
```

```
sudo docker run -p 8080:8080 -p 50000:50000 -v /var/jenkins_home:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock --name jenkins -d jenkins-docker
```
