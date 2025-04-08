# Building Docker Container
Run the following command from the top of the repository

```sh
sudo docker build -t nexmon_image -f docker/Dockerfile .
```

# Running Docker Container
```sh
sudo docker run -d --name=nexmon_container nexmon_image tail -f /dev/null
```

# Exec into Container
```sh
sudo docker exec -it nexmon_container /bin/bash
```
