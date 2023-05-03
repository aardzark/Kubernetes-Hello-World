# Getting Started
1. Create a new EC2 Ubuntu Server instance with 2 CPU cores
2. Add a security group that allows incoming traffic on port 80 and add it to the instance
3. Install necessary packages:
   - `sudo apt-get update && sudo apt-get install -y apt-transport-https gnupg2 curl docker.io`
   - `curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -`
   - `echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list`
   - `sudo apt-get update`
   - `sudo apt-get install -y kubectl`
4. Download and install Minikube:
   - `curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 && chmod +x minikube`
   - `sudo mv minikube /usr/local/bin/`
5. Add current user to docker group:
   - `sudo usermod -aG docker $USER`
   - `newgrp docker`
6. Start Minikube with Docker driver and port forwarding:
   - `minikube start --driver=docker --ports=80:30080`
   - `minikube addons enable ingress`
7. Clone the Kubernetes-Hello-World repository:
   - `git clone https://github.com/aardzark/Kubernetes-Hello-World.git`
   - `cd Kubernetes-Hello-World`
8. Deploy the application with Kubernetes:
   - `kubectl apply -f hello-world-deployment.yaml`
   - `kubectl apply -f hello-world-service.yaml`
   - `kubectl apply -f hello-world-ingress.yaml`
9. Get the public IP address of the EC2 instance:
   - `curl ifconfig.me`
10. Visit the public IP address of the EC2 instance to access the application
