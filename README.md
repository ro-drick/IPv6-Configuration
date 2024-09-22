# Packet Tracer Lab: IPv4/IPv6 Dual-Stack Network

## Lab Overview
This lab demonstrates the configuration of an **IPv4/IPv6 dual-stack network**, where devices are configured with both IPv4 and IPv6 addresses. The lab ensures full connectivity across the network for both protocols by enabling IPv6 routing, assigning IPv6 addresses to routers and PCs, and verifying connectivity with ping tests.

<img src= "https://github.com/ro-drick/IPv6-Configuration/blob/main/ipv6.PNG">

### Topology Details:
- **Router:** Cisco 2911 (R1)
- **Switches:** 3 x Cisco 2960-24TT (SW1, SW2, SW3)
- **PCs:** PC1, PC2, PC3
- **IPv4 Subnets:**
  - **192.168.1.0/24** (PC1)
  - **192.168.2.0/24** (PC2)
  - **192.168.3.0/24** (PC3)
- **IPv6 Subnets:**
  - **2001:DB8:0:1::/64** (PC1)
  - **2001:DB8:0:2::/64** (PC2)
  - **2001:DB8:0:3::/64** (PC3)

## Objectives

1. **Enable IPv6 Routing on R1**
   - Ensure IPv6 routing is enabled to support the dual-stack configuration.
   
   ```bash
   R1(config)# ipv6 unicast-routing
   ```

2. **Configure IPv6 Addresses on R1**
   - Assign IPv6 addresses to the router interfaces **G0/0** and **G0/1** for communication with the PCs.
   
   **R1 Configuration**:
   ```bash
   R1(config)# interface g0/0
   R1(config-if)# ipv6 address 2001:DB8:0:1::1/64
   R1(config-if)# no shutdown

   R1(config)# interface g0/1
   R1(config-if)# ipv6 address 2001:DB8:0:2::1/64
   R1(config-if)# no shutdown

   R1(config)# interface g0/2
   R1(config-if)# ipv6 address 2001:DB8:0:3::1/64
   R1(config-if)# no shutdown
   ```

3. **Confirm Configurations**
   - Verify the IPv6 configurations on each interface using the command:
   
   ```bash
   R1# show ipv6 interface brief
   ```
   - Expected Output: Each router interface should have its respective IPv6 address configured.

4. **Configure IPv6 Addresses on PCs**
   - Assign the correct IPv6 address and default gateway to each PC.

   **PC1 (IPv6 Config):**
   - **IPv6 Address:** `2001:DB8:0:1::2/64`
   - **Gateway:** `2001:DB8:0:1::1`

   **PC2 (IPv6 Config):**
   - **IPv6 Address:** `2001:DB8:0:2::2/64`
   - **Gateway:** `2001:DB8:0:2::1`

   **PC3 (IPv6 Config):**
   - **IPv6 Address:** `2001:DB8:0:3::2/64`
   - **Gateway:** `2001:DB8:0:3::1`

   On each PC, configure the IPv6 address under the IP Configuration tab.

5. **Verify Connectivity Between PCs**
   - Test both **IPv4 and IPv6** connectivity by pinging between PC1, PC2, and PC3:
     - **IPv4 Ping:**
       ```bash
       PC1> ping 192.168.2.2
       PC1> ping 192.168.3.2
       ```
     - **IPv6 Ping:**
       ```bash
       PC1> ping 2001:DB8:0:2::2
       PC1> ping 2001:DB8:0:3::2
       ```

## Key Findings

- **IPv6 Routing on R1:** Properly enabled and configured, allowing R1 to route IPv6 packets between subnets.
- **Dual-Stack Functionality:** Both **IPv4** and **IPv6** addresses are fully operational across the network, demonstrating the ability of dual-stack configurations to support both protocols simultaneously.
- **Ping Results:** Successful pings confirm connectivity for both **IPv4** and **IPv6**, verifying that the PCs can communicate over both networks.

## Commands Used

### Enable IPv6 Routing on R1:
```bash
R1(config)# ipv6 unicast-routing
```

### IPv6 Address Configuration on R1:
```bash
R1(config)# interface g0/0
R1(config-if)# ipv6 address 2001:DB8:0:1::1/64
R1(config-if)# no shutdown
```
## Conclusion

This lab successfully demonstrated the configuration of an **IPv4/IPv6 dual-stack network**, allowing devices to communicate using both protocols. By enabling IPv6 routing on **R1** and assigning appropriate IPv6 addresses to both the router interfaces and PCs, we ensured full IPv6 connectivity alongside the existing IPv4 configuration. Testing connectivity between PCs confirmed that both **IPv4** and **IPv6** addresses were operational and able to route packets correctly.

The dual-stack approach showcased in this lab is crucial for transitioning networks from IPv4 to IPv6, ensuring backward compatibility while supporting newer IPv6-enabled devices and networks. This configuration highlights the importance of modernizing network infrastructure to accommodate the growing demand for IPv6 addresses without disrupting existing IPv4 operations.

## Acknowledgements


Special thanks to **Jeremy's IT Lab** for providing valuable resources and tutorials that greatly contributed to the completion of this exercise. His in-depth explanations and practical demonstrations have been instrumental in enhancing my understanding of Cisco networking concepts and the effective use of Packet Tracer.

For more information and additional resources, visit [Jeremy's IT Lab](https://jeremysitlab.com/) and check out his YouTube for the full course, [Jeremy's IT Lab Free CCNA 200-301 | Complete Course](https://www.youtube.com/playlist?list=PLxbwE86jKRgMpuZuLBivzlM8s2Dk5lXBQ)
