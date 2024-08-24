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
The Red Team Resource Group contains our network, firewalls and virtual environments and will hold all of our VMs, jump-box and load balancer. Once we had implemented our resource group, our virtual network was added which will allow our virtual machines to communicate with each other on the network. Our virtual network will behave just like a physical one, and each VM will still have a designated IP address.
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
<br>
Each of these components run through our Network Security Group (RedTeamNSG) which acts as our firewall on the network. The NSG has been configured to only allow SSH connection via the listed IP addresses. We will then use our jump-box to SSH into either of our Web VMs. In order to do this, our VMs were configured with docker containers and Ansible to allow for SSH public/private key integration.
<br>
<br>
Our load balancer (RedTeam_LB) has been set up to mitigate against DoS attacks. It will recieve traffic and distribute it across our servers to prevent one specific machine being overloaded in the event of an attack. A health probe was configured to monitor the load balancer. This connection was created and uses port 80 (TCP) to operate.
<br>






