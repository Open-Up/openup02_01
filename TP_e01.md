#### TP DHCP

In this practical work (1h30), you will install a dhcp server and use it to give an IP address to a DHCP client. You will
test the different configuration options explained during the course, that is to know dynamic, static, and, if you have enough time,
a REST dhcp server. You will also discover **arpwatch**.

##### Q1 Dynamic DHCP server

Deploy a dynamic DHCP server and request an address with an other virtual machine.

- Start Virtual box
- Load the debian image
- Create an additional private network
- Boot 2 virtual machines
- add an interface on private network for both machines
- Give the server a fixed address on the private network
- Install DHCPD on the server
- Configure dynamically on your private network
- Restart DHCPD
- Configure your client to ask for an address on private network
- Restart networking on your client
- Observe the client's address + the lease file

##### Q2 Static configuration

Modify your above installation to give a static IP address to your client.

- Obtain MAC address of your client by command line
- Modify your server configuration
- Restart DHCPD
- Restart / reboot your client
- Observe the client's address + the lease file

##### Q3 Security (bonus)

Install **arpwatch** to see new MAC/IP associations.

- Install arpwatch on the DHCP server
- Configure it to send mails to root@localhost
- Boot a *pirate VM*
- Give it a fixed address on your private network
- Observe your mails

##### Clean Up

Destroy your VMs and your private network
