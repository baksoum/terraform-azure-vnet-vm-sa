# terraform-azure-vnet-vm storage account

This repository contains an Infrastructure as Code (IaC) example for creating a web server with a custom webpage, using Terraform and deploying it on Microsoft Azure.

Getting Started

To set up the environment and deploy the infrastructure, follow the steps below:

# Prerequisites

Terraform installed
Azure account and access credentials

Steps

Clone the repository:

git clone https://github.com/baksoum/terraform-azure-vnet-vm.git
cd terraform-azure-vnet-vm


Initialize Terraform:

terraform init


Apply the Terraform configuration:

terraform apply


After running this command, Terraform will prompt you to confirm the action. Type yes to proceed.

Retrieve the SSH private key:
Once the infrastructure has been provisioned, retrieve the private key for SSH access with the following command:

terraform output -raw ssh_private_key > cleduserveur.key


Set permissions for the SSH key:
Secure the private key by setting the appropriate file permissions:

chmod 600 cleduserveur.key


Access the server:
You can now SSH into the server using the private key:

ssh -i cleduserveur.key <username>@<public-ip>


Replace <username> with the appropriate user and <public-ip> with the public IP address of the server, which can be found in the output of the Terraform deployment.

Notes

This setup creates a basic Azure Virtual Network (VNet) and a virtual machine (VM) with a custom webpage.

Make sure your Azure credentials are properly configured, either via environment variables or a service principal.
