# Overview
Kubernetes, often abbreviated as K8s, is an open-source container orchestration platform. In simpler terms, it's a powerful tool designed to help you manage and deploy containerized applications.

## Key Concepts

### Containerized Applications
Modern applications are often packaged into containers. Containers encapsulate an application and its dependencies, ensuring consistent and reliable execution across different environments.

### Orchestration
Kubernetes is great at organizing and controlling many parts of your app. It smartly figures out where to put them, how many to have, and takes care of their lifecycle smoothly.

### Scaling
With Kubernetes, scaling your application becomes a breeze. It can automatically deploy more container instances to handle increased traffic and scale down when demand decreases.

### Management
Simplify the management of your containerized applications with Kubernetes. It takes care of crucial tasks like load balancing, rolling updates, and fault tolerance, ensuring reliability and efficiency.

## Why Kubernetes?

- **Efficient Scaling:** Easily scale your application to meet varying demands.
- **Reliable Management:** Kubernetes handles tasks like load balancing and updates, ensuring your application runs smoothly.
- **Fault Tolerance:** Enhance the reliability of your application with Kubernetes' fault tolerance features.

## Getting Started
To start using Kubernetes, follow these steps:

1. Install Kubernetes on your system.
2. Define your application's configuration using Kubernetes manifests.
3. Deploy your application with a simple command.

