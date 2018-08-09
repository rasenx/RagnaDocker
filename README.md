# RagnaDocker
rAthena, FluxCP, and the LAMP Stack

RagnaDocker allows you to spin up your own Ragnarok Server built off of rAthena in seconds!
The docker container is a snapshot instance of a server ready to go, right before the setup process begins.
While these instructions won't be going indepth on how to best utilize a rAthena server or a FluxCP instance, I will try to go into detail on how to start using them.

Install Docker to your Docker Host Computer; instructions can be found here: https://docs.docker.com/install/
Add an local ip address for your Ragnarok Server Docker Container to use:
	
```bash
ip addr add 192.168.169.142 dev eth0
```
  
  This ties one of your ips to a networking device on your docker host.
After docker is running on your host computer, you can run this command which will not only download the Docker Image, but create a Docker Container for you to use that is bound to the specified ports/ip:
	
```bash
docker run -it -p 192.168.169.142:20000:80 -p 192.168.169.142:20001:443 -p 192.168.169.142:20002:3306 -p 192.168.169.142:20003:5121 -p 192.168.169.142:20004:6121 -p 192.168.169.142:20005:6900 -v ~/Desktop/datastore/:/datastore/ -v ~/Desktop/datastore/etc-apache2/:/datastore/etc/apache2/ -v ~/Desktop/datastore/etc-mysql/:/datastore/etc/mysql/ -v ~/Desktop/datastore/usr-bin-rathena/:/datastore/usr/bin/rathena/ -v ~/Desktop/datastore/var-lib-mysql/:/datastore/var/lib/mysql/ --name Aegis tvollscw/RagnaDocker 
```

After running that command, you will be using the terminal within that Docker Container. Inside of here, you will learn how to start up your rAthena server.
	
```bash
./launch-athena.sh
```

This should run without errors, starting up your map-server, character-server, and the login-server.
Next, in your browser, you can enter in the IP or Hostname that you have given to your docker host:

```
http://192.168.169.142:20000
```

This will bring up your FluxCP installation, which will act as your front-end website for your Ragnarok Server; allowing users to register for your server and obtain other information about your server.
	The password to use is: 
  
```
secretpassword
```

Next you will need to enter in the login information for FluxCP to update the MySQL database; both are:

```
ragnarok
```
	

For more information on getting started with FluxCP and the Ragnarok Server, visit the project's page on github:
https://github.com/tvollscw/RagnaDocker
