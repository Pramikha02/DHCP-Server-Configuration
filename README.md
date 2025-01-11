# DHCP-Server-Configuration

**DHCP (Dynamic Host Configuration Protocol)** is used to automatically assign IP addresses and other network configuration parameters to devices on a network. Here are the key points for DHCP configuration:

### 1. **DHCP Overview**:
   - **Purpose**: DHCP automates IP address assignment, reducing the need for manual configuration.
   - **Components**:
     - **DHCP Server**: A device that provides IP addresses and other configuration parameters (e.g., DNS servers, gateway).
     - **DHCP Client**: A device (e.g., computer, printer) that requests configuration information from a DHCP server.
     - **DHCP Lease**: The temporary assignment of an IP address to a client for a specified time.

### 2. **DHCP Configuration Steps**:
   - **Step 1: Configure DHCP Server**: 
     - Set up the DHCP pool (range of IP addresses) from which the server will assign IP addresses.
     - Define default gateway, DNS server, lease duration, and other options.
   
   - **Step 2: Configure Network Interface**:
     - Enable DHCP on the network interface of the router or server that will function as the DHCP server.
   
   - **Step 3: Enable DHCP on Client Devices**:
     - Configure client devices to obtain an IP address automatically (DHCP client mode).

### 3. **DHCP Server Configuration Example (Cisco Router)**:
```shell
ip dhcp pool CLIENTS
   network 192.168.1.0 255.255.255.0
   default-router 192.168.1.1
   dns-server 8.8.8.8
   lease 7
```
   - **ip dhcp pool CLIENTS**: Defines the DHCP pool named "CLIENTS."
   - **network 192.168.1.0 255.255.255.0**: Specifies the network and subnet mask.
   - **default-router 192.168.1.1**: Sets the default gateway for clients.
   - **dns-server 8.8.8.8**: Configures the DNS server.
   - **lease 7**: Specifies the lease duration in days.

### 4. **DHCP Lease Process**:
   - **Discover**: The client broadcasts a DHCP Discover message.
   - **Offer**: The server responds with a DHCP Offer message containing an available IP address.
   - **Request**: The client sends a DHCP Request message to the server to accept the offered IP address.
   - **Acknowledge**: The server sends a DHCP Acknowledgement message confirming the assignment.

### 5. **DHCP Options**:
   - **Option 1**: Subnet Mask
   - **Option 3**: Default Gateway (Router)
   - **Option 6**: DNS Server
   - **Option 15**: Domain Name

### 6. **DHCP Exclusions**:
   - **Exclusion Range**: Some IP addresses may be excluded from the DHCP pool to ensure they are not dynamically assigned (e.g., for servers or printers).
   - **Example**: `ip dhcp excluded-address 192.168.1.1 192.168.1.20`

### 7. **DHCP Relay**:
   - If the DHCP server is not on the same subnet as the client, a **DHCP Relay Agent** (usually a router) is required to forward DHCP requests.

### 8. **DHCP Troubleshooting**:
   - Check if the DHCP server is reachable and correctly configured.
   - Verify that the IP pool has available addresses.
   - Use `show ip dhcp binding` (Cisco) to see the assigned IP addresses.
   - Use `ping` and `ipconfig` to troubleshoot client connections.

### 9. **DHCP Benefits**:
   - Simplifies IP address management.
   - Reduces manual errors in IP address assignment.
   - Centralizes network configuration management.

These points cover the basic steps and configurations involved in setting up DHCP on a network.