For detailed instructions, refer to the [official Kubernetes documentation](https://kubernetes.io/docs/)

## Installing Docker on MacBook Pro with Apple Silicon Chip

### Overview
Docker is a platform for developing, shipping, and running applications in containers. This guide provides step-by-step instructions on how to install Docker on a MacBook Pro with Apple Silicon (chip).

### Prerequisites
- MacBook Pro with Apple Silicon ( chip)
- macOS 11.3 or later

## Installation Steps

1. **Download Docker Desktop for Mac (Apple Silicon):**
   Visit the [official Docker website](https://www.docker.com/products/docker-desktop) and download the Docker Desktop for Mac (Apple Silicon) package.

2. **Install Docker Desktop:**

   Double-click the downloaded Docker Desktop package (`.dmg`) to open it. Drag the Docker icon to the Applications folder to install it.

3. **Run Docker Desktop:**

   Open Docker Desktop from the Applications folder. The first time you run it, you may need to confirm that you want to open the application.

4. **System Extension Blocked (if prompted):**

   If you encounter a "System Extension Blocked" message, open "Security & Privacy" settings in System Preferences. Click "Allow" next to the message related to Docker to enable the system extension.

5. **Sign in (Optional):**

   You may be prompted to sign in with your Docker ID. If you don't have one, you can create a Docker ID for free.

6. **Docker Desktop Running:**

   Once installed, Docker Desktop will appear in your system tray. You are now ready to use Docker on your MacBook Pro with Apple Silicon.

## Verify Installation

Open a terminal and run the following command to verify that Docker is installed and working correctly:

```bash
docker --version
This should display the installed Docker version.
```
## Credential Storage Issue

In some cases, you may encounter a credential storage issue. Follow these steps if you experience problems related to the credential helper:

- **Check Credential Helper:**
  Run the following command to verify the credential helper is configured correctly:

  ```bash
  docker info

  If it's set to "desktop," try switching to "osxkeychain" on macOS or "pass" on Linux.

Edit ~/.docker/config.json:
Open the Docker configuration file and make necessary changes:

nano ~/.docker/config.json
Update the credential helper to the appropriate value based on your operating system.

```

## Run Your First Docker Container
Now that Docker is installed, run a simple container to ensure everything is working:
```bash
docker run hello-world
```

## Installing Minikube
Open a terminal and run the following command to install Minikube using Homebrew:

```bash
brew install minikube

Start your cluster:

From a terminal with administrator access (but not logged in as root), run:

minikube start

If Minikube fails to start, see the drivers page for help setting up a compatible container or virtual-machine manager.

Interact with your cluster:

If you already have kubectl installed (see documentation), you can now use it to access your shiny new cluster:

minikube status

```

## Master Node
In Kubernetes, a master node is like the brain of the whole system. It manages and oversees the entire cluster of computers (nodes) that work together to run and deploy applications.

#### The master node takes care of important tasks, such as:

**Scheduling:** It decides which node should run specific tasks or applications based on available resources and requirements.

**Maintaining Cluster State:** The master node keeps track of all the nodes in the cluster and the applications running on them. It ensures that the desired state of the cluster matches the actual state.

**Scaling:** The master node can instruct the worker nodes to scale applications up or down, depending on the demand.

**Handling Failures:** If a node or application fails, the master node can detect it and take corrective actions, like rescheduling tasks on healthy nodes.

So, you can think of the master node as the central coordinator that makes sure everything in the Kubernetes cluster runs smoothly and as expected.

### Key components on the master node include:
- **API Server:** Serves as the entry point for all administrative tasks.
- **Controller Manager:** Watches for changes in the cluster and takes corrective action.
- **Scheduler:** Assigns workloads to worker nodes based on resource availability.
- **etcd:** A distributed key-value store that holds the cluster's configuration data.


## Kubernetes Worker Node

In a Kubernetes cluster, the worker node plays a crucial role in executing and managing containerized applications. This document provides an overview of the responsibilities and functions performed by a Kubernetes worker node.

### Worker Node Responsibilities
##### Running Containers
Worker nodes host containers, which are lightweight and portable units encapsulating applications and their dependencies. These containers execute the actual workloads or applications.
#### Kubelet
The Kubelet is an agent running on each worker node. Its primary responsibility is to ensure that containers are running within a Pod, which is the smallest deployable unit in Kubernetes. The Kubelet communicates with the master node to receive instructions on which containers to run.
#### Container Runtime
Worker nodes utilize a container runtime (e.g., Docker or containerd) to start, stop, and manage containers based on instructions received from the Kubelet.
#### Networking
Worker nodes manage networking for containers. They facilitate communication between containers within the same Pod and ensure that containers on different nodes can communicate effectively.
#### Node Status Reporting
Worker nodes report their status and resource utilization back to the master node. This information is crucial for the master node to make informed decisions about scheduling new workloads across the cluster.
#### Handling Pods
Worker nodes execute and manage Pods, which are groups of one or more containers that share the same network namespace and storage. Pods are scheduled together on the same node, contributing to efficient resource utilization.
#### Worker Node in Simple Terms
In simple terms, a worker node acts as the muscle of the Kubernetes cluster, responsible for running containerized applications. It ensures the proper execution of tasks assigned by the master node. The master node, on the other hand, coordinates and manages the entire cluster, working together with worker nodes to provide a scalable and resilient environment for deploying and managing containerized applications.

Together, the master and worker nodes form a cohesive Kubernetes cluster, orchestrating containerized workloads seamlessly.

### Key components on a worker node include:

- **Kubelet:** Listens for instructions from the master node and manages containers on the node.
- **Container Runtime:** Responsible for running containers, such as Docker or containerd.
- **Kube Proxy:** Maintains network rules on the worker nodes.

## Kubernetes Basic Objects
This document provides a brief overview of fundamental Kubernetes objects that are essential for deploying and managing applications within a Kubernetes cluster.

## Pods
A **Pod** is the smallest deployable unit in Kubernetes, representing one or more containers that share the same network namespace and storage. Pods are the basic building blocks for running applications.

### Example:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: mypod
spec:
  containers:
    - name: mycontainer
      image: nginx:latest
```
**apiVersion:** Specifies the API version for this Kubernetes object.<br>
**kind:** Specifies the type of object, in this case, a Pod.<br>
**metadata:** Contains information like the name of the Pod.<br>
**spec:** Defines the specification for the Pod, including the containers it should run.
<br>
In this example, a Pod named "mypod" is defined, running a single container based on the latest nginx image.

## To create and run the multi-container pod using the provided YAML configuration, follow these steps:
In a multi-container pod, you can define multiple containers that share the same network and storage namespace. Each container in the pod runs its own processes but can communicate with other containers in the same pod through the localhost network. Here's an example YAML configuration for a multi-container pod:
### Step 1: Save the YAML Configuration
Save the multi-container pod YAML configuration to a file, for example, multi-container-pod.yaml.



```yaml
apiVersion: v1
kind: Pod
metadata:
  name: multi-container-pod
spec:
  containers:
    - name: nginx-container
      image: nginx:latest
      ports:
        - containerPort: 80

    - name: sidecar-container
      image: busybox:latest
      command: ["/bin/sh", "-c", "while true; do echo 'Hello from Sidecar Container'; sleep 10; done"]
```

There are two containers defined within the same pod: nginx-container and sidecar-container.
nginx-container runs the Nginx web server and exposes port 80.
sidecar-container runs a simple shell command that prints a message every 10 seconds.
This illustrates the concept of a multi-container pod where each container performs a different task but can work together within the same pod. Adjust the images, commands, and other specifications based on your specific use case.

### Step 2: Create the Pod
Use the following command to create the pod:
```yaml
kubectl apply -f multi-container-pod.yaml
This command instructs Kubernetes to create the pod based on the specifications in the YAML file.

```

### Step 3: Check Pod Status
You can check the status of the pod using the following command:

```bash
kubectl get pods
This command will display a list of pods, and you should see your multi-container-pod in the output.
```

### Step 4: Access Nginx Container Logs
To check the logs of the nginx-container, you can use the following command:

```bash
kubectl logs multi-container-pod -c nginx-container
This command retrieves the logs from the specified container (nginx-container) within the pod.
```

### Step 5: Access Sidecar Container Logs
To check the logs of the sidecar-container, you can use a similar command:

```bash
kubectl logs multi-container-pod -c sidecar-container
This command retrieves the logs from the specified container (sidecar-container) within the pod
```

### Step 6: Cleanup (Optional)
If you want to delete the pod, you can use the following command:

```bash
kubectl delete pod multi-container-pod
This will delete the pod and its associated containers.

These steps assume you have kubectl configured to interact with your Kubernetes cluster. Adjust the commands as needed based on your specific setup.
```

## Kubernetes Pod with Environment Variables
In Kubernetes, environment variables can be passed to containers in a pod. These variables can be used to configure the behavior of applications running in the containers. Environment variables are often used to provide dynamic configuration, such as database connection strings, API keys, or other settings that may vary between environments.

### Step 1: Save the YAML Configuration

Save the pod YAML configuration with environment variables to a file, for example, `env-variable-pod.yaml`.

### Step 2: Update Environment Variables

Open the `env-variable-pod.yaml` file and modify the environment variables based on your requirements.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: env-variable-pod
spec:
  containers:
    - name: mycontainer
      image: nginx:latest
      env:
        - name: MY_ENV_VARIABLE
          value: "Hello, Kubernetes!"

```

### Step 3: Create the Pod
Use the following command to create the pod:

``` bash
kubectl apply -f env-variable-pod.yaml
```

### Step 4: Check Pod Status
You can check the status of the pod using the following command:
```bash
kubectl get pods
```
### Step 5: Access Container Logs
To check the logs of the container and verify the environment variable, you can use the following command:

```bash
kubectl logs env-variable-pod
```
### Step 6: Cleanup (Optional)
If you want to delete the pod, you can use the following command:

```bash
kubectl delete pod env-variable-pod
```
Adjust the environment variables in the YAML configuration as needed for your specific use case.

## Kubernetes Pod with Ports

### Step 1: Save the YAML Configuration

Save the pod YAML configuration with specified ports to a file, for example, `pod-with-ports.yaml`.

```yaml
kind: Pod
apiVersion: v1
metadata:
  name: testpod4
spec:
  containers:
    - name: c00
      image: httpd
      ports:
        - containerPort: 80
```

### Step 2: Create the Pod
Use the following command to create the pod:

```bash
kubectl apply -f pod-with-ports.yaml
```
### Step 3: Check Pod Status
You can check the status of the pod using the following command:

```bash
kubectl get pods
```
### Step 4: Access Container Logs
To check the logs of the container, you can use the following command:

```bash
kubectl logs testpod4
```
### Step 5: Access Container via Port
Since the container exposes port 80, you can access it using the cluster IP and port. If running locally, you might use localhost or the cluster IP:

```bash
# Example if running locally
curl http://localhost:80
```
### Step 6: Cleanup (Optional)
If you want to delete the pod, you can use the following command:

```bash
kubectl delete pod testpod4
Adjust the port configuration in the YAML file as needed for your specific use case.
```

## Labels and Selectors
In Kubernetes, labels and selectors are essential concepts used for organizing and selecting groups of resources. Labels are key-value pairs attached to Kubernetes objects, while selectors are used to filter and query these objects based on their labels. Labels provide a flexible and expressive way to categorize and identify resources within a cluster.

## Labels:
**Definition:** Labels are key-value pairs associated with Kubernetes objects. They are used to provide metadata and categorization to resources.

**Purpose:** Labels offer a way to organize and identify resources based on user-defined characteristics. They are not used to directly influence the behavior of the system but provide a means for users and tools to organize and select resources.

**Examples:**

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: mypod
  labels:
    app: frontend
    environment: production
```
#### Usage:

**Organization:** Labels can be used to categorize resources based on application, environment, version, or any other relevant attribute.
**Grouping:** Resources with similar labels can be grouped together for management, monitoring, or other operational tasks.

## Selectors:
**Definition:** Selectors are used to filter and query resources based on their labels. They allow you to specify criteria for identifying a set of resources.

**Purpose:** Selectors are crucial for identifying and working with groups of resources. They provide a way to dynamically select and operate on subsets of objects within a cluster.

**Examples:**

Equality-based Selector:
```yaml
apiVersion: v1
kind: Service
metadata:
  name: myservice
spec:
  selector:
    app: frontend
```    
**Set-based Selector:**
```yaml
apiVersion: v1
kind: Deployment
metadata:
  name: mydeployment
spec:
  selector:
    matchLabels:
      app: frontend
    matchExpressions:
      - {key: environment, operator: In, values: [production, staging]}
```
**Usage:**

**Service Discovery:** Selectors are used to define which Pods a Service should target.
**Controllers:** Controllers like Deployments use selectors to manage a set of Pods based on label criteria.
**Monitoring and Logging:** Selectors enable the selection of specific resources for monitoring or logging purposes.

## Here are some kubectl commands to demonstrate labeling and selecting resources in Kubernetes:

### Labeling Resources:
### Labeling a Pod:

```bash
kubectl label pod <pod-name> app=frontend environment=production

This command adds labels app=frontend and environment=production to the specified pod.
```

### Labeling a Service:

```bash
kubectl label service <service-name> app=frontend

This command adds the label app=frontend to the specified service.
```

## Selecting Resources:
### Selecting Pods with a Specific Label:

```bash
kubectl get pods -l app=frontend

This command lists all pods with the label app=frontend.
```
### Selecting Services with a Specific Label:

```bash
kubectl get services -l app=frontend

This command lists all services with the label app=frontend.
```
### Selecting Pods with Multiple Labels:

```bash
kubectl get pods -l app=frontend,environment=production

This command lists pods that have both labels app=frontend and environment=production.
```

### Selecting Pods with Set-Based Label Selector:

```bash
kubectl get pods --selector='environment in (production, staging)'

This command lists pods with the label environment set to either production or staging.
```
These commands provide a basic illustration of how to label and select resources using kubectl. Adapt them based on your actual resource names, label values, and selection criteria in your Kubernetes cluster.


## Node Selector

In Kubernetes, a Node Selector is a feature that allows you to constrain which nodes your Pods are eligible to be scheduled based on node labels. It provides a way to influence the scheduling decisions made by the Kubernetes scheduler, determining on which nodes your Pods can run.

Here's how Node Selector works:

### Node Labels:

Nodes in a Kubernetes cluster can be labeled with key-value pairs, known as node labels. These labels are used to add metadata or attributes to nodes.
Labels can represent various characteristics of nodes, such as hardware capabilities, geographic location, or other user-defined attributes.

### Node Selector in Pod Specification:
When defining a Pod, you can include a nodeSelector field in the Pod's specification. This field is a set of key-value pairs that must match the labels of a node for the Pod to be scheduled on that node.
If the node labels match the nodeSelector specified in the Pod, the scheduler considers the node eligible for running the Pod.

### Example Pod Configuration with Node Selector:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: mypod
spec:
  containers:
  - name: mycontainer
    image: nginx
  nodeSelector:
    mylabel: myvalue

In this example, the Pod is configured with a node selector specifying that it should be scheduled only on nodes labeled with mylabel: myvalue.
```
### Scheduling Decision:

When the scheduler receives a Pod creation request, it evaluates the node selector against the labels of available nodes.
If there is a node whose labels match the node selector, the scheduler places the Pod on that node.
If there is no matching node, the Pod remains in a pending state until a suitable node becomes available.
Node Selector is particularly useful in scenarios where you want to influence the placement of Pods based on specific characteristics or requirements of your nodes.

### Here's a summary of how to use Node Selector:

Label Nodes: Label nodes with key-value pairs representing their attributes.
Define Node Selector in Pod: In your Pod specification, include the nodeSelector field with the desired labels.
Scheduler Decision: The Kubernetes scheduler considers nodes with matching labels eligible for running the Pod.
This feature helps ensure that Pods are scheduled on nodes that meet specific criteria, allowing for better control and optimization of resource utilization within a Kubernetes cluster.






## Scaling and Replication in Kubernetes:
Scaling and replication are crucial concepts in Kubernetes for managing containerized applications. Let's break down each term and how they relate to the Replica Controller:

### 1. Scaling:

Refers to adjusting the number of replicas, or instances, of a containerized application running in your Kubernetes cluster.
Scaling can be up (adding more replicas) to handle increased demand or down (removing replicas) to save resources during low traffic periods.
Kubernetes offers various methods for scaling, including manual commands, scaling deployments, and autoscalers.
### 2. Replication:

Creates and maintains a desired number of identical pods for your application.
Pods are the units of deployment in Kubernetes, containing one or more containers and the resources they need to run.
By replicating pods, you ensure application availability and distribute workload across multiple nodes for improved performance and resiliency.
### 3. Replica Controller (Deprecated):

An older mechanism for managing replication in Kubernetes.
It allows you to define the desired number of replicas for a pod template and creates/maintains them.
Replica Controllers are considered deprecated and replaced by Deployments for several reasons:
Deployments offer improved rollout and rollback strategies for updates.
Deployments can manage more complex pod configurations with multiple containers and volumes.
Replica Controllers lack scaling features of Deployments.
Summary:

Scaling and replication work together to maintain the desired number of running applications in your Kubernetes cluster.
Replica Controllers used to be the primary tool for replication but are now superseded by Deployments.
Understanding scaling and replication principles is essential for managing highly available and scalable applications in Kubernetes.

```yaml
apiVersion: v1
kind: ReplicationController
metadata:
  name: my-nginx-rc
spec:
  replicas: 3  # Desired number of pods
  selector:
    app: nginx  # Label for selecting pods to manage
  template:
    metadata:
      labels:
        app: nginx  # Label applied to the pods
    spec:
      containers:
      - name: nginx
        image: nginx:1.21.6  # Container image to use
        ports:
        - containerPort: 80
```
### Explanation:

apiVersion: Specifies the Kubernetes API version (v1 in this case).
kind: Indicates the type of resource, which is ReplicationController here.
metadata: Contains basic information about the controller, including its name.
spec: Specifies the desired state of the controller, including:
replicas: The number of replicas (pods) to maintain.
selector: A label selector to identify the pods the controller should manage.
template: A pod template defining the pod configuration.
template.metadata.labels: The labels applied to the pods created by the controller.
template.spec: The specification for the containers within the pods.
containers: A list of containers to run in each pod.
name: The name of the container.
image: The container image to use.
ports: The ports exposed by the container.

## ReplicaSet
A ReplicaSet is a more modern and improved version of the Replica Controller in Kubernetes. It essentially serves the same purpose, which is to maintain a desired number of identical pods running in your cluster. However, it offers several advantages over the deprecated Replica Controller:

### Key points about ReplicaSets:

**Selector based:** Identifies pods to manage based on labels instead of specific pod names. This allows for greater flexibility and easier scaling.
**Pod template:** Uses a pod template to define the desired configuration for the replicas, including container images, resources, environment variables, etc.
**Scaling and rolling updates:** Supports scaling both up and down, as well as controlled rolling updates for deploying new versions of your application.
**Automatic recovery:** Automatically rebuilds failed pods to maintain the desired number of replicas.

### Here's a simplified explanation of how a ReplicaSet works:

You define a ReplicaSet object with the desired number of replicas and a pod template.
The ReplicaSet controller starts creating pods based on the template until the desired number is reached.
The controller constantly monitors the status of the pods. If a pod fails or is deleted, it automatically creates a new one to maintain the desired number.
When you update the ReplicaSet with a new pod template, it performs a rolling update by gradually creating new pods with the updated configuration and terminating old ones.

### Here are some real-world use cases for ReplicaSets:

Deploying and scaling web applications
Running background workers for tasks like data processing
Managing database replicas for high availability

```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: my-nginx-rs
spec:
  replicas: 3  # Desired number of replicas (pods)
  selector:
    matchLabels:
      app: nginx  # Label selector to identify pods to manage
  template:
    metadata:
      labels:
        app: nginx  # Label applied to the pods
    spec:
      containers:
      - name: nginx
        image: nginx:1.21.6  # Container image to use
        ports:
        - containerPort: 80
```

## Deployments and Rollbacks in Kubernetes
Deployments are a powerful tool in Kubernetes for managing the lifecycle of your containerized applications. They handle:

**Creation of ReplicaSets:** Deployments define the desired state of your application by specifying a pod template with container images, resources, etc. They then create and manage ReplicaSets to maintain the desired number of pods running based on that template.
**Controlled Rollouts:** When you update a Deployment with a new pod template, it performs a rolling update by gradually creating new pods with the updated configuration and terminating old ones, minimizing downtime and ensuring service continuity.
**Rollback Strategies:** If a new version of your application encounters issues, Deployments allow you to easily rollback to a previous stable version with various rollback strategies.
Here's a breakdown of deployment and rollback steps:

## 1. Deployment:

You define a Deployment object with a pod template and desired number of replicas.
Kubernetes creates a new ReplicaSet with the provided template.
The new ReplicaSet starts creating pods until the desired number is reached.
If you update the Deployment with a new template, a new ReplicaSet is created with the updated configuration.

## 2. Rolling Update:

The new ReplicaSet starts creating pods with the updated configuration.
Kubernetes gradually terminates pods from the old ReplicaSet while ensuring enough healthy pods from the new ReplicaSet are running.
This minimizes downtime and ensures a smooth transition to the new version.

## 3. Rollback Strategies:

If the new version encounters issues, you can trigger a rollback to a previous stable version.
Deployments offer three rollback strategies:
Recreate: Deletes all existing pods and creates new ones from the specified rollback version. This leads to downtime but is the simplest strategy.
Rolling Backwards: Creates a new ReplicaSet with the rollback version and performs a rolling update, similar to deployment.

Blue-Green Deployment: Deploys the new version to a separate blue ReplicaSet alongside the existing green (stable) ReplicaSet. Once validated, traffic is switched to the blue ReplicaSet and the green one is deleted. This minimizes downtime but requires additional infrastructure.
Benefits of Deployments:

Controlled updates with reduced risk: Rolling updates minimize downtime and allow you to roll back if issues arise.
Easier scaling and version management: You can easily adjust the number of replicas or update your application version through the Deployment object.
Declarative configuration: Define the desired state of your application, and Kubernetes ensures it's maintained.

```yaml
kind: Deployment
apiVersion: apps/v1
metadata:
   name: mydeployments
spec:
   replicas: 2
   selector:     
    matchLabels:
     name: deployment
   template:
     metadata:
       name: testpod
       labels:
         name: deployment
     spec:
      containers:
        - name: c00
          image: ubuntu
          command: ["/bin/bash", "-c", "while true; do echo Technical-Guftgu; sleep 5; done"]
          
```

## Kubectl Commands for Deployment and Rollback in Kubernetes
Navigating deployments and rollbacks in Kubernetes can be made much easier with the kubectl command-line tool. Here's a breakdown of essential commands for managing your containerized applications:

### 1. Deployment Management:

Create a Deployment:

```bash
kubectl apply -f my-deployment.yaml
```

List Deployments:
```bash
kubectl get deployments
```

Describe a Deployment:
```Bash
kubectl describe deployment my-app-deployment
```

Scale a Deployment:
```Bash
kubectl scale deployment my-app-deployment --replicas=5
```

Get Deployment Logs:
```Bash
kubectl logs -f deployment/my-app-deployment
```

## 2. Rollback Strategies:

Rolling Back to Previous Version:
```Bash
kubectl set image deployment/my-app-deployment my-app-container=your-image-registry/my-app:v1.2.3
```

Recreate Deployment (Full Restart):
```Bash
kubectl rollout restart deployments/my-app-deployment
```

View Rollback History:
```Bash
kubectl rollout history deployment/my-app-deployment
```

## Networking and Services in Kubernetes:
Understanding networking and services in Kubernetes is crucial for building and managing containerized applications. Here's a breakdown of the key concepts:

## 1. Networking:

Kubernetes pods communicate with each other through a virtual network.
Each pod has a unique IP address within the cluster.
Multiple pods can share a network namespace, allowing them to communicate directly through localhost.
Communication between pods across different nodes is achieved through Kubernetes' built-in network plugins like kubenet or third-party CNI plugins.

## 2. Services:

Services act as a virtual abstraction layer for pods, providing a stable endpoint for communication.
They abstract away the pod IPs and network topology, simplifying communication between pods and external clients.
Services can be exposed in various ways:
ClusterIP: Accessible only within the Kubernetes cluster.
NodePort: Accessible through a unique port on each node.
LoadBalancer: Creates a load balancer for external access.
Ingress: Provides a single entry point for multiple services using routing rules.

## 3. Service Types:

ClusterIP: Suitable for internal communication between pods within the cluster.
NodePort: Useful for testing and development, but not recommended for production due to potential security vulnerabilities.
LoadBalancer: Ideal for exposing services to the internet with automatic load balancing.
Ingress: Provides a centralized point of entry for external traffic, managing routing and TLS termination for multiple services.

## 4. Benefits of Services:

Abstraction: Simplifies communication by hiding pod IP addresses and network topology.
Load Balancing: Distributes traffic across multiple pods for improved performance and scalability.
High Availability: Ensures service availability even if individual pods fail.
Scalability: Easily scale your application by adding or removing pods without affecting service discovery.

## 5. Additional Concepts:

DNS entries: Kubernetes automatically creates DNS entries for services within the cluster, making them easily discoverable by other pods.
Selectors: Services use labels to identify the pods they should route traffic to.
Endpoints: A list of pods currently serving the service.


**Here's an example YAML configuration for an application service of type ClusterIP, exposing a web application on port 80:**

```YAML
apiVersion: v1
kind: Service
metadata:
  name: my-app-service
spec:
  selector:
    app: my-app  # Selects pods with the label "app: my-app"
  ports:
  - protocol: TCP
    port: 80  # Port the service listens on
    targetPort: 80  # Port the pod listens on
  type: ClusterIP  # Service type


  Explanation:

apiVersion: Specifies the Kubernetes API version (v1 in this case).
kind: Indicates the type of resource, which is Service.
metadata: Contains basic information about the service, including its name.
spec: Specifies the desired state of the service:
selector: Matches pods with the label "app: my-app" to include in the service.
ports: Defines the port mappings:
protocol: The protocol to use (TCP in this example).
port: The port the service listens on (80).
targetPort: The port the pods targeted by the service listen on (also 80).
type: The type of service (ClusterIP, only accessible within the cluster).
```

## Volumes
In Kubernetes, a volume essentially acts as a directory containing data accessible to containers within a pod. This data persists beyond the container lifespan, even if the pod restarts or terminates. Volumes enable developers to store application data, configuration files, and other persistent content independently of the container image, ensuring data doesn't get lost when containers are recreated.

Here's a breakdown of key points about volumes in Kubernetes:

## Types of Volumes:

There are numerous types of volumes available in Kubernetes, catering to different storage needs and deployment scenarios. Some popular types include:

**EmptyDir:** Creates a temporary directory within the container that disappears when the pod is deleted.
**HostPath:** Mounts a directory from the host node's filesystem into the container.
**PersistentVolumeClaim (PVC):** Requests a persistent volume from the cluster storage provisioner.
**Network File System (NFS):** Mounts a shared directory from an NFS server.
**Azure File Share:** Mounts a file share from Azure storage.

## Volume Mounting:

Volumes are mounted within the container by specifying their type and configuration details in the pod Spec. This instructs Kubernetes to link the chosen directory from the volume source to a specific location within the container filesystem.

Benefits of Volumes:

Using volumes offer several advantages for managing containerized applications:

Persistence: Data stored in volumes persists even when pods are recreated or scaled, ensuring application continuity.
Configurability: Different types of volumes cater to diverse storage needs and deployment environments.
Decoupling: Separates application data from container images, simplifying image management and deployment.
Scalability: Volumes readily support scaling applications by attaching them to new pods.

### Volume 
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: myvolemptydir
spec:
  containers:
  - name: c1
    image: centos
    command: ["/bin/bash", "-c", "sleep 15000"]
    volumeMounts:                                    # Mount definition inside the container
      - name: xchange
        mountPath: "/tmp/xchange"          
  - name: c2
    image: centos
    command: ["/bin/bash", "-c", "sleep 10000"]
    volumeMounts:
      - name: xchange
        mountPath: "/tmp/data"
  volumes:                                                   
  - name: xchange
    emptyDir: {}
```

### HOST PATH
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: myvolhostpath
spec:
  containers:
  - image: centos
    name: testc
    command: ["/bin/bash", "-c", "sleep 15000"]
    volumeMounts:
    - mountPath: /tmp/hostpath
      name: testvolume
  volumes:
  - name: testvolume
    hostPath:
      path: /tmp/data 

```

## Persistent Volume (PV)
In Kubernetes, a Persistent Volume (PV) is a unit of storage that exists independently of any pod. Unlike standard volumes that vanish when a pod terminates, PVs persist and retain data through pod restarts, updates, and even cluster upgrades. This makes them crucial for stateful applications like databases, web servers with persistent files, and message queues.

## Here's a breakdown of PVs in Kubernetes:

### Key Features:

**Persistence:** Data written to a PV isn't tied to specific pods, ensuring it survives pod terminations and reschedulements.
Abstraction: PVs decouple your application from the underlying storage implementation (NFS, AWS EBS, etc.). You only specify storage requirements, not specifics.
**Flexibility:** Multiple pods can access the same PV simultaneously or sequentially (depending on access mode).
**Provisioning:** PVs can be manually provisioned by administrators or dynamically created using Storage Classes.
### How they work:

PersistentVolumeClaim (PVC): Pods don't directly access PVs. Instead, they request storage using a PersistentVolumeClaim (PVC). It specifies the required storage size, access mode (ReadWriteOnce, ReadWriteMany, etc.), and optional storage class.
Binding: Kubernetes matches PVCs to suitable PVs based on requirements. Once a match is found, the PV is bound to the PVC, becoming accessible to the requesting pod.
Mounting: The PV is then mounted to the appropriate directory or block device within the pod's container.
Benefits of using PVs:

Data resiliency: Applications can store and access persistent data reliably.
Scalability: Pods can be easily scaled up or down without losing data.
Simplicity: Developers can focus on application logic without worrying about managing storage details.


## Here's a YAML example demonstrating Persistent Volumes in Kubernetes:

## 1. PersistentVolume (PV) definition:

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: task-pv-volume
  labels:
    type: local
spec:
  storageClassName: manual  # Optional storage class
  capacity:
    storage: 10Gi
  accessModes:
    - ReadWriteOnce  # Access mode (can be ReadWriteMany for multi-pod access)
  hostPath:
    path: "/mnt/data"  # Location of the actual storage on the node
```

## 2. PersistentVolumeClaim (PVC) definition:

```yaml 
apiVersion: v1
kind: PersistentVolume
metadata:
  name: task-pv-volume
  labels:
    type: local
spec:
  storageClassName: manual  # Optional storage class
  capacity:
    storage: 10Gi
  accessModes:
    - ReadWriteOnce  # Access mode (can be ReadWriteMany for multi-pod access)
  hostPath:
    path: "/mnt/data"  # Location of the actual storage on the node
```

## 3. Pod definition using the PVC:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: task-pv-pod
spec:
  volumes:
    - name: task-pv-storage
      persistentVolumeClaim:
        claimName: task-pv-claim
  containers:
    - name: task-pv-container
      image: nginx
      ports:
        - containerPort: 80
          name: "http-server"
      volumeMounts:
        - mountPath: "/usr/share/nginx/html"
          name: task-pv-storage
```

### Explanation:

The PV task-pv-volume defines a 10Gi storage volume on the host path /mnt/data. It's accessible in ReadWriteOnce mode (can be mounted as read-write by a single node).
The PVC task-pv-claim requests a volume with at least 5Gi capacity, matching the PV's storage class and access mode.
The pod task-pv-pod uses the PVC to mount the PV at /usr/share/nginx/html within the container. This allows the container to access the persistent data on the PV.
Key Points:

Provisioning: The PV can be provisioned manually or dynamically using StorageClasses.
Flexibility: Access modes can be adjusted for different use cases (e.g., ReadWriteMany for shared storage).
Application-agnostic: Pods don't need to know the underlying storage details.
Data Persistence: Data remains intact even if pods are deleted or rescheduled.
To apply these YAML files:

Save each definition in separate files (e.g., pv.yaml, pvc.yaml, pod.yaml).
Use kubectl apply -f pv.yaml -f pvc.yaml -f pod.yaml to create the PV, PVC, and pod.

## HEALTHCHECK / LIVENESSPROBE
## 1. Health Checks:

Kubernetes periodically performs health checks on your containers using probes. These probes are configurable scripts or commands that verify if the container is still functioning properly.
There are three types of probes:
Readiness Probe: Determines if a container is ready to receive traffic.
Liveness Probe: Determines if a container is still running properly. If the liveness probe fails, the kubelet (Kubernetes agent on the node) will restart the container.
Startup Probe: Used for slow-starting containers, it allows some extra time for the container to be ready before failing a liveness probe.
These probes can be configured in your pod specifications using YAML.

## 2. Liveness Probe:

Focusing on "LIVENESSPROBE" specifically, it is a type of health check that tells Kubernetes whether a container is truly alive and functioning as expected. This is crucial for ensuring high availability and preventing unresponsive containers from serving traffic.
You can define the liveness probe using three methods:
Command: Executing a script or command within the container.
HTTP Get: Sending an HTTP request to a specific endpoint within the container.
TCP Socket: Attempting to open a TCP connection to a port within the container.
If the liveness probe fails a certain number of times (configurable), the kubelet will automatically restart the container. This helps to automatically recover from crashes, deadlocks, or other issues that might render the container non-functional.
Overall, "HEALTHCHECK / LIVENESSPROBE" is a crucial aspect of application deployment and management in Kubernetes. It ensures that only healthy and responsive containers receive traffic, leading to a more reliable and resilient system.

## Pod using the PVC, with a Liveness Probe:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: task-pv-pod
spec:
  containers:
    - name: task-pv-container
      image: nginx
      ports:
        - containerPort: 80
          name: "http-server"
      volumeMounts:
        - mountPath: "/usr/share/nginx/html"  # Mount path within the container
          name: task-pv-storage
      livenessProbe:
        httpGet:
          path: /  # Check the root path of the web server
          port: 80
        initialDelaySeconds: 15  # Delay before first probe
        periodSeconds: 20  # Probe every 20 seconds
        timeoutSeconds: 5  # Timeout for each probe
        failureThreshold: 3  # Restart after 3 consecutive failures
  volumes:
    - name: task-pv-storage
      persistentVolumeClaim:
        claimName: task-pv-claim
```

### Key Points:

Apply each definition in separate files (e.g., pv.yaml, pvc.yaml, pod.yaml) using kubectl apply -f FILENAME.
Adjust storage size, access mode, and probe details as needed for your specific application.
Consider using a StorageClass for dynamic provisioning of PVs.
Explore other probe types (command or TCP) if HTTP probes aren't suitable.
Customize probe parameters (initial delay, period, timeout, failure threshold) based on your application's startup time and health check requirements.

## ConfigMaps and Secrets
Both ConfigMaps and Secrets in Kubernetes manage configuration data for your deployed applications, but they have distinct purposes and security considerations:

## ConfigMaps:
```YAML
apiVersion: v1
kind: ConfigMap
metadata:
  name: my-configmap
data:
  # Non-confidential key-value pairs
  app-name: my-app
  log-level: DEBUG
  db-url: jdbc:mysql://my-database:3306/my-app
  ```
  #### Pod using the ConfigMap:

  ```yaml
YAML
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
spec:
  containers:
    - name: my-container
      image: my-app-image
      envFrom:
        - configMapRef:
            name: my-configmap
      # Alternatively, use individual env variables:
      # env:
      #   - name: APP_NAME
      #     valueFrom:
      #       configMapKeyRef:
      #         name: my-configmap
      #         key: app-name
  # ... (other pod configuration)
  ```
Purpose: Store non-confidential configuration data in key-value pairs. This can include environment variables, URLs, database connection strings, application settings, etc.
Security: Data is stored in plain text and not encrypted. Anyone with access to the Kubernetes API server can view the contents of ConfigMaps.
Benefits:
Centralized configuration: Decouple configuration from container images, simplifying deployments and updates.
Environment abstraction: Eliminate hardcoded configuration in environments, improving portability and consistency.
Easy sharing: Mount ConfigMaps as volumes or environment variables in any pod within a namespace.
Use cases: Configuring application logging levels, database usernames, API endpoint URLs, etc.

## Secrets:

Purpose: Securely store sensitive data like passwords, API keys, tokens, certificates, etc.
Security: Data is base64 encoded and potentially further encrypted depending on your cluster configuration. Only authorized users with specific permissions can access Secrets.
Benefits:
Enhanced security: Protect sensitive data from accidental exposure or unauthorized access.
Simplified rotation: Update secrets without recompiling or redeploying container images.
Centralized management: Manage secrets efficiently across multiple applications and environments.
Use cases: Storing database passwords, service account tokens, encryption keys, etc.

```YAML
apiVersion: v1
kind: Secret
metadata:
  name: my-secret
type: Opaque  # Common type for generic secrets
data:
  # Base64-encoded sensitive data
  db-password: MWYyZDFlMmU2N2Rm
  api-key: YWRtaW4=
Use code with caution. Learn more

```

### Pod using the Secret:

```YAML
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
spec:
  containers:
    - name: my-container
      image: my-app-image
      envFrom:
        - secretRef:
            name: my-secret
      # Alternatively, use individual env variables:
      # env:
      #   - name: DB_PASSWORD
      #     valueFrom:
      #       secretKeyRef:
      #         name: my-secret
      #         key: db-password
  # ... (other pod configuration)
```
### Key Points:
Apply each definition using kubectl apply -f FILENAME.
ConfigMap data is in plain text, while Secret data is base64 encoded.
Use kubectl get configmap and kubectl get secret to view them.
Access data in pods using environment variables or mounted volumes.
Exercise caution with Secrets due to their sensitive nature.


## Jobs
```yaml
apiVersion: batch/v1
kind: Job
metadata:
  name: testjob
spec:
  template:
    metadata:
      name: testjob
    spec:
      containers:
      - name: counter
        image: centos:7
        command: ["bin/bash", "-c", "echo Technical-Guftgu; sleep 5"]
      restartPolicy: Never
--------------
apiVersion: batch/v1
kind: Job
metadata:
  name: testjob
spec:
  parallelism: 5                           # Runs for pods in parallel
  activeDeadlineSeconds: 10  # Timesout after 30 sec
  template:
    metadata:
      name: testjob
    spec:
      containers:
      - name: counter
        image: centos:7
        command: ["bin/bash", "-c", "echo Technical-Guftgu; sleep 20"]
      restartPolicy: Never```