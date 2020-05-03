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

TO RESOLVE CRSF ISSUE 
_no valid crumb error_
```
wget --user=admin --password=admin --auth-no-challenge -q --output-document - 'http://localhost:8080/crumbIssuer/api/xml?xpath=concat(//crumbRequestField,":",//crumb)'
```

TO INCLUDE MAVEN IN THE BUILD 
There are many options:

1. is to include mavins code in the build
```
RUN apt-get update && apt-get install -y maven 
```
2. login to the running jenkins container to run
```
sudo docker exec -u root -t -i [container-id] bash
```
run 
```
apt-get update & apt-get install
```
You will have Maven running 
