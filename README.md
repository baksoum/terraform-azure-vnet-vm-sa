Infrastructure Overview

This Terraform configuration sets up a basic infrastructure on Azure. It deploys a Linux virtual machine (VM) with a custom Apache2 web server, as well as the necessary networking and security components. Below is a high-level overview of the resources being created:

1. Resource Group

A Resource Group is created to contain all the Azure resources. This acts as a container to manage and organize the resources within the deployment.

2. Storage Account

A Storage Account is provisioned to store and manage resources such as virtual machine disks, backups, and other data in Azure. The account uses Locally Redundant Storage (LRS) for redundancy.

3. Virtual Network (VNet)

A Virtual Network (VNet) is created to host the infrastructure in a secure network. The network has a defined address space (10.0.0.0/16), and it enables communication between the virtual machine and other resources in the Azure environment.

4. Subnet

A Subnet is created within the virtual network to segment the address space. This subnet will house the virtual machine and allows you to apply specific network rules.

5. Public IP Address

A Public IP Address is allocated to provide external access to the virtual machine. This IP will be used to connect to the VM via SSH and HTTP.

6. Network Interface

A Network Interface (NIC) is created to connect the virtual machine to the virtual network. The NIC is configured with a dynamic private IP and the previously allocated public IP.

7. Linux Virtual Machine

A Linux Virtual Machine is deployed using the Ubuntu 22.04 LTS image. This VM is configured with SSH key authentication, and password authentication is disabled for security. It also installs a custom Apache2 web server through a cloud-init script, making it ready to serve web content.

8. Network Security Group (NSG)

A Network Security Group (NSG) is configured to control inbound traffic to the virtual machine. The NSG allows SSH access (port 22) and HTTP access (port 80) to the VM from any source.

9. SSH Key

An SSH Key is generated to provide secure access to the virtual machine. The public key is deployed on the VM, while the private key is saved locally for SSH access.

10. NSG Association to Subnet

The Network Security Group (NSG) is associated with the subnet, ensuring that the security rules (such as allowing SSH and HTTP) are applied to the virtual machine within the subnet.

Deployment Steps

Clone the Repository:

git clone https://github.com/<your-username>/terraform-azure-vnet-vm.git
cd terraform-azure-vnet-vm


Initialize Terraform:

terraform init


Apply the Configuration:

terraform apply


Confirm the action by typing yes.

Access the Virtual Machine:
Once the VM is deployed, you can access it using SSH:

ssh -i cleduserveur.key <admin-username>@<public-ip>


Ce texte résume les différentes ressources et leur rôle dans l'infrastructure déployée. Les utilisateurs peuvent suivre les étapes pour initialiser et appliquer cette configuration.
