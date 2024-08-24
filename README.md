# Cloud Security

<h2>Scenario</h2>
During our in-class activities we focused on configuring and setting up 3 VMs running VDWA through the use of Azure Labs. Within the virtual network, a variety of tools and policies were implemented, including:
<ul>
  <li>Network Security Groups</li>
  <li>Resource Groups</li>
  <li>Load Balancers</li>
  <li>Jump Box Provisioners</li>
  <li>Azure Lab VMs</li>
  <li>DVWA and Docker Containers</li>
</ul>
<br>
<h2>Deliverable</h2>
The image below presents my final deliverable for this task:
<br>
<br>
<img src="https://github.com/bailey-curtis/Cloud-Security/blob/main/Cloud%20Security%20Deliverable.png">
<br>
<br>
<b>Summary</b>
<br>
The following diagram was create within draw.io and outlines a cloud infrastructure network, which was created with Azure Labs.
<br>
<br>
Our initial steps in creating the network involved creating our Red Team Resource Group, which will contain our network, firewalls and virtual environments.
<br>
<br>
Once we had implemented our resource group, our virtual network was added which will allow our virtual machines to communicate with each other on the network. Our virtual network will behave just like a physical one, and each VM will still have a designated IP address.
<br>
<br>
In order to harden our network, a network security group (NSG) was added. This will act as our basic firewall and will be used to block and allow traffic between our machines and the virtual network.
<br>
<br>
VMs were then added accordingly, and set up with SSH keys. In order to do this, the following command was executed, which allowed us to create public/private key pair:
<br>
<b>ssh-keygen -t rsa</b>
<br>
<br>
Once our key was generated, we ran <b>cat</b> against our new <b>id_rsa.pub</b> key. <br>
The key string was copied and pasted into Azure's Administrator Account sections for the corresponding VM in Azure.
<br>
In conclusion, this has allowed us to create an administrator account on the machine which will have SSH access. This specific machine will be our jump box provisioner and will be used to access our other machines on the network.
<br>
<br>
To configure the newly created machine, we identify our public IP address via entering the command <b>curl icanhazip.com</b> onto thew command line. We want to use of IPv4 address, and not our IPv6.
<br>
Once we have our IP, we had to create a rule within our security group to allow SSH connections through our public IP address to our internal VM's IP address.
<br>
<br>
Docker was used to manage our containers within the other VMs on the network.
<br>
<b>cyberxsecurity/ansible</b> was pulled once docker was installed - this container will be the foundation for your VMs. Once these were successfully installed, a new security group rule was applied to allow our jump box full access to the virtual network.
<br>
<br>





