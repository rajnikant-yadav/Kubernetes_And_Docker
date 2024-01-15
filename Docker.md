docker login

sudo docker build -t todo_test .

docker ps -a

2. Remove the Stopped Container:
Use the following command to remove the stopped container:


docker rm e836670e77cc
Replace e836670e77cc with the actual container ID.

3. Forcefully Remove the Docker Image:
Now that the associated container is removed, you can try removing the Docker image again, this time with the --force or -f flag:


docker rmi -f ee301c921b8a


1. Remove Stopped Containers:
If you don't need any of the stopped containers (nice_ritchie, great_bhaskara, youthful_cartwright), you can remove them with the following command:

docker rm e836670e77cc a76b84dca023 8ac71c7799a7

2. Forcefully Remove Docker Image:
Now, attempt to remove the Docker image again, this time using the --force or -f flag:


docker rmi -f hello-world

docker images


docker run -p 8080:3031 -d todo_server


Check for Running Processes on Port 8080:
Check if there are any other processes or services already running on port 8080 on your host machine. If another process is using that port, it can conflict with your Docker container. You can use the following command to check for processes:

lsof -i :8080
If there's another process using port 8080, you might need to stop or reconfigure it.

Use a Different Host Port:
As a test, try using a different port on your host machine, for example:

docker run -p 9090:3031 -d todo_server

curl http://localhost:8080/ping


ß

sudo docker buildx build -t todoreact:1.0 --platform linux/amd64 --load .


docker run -p 5173:5173 -d todo_react


sudo docker tag todoreact:1.0 rajnikant98/todoreact:1.0


docker push rajnikant98/todoreact:1.0