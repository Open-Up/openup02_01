# TP 1

## Question 1

### Step 1 : creating virtual machines

Importing debian.ova once

(reset MAC address + name it server)

Importing again debian.ova

(reset MAC address + name it client)

### Step 2 : adding a network adapter to each virtual machine

 1. Click on server
 2. Click on settings
 3. Click on network
 4. Click on adapter 2
 5. Click on enable network
 6. Click on internal network
 7. OK

Do it again for the client

### Step 3 : configure a static ip address for our DHCP server

Boot server

Login : root
Password : 1234

Edit /etc/network/interfaces

add these lines at the bottom :

```

auto eth1
iface eth1 inet static
    address 192.168.102.4
    netmask 255.255.255.0
```

And restart the network : /etc/init.d/networking restart

### Step 4 : install isc-dhcp-server

On server :

    apt-get install isc-dhcp-server

### Step 5 : configuring the server

Edit /etc/default/isc-dhcp-server and add :

```
INTERFACES="eth1"
```

Then edit /etc/dhcp/dhcpd.conf and add a subnetwork :

```

subnet 192.168.102.0 netmask 255.255.255.0 {
  range 192.168.102.10 192.168.102.254;
} 
```

Restart the DHCP server /etc/init.d/isc-dhcp-server restart

### Step 6 : configure the client to demand an IP on the private network

Edit /etc/network/interfaces on the client and add these lines :

```

auto eth1
iface eth1 inet dhcp

```

And restart the network : /etc/init.d/networking restart

### Step 7 verifying that it works

On the client : ifconfig should return an address in the range configured on the server.

On the server /var/lib/dhcp/dhcpd.leases should contain your client lease.
