# Nginx Playground in Mac

## Prerequisite

* Install Docker Desktop in [Mac](https://docs.docker.com/desktop/install/mac-install/)
* Install Nginx in Mac

```
brew install --cask nginx
```

## Procedure

1. Run Docker Desktop & create image using Dockerfile

```
docker build -t nodeapp -f ./docker/Dockerfile
```

2. Create 4 running nodeapp containers with user-defined APPID

```
docker run -p 2222:9999 -e APPID=2222 -d nodeapp
docker run -p 3333:9999 -e APPID=3333 -d nodeapp
docker run -p 4444:9999 -e APPID=4444 -d nodeapp
docker run -p 5555:9999 -e APPID=5555 -d nodeapp
```

3. Copy the nginx.conf to the Nginx directory

```
cp nginx.conf /usr/local/etc/nginx/nginx.conf
```

4. Run Nginx

```
/usr/local/bin/nginx

# If Nginx is running, just reload configuration
/usr/local/bin/nginx -s reload
```

5. Observe the round robin

```
http://localhost:8080/ or admin or app1 or app2 --> observe round robin
http://localhost:8080/app1, http://localhost:8080/app2 --> observe round robin
http://localhost:8080/admin --> block
```





