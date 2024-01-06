# EKSCTL-DEMO-TODO

#### Pre-requisites: 
  - an EC2 Instance (Note : If Using Ubuntu EC2 Instance instead of Amazon Linux then Make Sure to have **aws-iam-authenticator** installed.)


#### Article to Install aws-iam-authenticator :
```sh
https://docs.aws.amazon.com/eks/latest/userguide/install-aws-iam-authenticator.html
curl -o aws-iam-authenticator https://amazon-eks.s3.us-west-2.amazonaws.com/1.22.1/2021-07-05/bin/darwin/amd64/aws-iam-authenticator
chmod +x ./aws-iam-authenticator
mv ./aws-iam-authenticator /usr/local/bin/aws-iam-authenticator

```

#### AWS EKS Setup 
1. Setup kubectl   
   a. Download kubectl  
   b. Grant execution permissions to kubectl executable   
   c. Move kubectl onto /usr/local/bin   
   d. Test that your kubectl installation was successful    
   ```sh 
   curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/1.19.6/2021-01-05/bin/linux/amd64/kubectl
   chmod +x ./kubectl
   mv ./kubectl /usr/local/bin 
   kubectl version --short --client
   ```
2. Setup eksctl   
   a. Download and extract the latest release   
   b. Move the extracted binary to /usr/local/bin   
   c. Test that your eksclt installation was successful   
   ```sh
   curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
   sudo mv /tmp/eksctl /usr/local/bin
   eksctl version
   ```
  
3. Create an IAM Role and attach it to EC2 instance    
   `Note: create IAM user with programmatic access if your bootstrap system is outside of AWS`   
   IAM user should have access to   
   IAM   
   EC2   
   VPC    
   CloudFormation
   EKS
   Administrator

4. Create your cluster and nodes 
   ```sh
   eksctl create cluster --name cluster-name  \
   --region region-name \
   --node-type instance-type \
   --nodes-min 2 \
   --nodes-max 2 \ 
   --zones <AZ-1>,<AZ-2>
   
   example:
   eksctl create cluster --name todo-cluster \
   --region ap-south-1 \
   --node-type t2.small \
   --nodes-min 2 \
   --nodes-max 2
    ```




## Docker

To build a docker image for the todo-list-app and run it inside a container execute

```sh
docker build -t dockerhub9876/todo .
```


## Kubernetes

To Apply deployment.yaml

```sh
kubectl apply -f deployment.yaml
```


To Apply service.yaml

```sh
kubectl apply -f service.yaml
```


## Screenshots ( Whole Process Can take 20-25 Minutes which is normal in creating Cluster)

<img width="548" alt="image" src="https://user-images.githubusercontent.com/110477025/210777883-4eafd817-64ce-4ade-8952-7d6cab8a9d81.png">


![image](https://user-images.githubusercontent.com/110477025/210777995-c1308f1a-0b75-4c59-96ee-c5f1be7b3fff.png)


<img width="549" alt="image" src="https://user-images.githubusercontent.com/110477025/210778102-3ebf4770-6fb3-4b82-bf51-ade2c330c52b.png">


<img width="549" alt="image" src="https://user-images.githubusercontent.com/110477025/210778171-c04f3b85-dd77-48ae-892e-b750b6307353.png">






