# AWS EC2 Installation instruction

1. Launch AWS instance with Ubuntu OS

2. Setup ssh config to connect to it

```
Host hack-kosice-ec2
    User ubuntu
    IdentityFile /path/to/pem-file
    HostName ec2-18-159-195-207.eu-central-1.compute.amazonaws.com
```

3. After that it is possible to connect to instance using

```
ssh hack-kosice-ec2
```

4. Install Docker related things on EC2 instance
 - [Docker installation](https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository)
 - [Docker post installation](https://docs.docker.com/engine/install/linux-postinstall/#:~:text=The%20Docker%20daemon%20binds%20to,runs%20as%20the%20root%20user.&text=When%20the%20Docker%20daemon%20starts,members%20of%20the%20docker%20group.)
 - [Docker compose installation](https://docs.docker.com/compose/install/)

5. Jenkins installation
 - Using `docker-compose up`
 - Initial Jenkins password:
```
 docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword
``` 

6. Maven installation 
```
sudo apt install maven
```

7. Jenkins build setup
```
mvn clean install
scp -i "/var/jenkins_home/hack-kosice-ec2.pem" target/main-service-0.0.1-SNAPSHOT.jar ubuntu@ec2-18-159-195-207.eu-central-1.compute.amazonaws.com:/home/ubuntu/main-service-app
ssh -i "/var/jenkins_home/hack-kosice-ec2.pem" ubuntu@ec2-18-159-195-207.eu-central-1.compute.amazonaws.com
cd /home/ubuntu/main-service-app
kill $(cat ./pid.file)
java -jar main-service-0.0.1-SNAPSHOT.jar & echo $! > ./pid.file
```
