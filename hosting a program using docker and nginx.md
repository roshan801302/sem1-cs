### GET STARTED DOCKER

# Docker1) Install Docker on your VM with the help of the following commands (only for Ubuntu and Debian Operating Systems)

  install packages:

    sudo apt update
    sudo apt install -y \
        apt-transport-https \
        ca-certificates \
        curl \
        gnupg \
        lsb-release \
        jq
        
  Add Docker’s official GPG key:

    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
setup repository:

    echo \
      "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
      $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
      
Install Docker Engine:

    sudo apt update
    sudo apt install -y docker-ce docker-ce-cli containerd.io
    Add your user to the docker group:

    sudo usermod -aG docker $USER

Docker Compose
download the current stable release of Docker Compose:

    COMPOSE_VERSION=$(curl -s "https://api.github.com/repos/docker/compose/tags" | jq -r '.[0].name')
    sudo curl -L "https://github.com/docker/compose/releases/download/${COMPOSE_VERSION}/docker-compose-$(uname -s)-$(uname -m)" \
      -o /usr/local/bin/docker-compose
Apply executable permissions to the binary:

    sudo chmod +x /usr/local/bin/docker-compose

2)Pull nginx & hello-world:  

        docker pull hello-world
        docker pull nginx

3)Port forward nginx to port 80: <br>
    `docker run --name mynginxl -p 80:80 -d nginx`

Open your public ip after successfully executing this command.

4)View images: <br>

  `docker images`

5)Pull apache2: <br>

   `docker pull ubuntu/apache2`

6) Kill nginx to allocate port 80 to apache2: <br>
   `docker kill <container_id_nginx>`

To grab the container id of nginx, run `docker ps`

7) Finally, port apache2 to port 80: <br>
   `docker run --name apache -p 80:80 -d ubuntu/apache2`

   and reopen your public ip.(see your public ip change)

 # Host a website using Docker and Nginx <br/>
 - Login to your AWS account and download your passkey and launch the EC2 instance.  
- Launch PuTTY and add the IP address from instance and add key pair file and open the PuTTY terminal.
- Login to the OS by writing "ubuntu"
- After that I have to install docker in my OS .<br/>
- Now install Docker using following command:
```bash
curl -sL https://github.com/ShubhamTatvamasi/docker-install/raw/master/docker-install.sh | bash
```
- Type following command to avoid using ``sudo`` always (right that's irritating)
```bash
newgrp docker
```
- Then type (This will provides a list of the Docker containers on your machine)
```bash
docker ps
```
- You can check your docker version by typing:
```bash
docker --version
```
- Now, to use ``Nginx`` in our container use:
```bash
docker pull nginx
```
- And:
```bash
docker run --name docker-nginx -p 80:80 nginx
```
- Now you can type your instance's IP and see Nginx default web page.
Use following command to stop the container from running:
```bash
ctrl + c
```
- Use following command to reveals that the Docker container has been exited:
```bash
docker ps -a
```
- Use following command to see container's ID
```bash
docker run --name docker-nginx -p 80:80 -d nginx
```
- Use following command to see new information about container:
```bash
docker ps
```
- Use following command to stop the container:
```bash
docker stop docker-nginx
```
- Then remove default Nginx page and create new custom html file using following commands:
```bash
docker rm docker-nginx
```
```bash
mkdir -p ~/docker-nginx/html
```
Now navigate to file created:
```bash
cd ~/docker-nginx/html
```
- Now create a ``index.html`` and write a html code on ``vim`` code editor:
```bash
vi index.html
```
- Now write your code and save the file.
Then connect the file to instance:
```bash
docker run --name docker-nginx -p 80:80 -d -v ~/docker-nginx/html:/usr/share/nginx/html nginx
```
## it will run other wise you make some correction in program. so, you need to recheck the program.
