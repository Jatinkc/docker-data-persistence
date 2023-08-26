# Data-Persistence-in-Docker

## > Create a Volume

```code 
docker volume create testvolume
```

## > List all the volumes present locally
```code
docker volume ls
```

![list volumes](https://github.com/Jatinkc/docker-data-persistence/blob/main/check%20volume.png)

## > Run a container with attached volume
Here we are are attaching volume `testvolume` with a folder named `app`
using nginx:latest image
```code
docker run -d --name voldemo -v testvolume:/app nginx:latest
```

![container run command](https://github.com/Jatinkc/docker-data-persistence/blob/main/Run%20a%20container.png)
![Check running container](https://github.com/Jatinkc/docker-data-persistence/blob/main/check%20running%20containers.png)


## > Let's connect to our container using bash
```code
docker exec -it voldemo bash
```

## > Let's create a file in `app` folder using `nano`
```code
apt update
apt install nano
cd app
nano test.txt
```
Once the nano editor opens up, add the below content or whatever you want
```code
Hello World! Welcome to the test file!! 
```
Now save the file using `ctrl+x` then press `y` and `Enter`

![Container bash](https://github.com/Jatinkc/docker-data-persistence/blob/main/container%20bash.png)

## > Now Stop and Remove the nginx container
```code
docker stop voldemo
docker rm voldemo
```
![Stopping and Removing cotnainer](https://github.com/Jatinkc/docker-data-persistence/blob/main/stop%20and%20remove%20container.png)

![Check running container](https://github.com/Jatinkc/docker-data-persistence/blob/main/removed%20container.png)

## > Now run the container again and see whether the data still exists or not
```code
docker run -d --name voldemo -v testvolume:/app nginx:latest
```

## > Let's connect to our container using bash
Again, check if the data still exists or not
```code
docker exec -it voldemo bash
```
```code
ls
cd app
cat test.txt
```

![All again process](https://github.com/Jatinkc/docker-data-persistence/blob/main/again%20create%20and%20connect%20conatiner%20bash.png)





