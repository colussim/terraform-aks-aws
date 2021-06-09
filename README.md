Create Amazon EKS cluster using Terraform

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
