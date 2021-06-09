## Create Amazon EKS cluster using Terraform

The purpose of this tutorial is to create an EKS cluster (3 nodes) with Terraform. Amazon Elastic Kubernetes Service (Amazon EKS) is a fully managed Kubernetes service by AWS.

## What is AWS EKS?

Amazon Elastic Kubernetes Service (Amazon EKS) gives you the ability to start, run, and scale Kubernetes applications in the AWS cloud or on-premises. Amazon EKS helps you deliver highly available and secure clusters and automates key tasks such as patching, node commissioning, and upgrades. Customers such as Intel, Snap, Intuit, GoDaddy, and Autodesk prefer EKS to run their most sensitive and critical applications.

EKS runs Kubernetes upstream and is certified Kubernetes compliant for a predictable experience. You can easily migrate any standard Kubernetes application to EKS without the need to refactor your code.

EKS makes it easy to standardize operations across environments. You can run fully managed EKS clusters on AWS. You can have a proven open source distribution of Kubernetes anywhere you want for consistent operations with Amazon EKS Distro.

![AWS EKS, AWS EKS infra](/images/aws-eks.png)


## Prerequisites

Before you get started, you’ll need to have these things:
* Terraform > 0.13.x
* kubectl installed on the compute that hosts terraform
* An AWS account with the IAM permissions
* AWS CLI : [the AWS CLI Documentation](https://github.com/aws/aws-cli/tree/v2){:target="_blank" }
* AWS IAM Authenticator : [the AWS IAM Authenticator Documentation](https://docs.aws.amazon.com/eks/latest/userguide/install-aws-iam-authenticator.html){:target="_blank" }


## Initial setup

The first thing to set up is your Terraform. We will create an AWS IAM users for Terraform.
In your AWS console, go to the IAM section and create a user named “FullAccess”. Then add your user to a group named “FullAccessGroup”. Attaches to this group the following rights:

```

AdministratorAccess
AmazonEKSClusterPolicy

```
fter these steps, AWS will provide you a Secret Access Key and Access Key ID. Save them preciously because this will be the only time AWS gives it to you.

In your own console, create a **~/.aws/credentials** file and put your credentials in it:
```
[default]
 aws_access_key_id=***********
 aws_secret_access_key=****************************

```

Creating the EKS cluster is pretty easy by just running terraform apply.
Clone the repository and install the dependencies:

```

$ git clone https://github.com/colussim/terraform-aks-aws.git
$ cd terraform-aks-aws
$ terraform init

```

The terraform template installs a three worker nodes cluster with an instance of type : t2.large.
These parameters can be changed in the file :  **ek-cluster.tf**

## Usage

Create an EKS Cluster :

```
$ terraform apply
```

After 15 minutes the cluster is up running

Tear down the whole Terraform plan with :

```
$ terraform destroy -force
```

Resources can be destroyed using the terraform destroy command, which is similar to terraform apply but it behaves as if all of the resources have been removed from the configuration.

## Conclusion

With Terraform, booting a EKS cluster can be done with a single command and it only takes some minutes to get a fully functional configuration.
Next step : deploy an application in our cluster .

## Resources :

![Documentation, the Terraform Documentation](https://www.terraform.io/docs/index.html "the Terraform Documentation")

![Documentation, Provision an EKS Cluster (AWS)](https://learn.hashicorp.com/tutorials/terraform/eks "Provision an EKS Cluster")

![Documentation, the AWS IAM Authenticator for Kubernetes](https://github.com/kubernetes-sigs/aws-iam-authenticator "the AWS IAM Authenticator for Kubernetes")

![Documentation, the AWS CLI](https://github.com/aws/aws-cli/tree/v2 "the AWS CLI")


Next step , see details 
![here](https://techlabnews.com/2021/terraform-EKS-AWS/index.html "Create Amazon EKS cluster using Terraform")

