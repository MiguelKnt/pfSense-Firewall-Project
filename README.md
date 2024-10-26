# pfSense Firewall Project for Home Lab Security

**Enhancing Network Security with pfSense in a Virtual Lab Environment**

---

## 📜 Overview
This project demonstrates the setup and configuration of a pfSense firewall VM alongside a Windows 10 VM in Oracle VirtualBox to secure and manage network traffic within a home lab environment. Key objectives include blocking website access using firewall rules and IP address management, while also implementing advanced network security techniques.

## ⚙️ Project Details
In this project, I used pfSense to:
1. Configure a firewall to control network traffic in a virtualized lab environment.
2. Set up firewall rules to block access to specific websites by domain and IP address.
3. Deepen understanding of network security practices, including the use of CIDR ranges for effective traffic blocking.

### Features
- **pfSense as Gateway**: Configured as the primary firewall and gateway for the Windows VM within the lab.
- **Domain Blocking**: Restricted access to specific websites using aliases for centralized rule management.
- **IP Blocking**: Explored blocking by individual IP and CIDR range for comprehensive network control.
- **DNS Query Testing**: Used `nslookup` to identify and confirm IP addresses associated with specific domains.

## 🛠️ Setup Environment
### Tools and Software
- **Oracle VirtualBox**: Virtualization platform used to create and manage VMs.
- **pfSense Firewall**: Configured as a firewall VM to monitor and control network traffic.
- **Windows 10 VM**: Set up using the Windows Media Creation Tool to create a testing environment.

### Network Configuration
1. **WAN Interface**: Configured with a bridged network adapter to connect directly to the physical network.
2. **LAN Interface**: Set up with a NAT network for internal connectivity, allowing the Windows VM to route traffic through pfSense.
3. **Gateway**: Set pfSense LAN IP as the default gateway for the Windows VM, ensuring that all traffic passes through the firewall.

## 🔧 Configuration and Firewall Rules
### Domain Blocking via Alias
1. Created an alias named **Blocked_Sites** to simplify rule management and enforce consistent blocking policies.
2. Configured a firewall rule to block traffic to the site **videocopilot.net**, positioning the rule at the top of the list to ensure it remains prioritized.
3. Verified the rule's effectiveness by attempting to access the site and confirming it was inaccessible.

### IP Blocking Using CIDR Range
1. Used `nslookup` to query the IP address associated with **videocopilot.net**, retrieving **52.9.112.83**.
2. Attempted to block the specific IP but found it ineffective due to CDN or load balancing.
3. Revised the strategy to block the CIDR range **52.9.112.83/24**, successfully restricting access to the site.
    - **Pros of CIDR Blocking**: Provides more comprehensive restriction by covering multiple IPs.
    - **Cons of CIDR Blocking**: May inadvertently block legitimate traffic within the range.

### Testing and Verification
- **Domain Blocking**: Confirmed that **videocopilot.net** was inaccessible by testing access through the browser, with results showing successful blocking.
- **IP and CIDR Blocking**: Validated the firewall's ability to block based on IP range after initial single IP blocking was ineffective.
- **DNS Lookup with `nslookup`**: Used to verify IP addresses and analyze the need for a broader CIDR range.

## 🧪 Insights and Learnings
- **Effective Rule Management with Aliases**: Using aliases for domain blocking streamlined rule management, making it easy to update and maintain restrictions as network security needs evolve.
- **Challenges with IP-Based Blocking**: Blocking by a single IP address can be limited, especially when sites use content delivery networks (CDNs) or load balancers. Expanding the block to a CIDR range provided a more comprehensive solution, though it requires careful planning to avoid affecting unrelated services.
- **Network Traffic Analysis**: Reviewing pfSense logs was essential for understanding how traffic patterns influence firewall rules, helping to diagnose why certain blocks were bypassed and guiding adjustments for improved network control.
- **Hands-on Firewall Configuration**: This project reinforced practical knowledge of firewall management, offering valuable experience with real-world techniques for securing a network in a virtualized environment.
