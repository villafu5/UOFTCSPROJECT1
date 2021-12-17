#### Domain: Network Security

**Question 1:  Faulty Firewall**

Suppose you have a firewall that's supposed to block SSH connections, but instead lets them through. 
How would you debug it?

It is important that firewall rules are configured properly as they are primarily the first line of defense between a system's internal network and the external network. Secure Shell (SSH) allows an individual to remotely access a system from their own device usually through port 22. There are various entities that are actively searching for open access through this port. In this scenario, each and every SSH  connection is allowed through the firewall, which in turn leaves the network vulnerable to remote attacks.

In Project 1 of my Cybersecurity boot camp, we created an Azure virtual network that contained various virtual machines (VMs), which only I was able to access via SSH by creating firewall rules that regulated remote access controls. First we created a “DenyAllInBound” rule that denied access to the virtual network from every source, port and protocol. After creating this rule, we were then able to create an “SSH allow” rule that allowed us to access the virtual network from our own local ip address by connecting to the Virtual JumpBox. After accessing the Virtual Jumpbox machine, we could then connect to the two virtual machines that were created within the network. Overall, each VM accepted SSH connections with certain restrictions in place in order to control remote access into the network. This in turn protects the network from any unwanted access via SSH as only authorized individuals are able to connect to the device while unauthorized connections will be refused.

Assuming that only one VM is accepting SSH connections while the other is not, we can assume that the source of error lies within the configuration of the network security group. First I would double check if the source and destination ip addresses for the SSH rules are correct as one may have used the dynamic public ip address instead of the private ip address of the virtual machines. Another configuration that may be incorrect would be adding the virtual machine to the wrong resource group or virtual network. After ensuring that the configurations are correct, the connections can then be tested by SSHing into the machine that was having the initial error.

By configuring the firewall rules for the entire network, we allowed SSH connections from only authorized users. These rules allowed the local user to SSH into the jump box provisioner and from there, the user was able to SSH into the virtual machines within the network. To ensure that only the local user was able to SSH into these machines, we used a public-private key binding pair which basically ensures that only the host user is the only individual with authorized access to this network. Lastly, we can add an intrusion prevention system (IPS) and an intrusion detection system (IDS) to monitor, log and mitigate any suspicious authentication attempts.
	

