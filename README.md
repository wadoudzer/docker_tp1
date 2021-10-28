Ex 1 : Docker & docker-compose installation :

I- Docker installation using the repository :

1- installing the necessary pacakges to allow apt to use a repo over https:
-  apt-get install ca-certificates/curl/gnupg/lsb-release

2- docker's official gpg key: 
-  curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

3- setting up a stable repo : 
-   echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

4- updating 

5- lastest version of docker engine installation :
   - apt install docker-ce docker-ce-cli containerd.io -y

II- Docker-composer installation 

1- docker-compose installation using the stable release :
    - curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
2- applying permissions to the binary
   - chmod +x /usr/local/bin/docker-compose

Ex 2 : New repository creation :

1- git init 
2- files creation 
3- git add . to add created files
4- git commit -m "name>"
5- git push origin master

Ex 3 : Executing a web sever within a docker container :

1-  systemctl start docker

2- docker run -dit --name devopstp -p 8080:80 /home/user/website/:/usr/local/apache2/htdocs httpd:2.4 

2- explanation : - setting an apache2 container named "devopstp" using the image httpd:2.4 from docker hub
                 - -p addressing port
		 - mapping /home/user/website on the container in /usr/local/apache2/htdocs

3- docker ps (checking if container is active)

5- creating the file index.html that serves as a simple web page inside /home/user/website

6- check screenshot.png to see the web page runnning  

EX 4 : Image Building

1- docker build -t webserver

2- docker run -dit -p 80:8080 webserver

3- docker ps 

4- check image.png to see the image running 

EX 5 : Using a database within a docker container
 
1- pulling the mysql image from docker hub : docker pull mysql:latest

2- runnig mysql container : docker run --name mysql-db -d -p 3306:3306 -e MYSQL_ROOT_PASSWORD=<password> mysql:latest

3- pulling the phpmyadmin image from docker : docker pull phpmyadmin/phpmyadmin:latest

4- runnnig phpmyadmin container while linking it to mysql : docker run --name my_phpmyadmin -d --link mysql-db:db -p 8081:80 phpmyadmin/phpmyadmin
 
5- connexion + database and table creation 

6- See image.png
