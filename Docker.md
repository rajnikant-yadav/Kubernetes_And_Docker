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

docker run -d --env-file=local.env --name=meera -p 9000:80 meera
## An overview of key Dockerfile instructions for building Docker images.
### 1 FROM:
This sets the base image for your Docker image. It's like specifying the operating system you want to use as a starting point.

### 2 RUN:
The RUN instruction is used to execute commands inside the Docker image. It can be used to install packages, update software, or perform any other command-line operations.

### 3 MAINTAINER:
Note: MAINTAINER is deprecated, and LABEL is commonly used instead. The LABEL instruction can include information about the maintainer, version, or any other metadata.

### 4 COPY and ADD:
These instructions are used to copy files or directories from the host machine into the Docker image. The primary difference is that ADD can also handle URLs and extract compressed files, while COPY is simpler and more explicit.

### 5 EXPOSE:
This instruction informs Docker that the container will listen on the specified network ports at runtime. It doesn't actually publish the ports; it's more of a documentation feature.

### 6 WORKDIR:
It sets the working directory for any subsequent RUN, CMD, ENTRYPOINT, COPY, and ADD instructions in the Dockerfile.

### 7 CMD:
This instruction provides default command and/or parameters for the container. It can be overridden when running the container.


### 8 ENTRYPOINT:
Similar to CMD, but the main difference is that ENTRYPOINT specifies the command to run as an executable, and CMD provides default arguments for that command.

### 9 ENV:
It sets environment variables in the Docker image. These variables can be used during the build process and will be available when the container is running.

### In a simple example, a Dockerfile might look like this:

```dockerfile
# Use an official Python runtime as a base image
FROM python:3.8

# Set the working directory
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . /app

# Install any needed packages specified in requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Make port 80 available to the world outside this container
EXPOSE 80

# Define environment variable
ENV NAME World

# Run app.py when the container launches
CMD ["python", "app.py"]
```