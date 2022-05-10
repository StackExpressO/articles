**Documentation for EKS**

Creating an Amazon EKS cluster

1. Go to the aws console and choose the region and search for eks on navigation bar

![](Aspose.Words.3536303c-37c2-4423-ade8-b6504f62d085.001.png)

2. Click on Elastic Kubernetes Service it will navigate to the page and then click on clusters and then click on create cluster

![](Aspose.Words.3536303c-37c2-4423-ade8-b6504f62d085.002.png)

3. After click on create cluster we need to select cluster template (EC2 Linux)

![](Aspose.Words.3536303c-37c2-4423-ade8-b6504f62d085.003.png)

4. After selecting the cluster template (EC2 Linux) click on Next step
5. Now we need to configure the cluster by define cluster name and instance type and number of instances and VPC and instance IAM role etc . 

![](Aspose.Words.3536303c-37c2-4423-ade8-b6504f62d085.004.png)

![](Aspose.Words.3536303c-37c2-4423-ade8-b6504f62d085.005.png)

6. After completion of cluster configuration click on create it will create the eks cluster

**Deploy application to EKS**

**Prerequisites**

1. Existing kubernetes cluster
1. Install kubectl on computer  

`   `curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/ 1.21.2/2021-07-05/bin/linux/amd64/kubectl

`   `To install kubectl for different kubernetes versions ( https:// docs.aws.amazon.com/eks/latest/userguide/install-kubectl.html )

3. We need to configure kubectl to communicate with the cluster for that we need to create kubeconfig for Amazon EKS, to create kubeconfig we need to    install AWS-CLI on our computer.

**Install aws-cli**

curl "https://awscli.amazonaws.com/awscli-exe-linux-x86\_64.zip" -o "awscliv2.zip"

unzip awscliv2.zip

sudo ./aws/install

./aws/install -i /usr/local/aws-cli -b /usr/local/bin

aws --version

Refer this link for aws-cli installation - [https://docs.aws.amazon.com/eks/latest/](https://docs.aws.amazon.com/eks/latest/userguide/create-kubeconfig.html)

[userguide/create-kubeconfig.html](https://docs.aws.amazon.com/eks/latest/userguide/create-kubeconfig.html)

4. After completion of **aws-cli** installation we need to create kubeconfig file     **To Create kubeconfig file automatically follow the steps**
- Check the aws-cli version by run the command **aws --version**
- Create or update a kubeconfig file for your cluster

`             `**aws eks update-kubeconfig --region region-code --name cluster-name**

- Test your configuration 

`             `**kubectl get svc**

Refer this link for creating kubeconfig - [https://docs.aws.amazon.com/eks/ latest/userguide/create-kubeconfig.html](https://docs.aws.amazon.com/eks/latest/userguide/create-kubeconfig.html)

**Steps to deploy application to EKS**

1. To deploy the appilcation to eks we need to clone the code templates 

(https://gitlab.com/stackexpresso/devops/code-templates/-/tree/master/ kubernetes/. application-deployments/nginx-example)

2. Create a namespace

`       `For example - kubectl create namespace example

3. To Deploy the application to EKS first we need to apply the deployment.yaml file (nginx-example-web-deployment.yaml) which we have in code templates   

![](Aspose.Words.3536303c-37c2-4423-ade8-b6504f62d085.006.png)    To apply the deployment manifest file we need to run the following command **kubectl apply -f nginx-example-web-deployment.yaml**

4. Instead of hard coding the values in the deployment file we can create secrets.yaml file

`       `Example:

![](Aspose.Words.3536303c-37c2-4423-ade8-b6504f62d085.007.png)

` `To apply secret.yml file run **kubectl apply -f secret.yml**

5. After apply the deployment file we need to apply service manifest file (nginx-example-web-service.yaml ) which we have in code templates

    then it will make our application accessible

![](Aspose.Words.3536303c-37c2-4423-ade8-b6504f62d085.008.png)

`       `To apply the service manifest file we need to run the following command   

`        `**kubectl apply -f nginx-example-web-service.yaml**        it will create the service for our application.

6. Now we need to apply the ingress file (nginx-example-ingress.yaml) which we have in code templates, ingress will manage external access to our service

![](Aspose.Words.3536303c-37c2-4423-ade8-b6504f62d085.009.png)        To apply the ingress we need to run the following command **kubectl apply -f nginx-example-ingress.yaml** it will apply the ingress rules for our service

7. To see the all resources exist in the name space run kubectl get all -n example
7. Now we need to create ssl certificate for that follow the link - **https:// kubernetes.io/docs/tasks/administer-cluster/certificates/**
