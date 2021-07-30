# Bastion Server
A bastion host is a server whose purpose is to provide access to a private network from an external network, such as the Internet. 

It is designed to be the primary access point from the Internet and acts as a proxy to your other EC2 instances. 

![img](img/NM_diagram_061316_a1.png)

Activity:


# Crearting a Bastion instance 

1. **Create a DB instance**

Create a DB EC2 instance with:
 - **Network**: VPC 
 - **Subnet**: Private Subnet 
 - **Auto-assign Public IP**: Enabled

2. **Create new SG**

Create a new security group and add the inboud rules:
- SSH -> 22 -> 'My IP'
- SSH -> 22 -> 
- Custom -> 27017 ->

3. **Create a Bastion instance**

Create a new EC2 instance with:
- **Newtork**: VPC 
- **Subnet**: Public subnet
- **Auto-assign Public IP**: Enabled 

4. **SSH into Bastion VM**

Using the Bastion IP code ssh into the bastion instance:

`ssh -i ~/.ssh/eng89_devops.pem ubuntu@VM_IP_ADRESS`

If any erros occur it may be because the VM does not have the key yet so we must send the key to the VM. To transfer the key I went into the ssh directory and used :

`scp -i ~/.ssh/eng89_devops.pem eng89_devops.pem ubuntu@54.155.64.23:/home/ubuntu/.ssh/`

You should now be able to view the key in your VM.


5. **SSH into the DB instance from the Bastion instance**

Using the private IP ssh into the DB instance. 

Note: Private Ip is located under `Description`

If errors occure it could be because of permission errors. Use this command on the key and then ssh into db using the private ip:

`chmod 600 eng89_devops.pem`

6. **Complete**

You should now hav eentered the DB instance via the bastion instance. 
