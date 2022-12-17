# deploy your docker container to the cloud (aws ec2)


## 1. create a security group

    + click on "security groups"
    + click on "create security group"
    + give it a name (e.g. "myDockerContainerSecurityGroup")
    + add the inbound rules:
        + type: "http" (port 80)
        + type: "custom tcp" (port 8001) => this should be the same port you specified in your docker-compose file
    + click on "create security group"

![image of security group](./assets/secutrity_group.png)

## 2. create a new ec2 instance

    + click on "launch instance"
    + choose "ubuntu" as the operating system
    + choose "t2.micro" as the instance type
    + key pair: create a new key pair (if you want to access the instance via ssh) 
    + for network settings: click on select an existing security group and choose the one we created on previous step
    + click on "launch instance"


## 3. connect to the instance 

    + click on "view instances"
    + click on "connect" (on the right side)
    + now you can either connect via ssh or via the browser 
    + click on "connect" button and you will be directed to a new tab which contains a terminal
    + now you can execute commands on the instance

## 4. install docker

    ```
        sudo apt-get update
        sudo apt-get upgrade
        sudo apt install docker.io
        systemctl start docker
        systemctl enable docker
        docker --version
    ```
    
**after that install docker-compose:**
    
    ```
        sudo curl -L "https://github.com/docker/compose/releases/download/1.25.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
        sudo chmod +x /usr/local/bin/docker-compose
    ```

## 5. clone your repository

    ```
        git clone <REPO LINK >

    ```

## 6. run your docker container

    ```
        cd <REPO NAME>
        sudo docker-compose build && sudo docker-compose up
    ```

if you dont want to use sudo for every command then run `sudo su`

and then run the commands above without sudo

#### run django commands for that image 

    ```
        sudo docker-compose exec web python manage.py makemigrations
        sudo docker-compose exec web python manage.py migrate
    ```

or `docker-compose run --rm web bash` and now your in the docker terminal and you can run django commands normally


    ``` 
        python manage.py makemigrations
        python manage.py migrate
    ```
## 7. open your app in the browser

+ click on "view instances"
+ click on "public ip" (on the right side)
+ now you can open your app in the browser by typing the public ip address in the browser and add port number to it 

e.g. http://<PUBLIC IP>:8001

+ now you can add your routes to the url and see the result in the browser


