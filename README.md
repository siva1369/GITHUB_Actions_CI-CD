GITHUB Action:-
-------------
Setup Project Repo
Create Pipeline & Run on Shared Runner 
Configure VM as a Private Runner
Set Up SonarQube Server
SonarQube Job in Pipeline
Setup Docker Job in Pipeline
Setup EKS Kubernetes Cluster
Kubernetes Job in Pipeline



if we run the cicd in Jenkins we need some resources (mechines) and setup of master slave. cost effective


in GitHub actions here no master and slave , just we have GitHub account ,
simply start writing cicd , here we have a concept of runners it means slaves.

in runners we have two types 

1. shared runners (free by github) here we can not access backend.


2. private runners; here we hae own VM controlled by our's 




setups;

1. github repo

2. VM as runner

3. CI-CD 

security checks
test cases
build application
publish the artifact
docker build and docker push
deploy the application to k8s.


add the self-hosted runner (ec2 mechine) follow the GitHub actions 

./run.sh


then create SonarQube server

t2 medium 

9000

25gb

connect



sudo apt update

sudo apt-get install docker.io

sudo usermod -aG docker $USER

newgrp docker

docker run -d --name sonar -p 9000:9000 SonarQube:lts-community

IP:9000


sonar get started




install unzip in runner

docker install on runner also


sudo usermod -aG docker ubuntu

newgrp docker

run the runner again 

./run.sh

------------------------------------------------------------------------------------------

EKS :- using terraform
-----

ec2 - ubuntu

t2 medium

25 Gb

launch

connect


install aws cli and terraform:-
-------------------------------

install aws cli:-
----------------

create security credentials

1. Update packages and install unzip + curl if not already installed
sudo apt update
sudo apt install unzip curl -y

2. Download the latest AWS CLI v2 package
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"

3. Unzip the package
unzip awscliv2.zip

4. Run the installer
sudo ./aws/install

5. Verify installation
aws --version


aws configure

give access and secret access key




install terraform:-
-------------------

# 1. Update system and install required dependencies
sudo apt update && sudo apt install -y gnupg software-properties-common curl

# 2. Add HashiCorp GPG key
curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg

# 3. Add HashiCorp repository
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | \
  sudo tee /etc/apt/sources.list.d/hashicorp.list

# 4. Update and install Terraform
sudo apt update && sudo apt install terraform -y

# 5. Verify installation
terraform -version


clone the repository of terraform files

git clone https://github.com/siva1369/K8S-EKS--Terraform.git

cd terraform

terraform init

terraform apply

eks setup got to done on aws cloud

--------------------------------------------------------------------------------------------

install kubectl:-
----------------


# 1. Update the apt package index and install dependencies
sudo apt update
sudo apt install -y apt-transport-https ca-certificates curl

# 2. Download the Google Cloud public signing key
sudo curl -fsSLo /usr/share/keyrings/kubernetes-archive-keyring.gpg \
  https://packages.cloud.google.com/apt/doc/apt-key.gpg

# 3. Add the Kubernetes APT repository
echo "deb [signed-by=/usr/share/keyrings/kubernetes-archive-keyring.gpg] \
  https://apt.kubernetes.io/ kubernetes-xenial main" | \
  sudo tee /etc/apt/sources.list.d/kubernetes.list

# 4. Update package index and install kubectl
sudo apt update
sudo apt install -y kubectl

# 5. Verify the installation
kubectl version --client



---------------------------------------------------------------------------------------------------------------
kubectl get pods ; we are not able to get the information because we are not configured.

-----------------------------------------------------------------------------------------------------



setup kubeconfig file:-
----------------------

aws eks --region ap-south-1 update-kubeconfig --name <give name>



kubeconfig is a file which contains complete information about cluster, it can also used as authentic ation of cluster.

for authentication 

cat ~/.kube/config  

we get a key copy all and add in secret block in GitHub .


----------------------------------------------------------------------------------------------

kubectl get nodes

--------------------------------------------------------------------------------------------------------
kubectl get all

---------------------------------------------------------------------------
