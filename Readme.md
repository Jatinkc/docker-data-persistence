# Data-Persistence-in-Docker

## > Create a Volume

```code 
docker volume create testvolume
```

## > List all the volumes present locally
```code
docker volume ls
```

## > Run a container with attached volume
Here we are are attaching volume `testvolume` with a folder named `app`
using nginx:latest image
```code
docker run -d --name voldemo -v testvolume:/app nginx:latest
```

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

## > Now Stop and Remove the nginx container
```code
docker stop voldemo
docker rm voldemo
```

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





