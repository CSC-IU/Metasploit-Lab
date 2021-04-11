# Labs

This is the repository for the Metasploit lab. Here we have a basic dockerfile network that connects a Kali OS to a Metasploitable2 OS. Metasploitable is a highly vulnerable OS made specifically to practice pentesting on!

# Create the network
To create the Docker network that will be used to allow connectivity between our containers:
```bash
sudo docker network create vulnerable --attachable --subnet 10.0.0.0/24
```
# Images
Then we will need to create two containers, one for Metasploit and the other for Metasploitable2.

## Metasploit:
```bash
docker pull kalilinux/kali:latest
```

## Metasploitable2:
While that is loading, begin pulling the second image (Metasploitable2):
```bash
docker pull tleemcjr/metasploitable2
```

# Create and run the containers:
## Metasploit
```bash
sudo docker run \
    --name kali \
    -it \
    --hostname kali \
    --network vulnerable \
    --ip="10.0.0.2" \
    --env DISPLAY=$DISPLAY \
    -v /dev/shm:/dev/shm \
    --device /dev/snd \
    --device /dev/dri \
    --mount type=bind,src=/tmp/.X11-unix,dst=/tmp/.X11-unix \
    kalilinux/kali:latest \
    /bin/bash
```
## Metasploit
```bash
docker run \
    -it \
    --network vulnerable \
    --ip="10.0.0.3" \
    --name metasploitable \
    --hostname metasploitable2 \
    tleemcjr/metasploitable2 \
    bash
```
### Start the vulnerable services
The services need to be started on this container, otherwise they won't show up when scanned. 

To do so, simple type `services.sh` in the home directory. It should look like this: 
```bash
root@metasploitable2:/# services.sh
```

# Exit

To stop the container, close the terminal with `CTRL + D`.

If you want to remove the images afterwards:
```bash
docker rm -f kali metasploitable
docker system prune -a
```
