# AWS EC2 Installation instruction

1. Launch AWS instance with Ubuntu OS

2. Setup ssh config to connect to it

```
Host hack-kosice-ec2
    User ubuntu
    IdentityFile </path/to/pem-file>
    HostName <ec2-instance-public-dns-name>
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
 - [Instructions](https://www.digitalocean.com/community/tutorials/how-to-install-jenkins-on-ubuntu-20-04)

6. Maven installation 
```
sudo apt install maven
```
