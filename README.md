# practical2.1
Installation of MySql and MongoDb using docker.
I. Steps to install Docker
    1.Uninstall old versions
        -$ sudo apt-get remove docker docker-engine docker.io containerd runc.

    2.Set up the repository (Update the apt package index and install packages to allow apt to use a repository over HTTPS:)
        -$ sudo apt-get update
        -$ sudo apt-get install \ ca-certificates \ curl \ gnupg \ lsb-release.

    3.Add Docker’s official GPG key:
        -$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

    4.Use the following command to set up the stable repository. 
        -$ echo \"deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" test | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

    1.Install Docker Engine
        -$ sudo apt-get update
        -$ sudo apt-get install docker-ce docker-ce-cli containerd.io

    2.install a specific version of Docker Engine
        -$ apt-cache madison docker-ce

    3.Install a specific version using the version string from the second column
        -$ sudo apt-get install docker-ce=5:18.09.1~3-0~ubuntu-xenial docker-ce-cli=5:18.09.1~3-0~ubuntu-xenial containerd.io
    
    4.Verify that Docker Engine is installed correctly by running the hello-world image.
        -$ sudo docker run hello-world

II. Steps for install mySql in docker 
   1.Pull the MySQL Docker Image
        -$ sudo docker pull mysql/mysql-server:latest
        -$ sudo docker images

    2.Deploy the MySQL Container
        -$ sudo docker run --name=mysql_docker -d mysql/mysql-server:latest
        -$ docker ps

    3.Connect to the MySQL Docker Container
        -$ sudo apt-get install mysql-client
        (Then, open the logs file for the MySQL container to find the generated root password:)
        -$ sudo docker logs mysql_docker (copy the generated password)
        -$ sudo docker -it mysql_docker bash
           type: mysql -uroot -p [password ]

    4.Finally, change the server root password to protect your information:
        -$ mysql> ALTER USER 'root'@'localhost' IDENTIFIED BY '[newpassword]';

III. Steps to install MongoDb
 1.Install the current stable release of Docker Compose.
        -$ sudo curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

 2. Apply executable permissions for the downloaded binary.
    -$ sudo chmod +x /usr/local/bin/docker-compose

 3.Verify the Docker Compose installation.
    -$ docker-compose --version
    -$ docker run -d -p 27017:27017 --name mongodb mongo:4.0.4

    Setting up a MongoDB container
    -$ sudo docker search mongodb
    -$ tree mongodb 
    -$ sudo docker-compose up -d


            


    
