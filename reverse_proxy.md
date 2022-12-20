# reverse_proxy

using nginx as reverse proxy

## Introduction

The reverse proxy is a service that allows you to expose your local services to the internet. It is a very powerful tool that can be used to expose your local services to the internet, or to create a private network for your local services.

+ by default the security group allow to connect to http on port 80 



## install nginx


+ Step 1:

Make a ssh connection to your instance

+ Step 2:

Update your apt-get (cause it may not have details of nginx) `sudo apt-get update`

+ Step 3:

Now run the following to install `sudo apt-get install nginx`

Step 4:

Now installing is done by step 3. Let’s start the nginx service with the following command.

`sudo service nginx start`

Step 5:

go to your browser and type your public ip address of your instance. You should see the following page.

![nginx]()


## modify nginx configuration

+ Step 1:

Now we need to modify the nginx configuration file. Run the following command to open the configuration file.

`sudo nano /etc/nginx/nginx.conf`

+ Step 2:

Now we need to modify the configuration file. Go to the following line and uncomment it.

`include /etc/nginx/sites-enabled/*;`

+ Step 3:

Now we need to create a new file for our configuration. Run the following command to create a new file.

`sudo nano /etc/nginx/sites-available/default`

+ Step 4:

Now we need to add the following configuration to the file.

```
server {
    listen 80;
    server_name _;
    location / {
        proxy_pass http://localhost:3030;
    }
}
```

**this configuration will forward any request on port 80 to prot 3030** 


+ Step 5:

Now we need to restart the nginx service. Run the following command to restart the service.

`sudo service nginx restart`

`sudo systemctl restart nginx`

+ Step 6:

Now go to your browser and type your public ip address of your instance. You should see the following page.


## Conclusion

In this tutorial, we have learned how to install nginx and configure it as a reverse proxy. We have also learned how to configure nginx to forward the request to a specific port.

## References

[revers_proxy_vid](https://www.youtube.com/watch?v=_EBARqreeao)
