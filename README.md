# Labs

This is the repository for the Metasploit lab. Here we have a basic dockerfile defined that creates an apache 2.0 webserver. This is a very basic setup but will showcase some of the capabilities of metasploit. 

To start the container:

```bash
docker run --name=nmaplab -d -p 8080:80 bradyanderson805/iucscnmap apachectl -D FOREGROUND
docker exec -it nmaplab /bin/bash
```

[Click me once you have run the command!](http://127.0.0.1:8080)


When you are done:

```bash
docker rm -f nmaplab
docker system prune -a
```
Finally delete the git repo (if you don't want it on your machine anymore :) )
