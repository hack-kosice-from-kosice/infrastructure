# Pipeline steps

1. Checkout main service source code from Github repository

```
mvn clean install
scp -i "/var/jenkins_home/hack-kosice-ec2.pem" target/main-service-0.0.1-SNAPSHOT.jar ubuntu@ec2-18-159-195-207.eu-central-1.compute.amazonaws.com:/home/ubuntu/main-service-app
ssh -i "/var/jenkins_home/hack-kosice-ec2.pem" ubuntu@ec2-18-159-195-207.eu-central-1.compute.amazonaws.com
cd /home/ubuntu/main-service-app
kill $(cat ./pid.file)
java -jar main-service-0.0.1-SNAPSHOT.jar & echo $! > ./pid.file
```
