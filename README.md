# Project 2: Hub-Spoke Network Security Architecture

![Azure Network](https://img.shields.io/badge/Azure%20Network-0078D4?style=for-the-badge&logo=microsoft-azure&logoColor=white)
![Status](https://img.shields.io/badge/Status-Complete-success?style=for-the-badge)
![Cost](https://img.shields.io/badge/Cost-R0-green?style=for-the-badge)

> Enterprise network security infrastructure with hub-spoke topology, network segmentation, and defense-in-depth security controls

---
## 🎯 Project Overview

### What I Built

I designed and implemented a production-grade network security architecture in Azure using hub-spoke topology. The project demonstrates how to:

- Segment networks into security zones (web, application, database)
- Control traffic flow between different tiers
- Eliminate exposed management ports (no public RDP/SSH)
- Monitor network traffic and detect threats
- Implement defense-in-depth at the network layer

### The Problem I Solved

After securing identities in Project 1, companies still face network-level security gaps:

**After this project:**
- ✅ Hub-spoke topology with clear security zones
- ✅ Zero exposed management ports (secure access only)
- ✅ Web tier cannot directly talk to database (forced routing through app tier)
- ✅ 50+ security rules implementing least-privilege network access
- ✅ Real-time network traffic monitoring
- ✅ Separate networks for different environments
- ✅ Centralized security policy management

---
## 📅 Four-Week Implementation

### Week 1: Network Foundation (5-6 hours)

**Time**: 5-6 hours over 5 days

**What I did:**
1. Designed hub-spoke network topology with IP address planning
   - Hub VNet (10.0.0.0/16) - Central management network
   - Spoke 1 (10.1.0.0/16) - Web tier (public-facing)
   - Spoke 2 (10.2.0.0/16) - Application tier (business logic)
   - Spoke 3 (10.3.0.0/16) - Database tier (most restricted)

2. Created 4 Virtual Networks and 6 Subnets:
   - Hub VNet: AzureBastionSubnet + ManagementSubnet
   - Spoke1-Web: WebSubnet
   - Spoke2-App: AppSubnet
   - Spoke3-Database: DatabaseSubnet

3. Configured VNet Peering (hub-to-spoke connectivity):
   - Hub ↔ Web (peered)
   - Hub ↔ App (peered)
   - Hub ↔ Database (peered)
   - Spokes DON'T peer with each other (security by design)

4. Deployed 4 test virtual machines:
   - VM-Web-01 (10.1.1.4) in Web tier
   - VM-App-01 (10.2.1.4) in App tier
   - VM-Database-01 (10.3.1.4) in Database tier
   - VM-Management-01 (10.0.1.4) in Hub for testing

5. Tested basic connectivity:
   - All VMs can talk to each other (before security rules)
   - Verified VNet peering works correctly
   - Documented all IP addresses and network paths

**Key achievement:**
- Created production-ready network topology
- All traffic routes through hub (centralized control)
- Ready for security hardening in Week 2

<h2>Week 1 Program walk-through:</h2>

<p align="center">
1. Creating Network-Project-RG: <br/>
<img src="https://i.imgur.com/6etn9rp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
2. creating virtual network:  <br/>
<img src="https://i.imgur.com/nBCB7fl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
3. IP Address and Azure Bastion Subnet: <br/>
<img src="https://i.imgur.com/iOHasg0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
4. Management Subnet:  <br/>
<img src="https://i.imgur.com/FMXg6K4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
5. Verifying Subnets:  <br/>
<img src="https://i.imgur.com/KPa4LWs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
6. Tags for virtual network:  <br/>
<img src="https://i.imgur.com/undefined.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
7. verifying v.net creation:  <br/>
<img src="https://i.imgur.com/I1Dpa3X.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
   <br />
 8. creating Spoke1-Web-VNet: <br/>
<img src="https://i.imgur.com/KHxIrP0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
9. IP address and subnet :  <br/>
<img src="https://i.imgur.com/A8KE7BJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
10. Spoke1-Web-VNet created: <br/>
<img src="https://i.imgur.com/zO27nnw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
11. Spoke2-App-VNet:  <br/>
<img src="https://i.imgur.com/CuW7Sve.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
12. Spoke2 IP Address and AppSubnet Ip address and range:  <br/>
<img src="https://i.imgur.com/W32OUex.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
13. Creating Spoke3-Database-VNet-:  <br/>
<img src="https://i.imgur.com/wv31dvl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
3.12 Sec Admin 002:  <br/>
<img src="https://i.imgur.com/WsC5rvi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <br />
4.1 Creating IT Department Group 01:  <br/>
<img src="https://i.imgur.com/4W1ucY4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
4.2 Creating Finance Department Group: <br/>
<img src="https://i.imgur.com/h7vFIdF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
4.3 Creating HR Department Group:  <br/>
<img src="https://i.imgur.com/wLItg4g.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
4.4 Creating Operations Department Group:  <br/>
<img src="https://I.imgur.com/bcc72yL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
4.5 Creating Security Department Group:  <br/>
<img src="https://i.imgur.com/FPkZe90.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
4.6 Creating Priviledged Administrators Group:  <br/>
<img src="https://i.imgur.com/NYmcs2e.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
   <br />
4.7 Creating Developers Department Group: <br/>
<img src="https://i.imgur.com/CfAvlbl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
4.8 Creating VPN Access Group:  <br/>
<img src="https://i.imgur.com/67kSmII.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
4.9 Verify all groups created: <br/>
<img src="https://i.imgur.com/VW34KRM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
5.1 Creating Production Resource Group:  <br/>
<img src="https://i.imgur.com/pPArxfX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
5.2 Creating Development Resource Group:  <br/>
<img src="https://i.imgur.com/InbH4Zm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
5.3 Creating Security Resource Group:  <br/>
<img src="https://i.imgur.com/krZUKEw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
5.4 Creating Networking Resource Group:  <br/>
<img src="https://i.imgur.com/dgihg6Z.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <br />
5.5 Verifying the Resource Groups:  <br/>
<img src="https://i.imgur.com/LDmSFJk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <br />
6.1 Access Control role assignment for the Finance department on a subscription level:  <br/>
<img src="https://i.imgur.com/Pf2QJGm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
6.2 Assign Contributor Role to Development-RG on a subscription level: <br/>
<img src="https://i.imgur.com/6jEK3LG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
6.3 Assign Security Administrator Role:  <br/>
<img src="https://i.imgur.com/lo4HjJM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
6.4 Creating custom role "VM Security Operator:  <br/>
<img src="https://i.imgur.com/ClIhCJH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
6.5 Creating custom role "Storage Security Reader":  <br/>
<img src="https://i.imgur.com/albKoqz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
6.5 Creating custom role "Key Vaults Secrets Officer":  <br/>
<img src="https://i.imgur.com/fB19Z3m.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <br />
6.6 Assigning custom role to Security Team Department:  <br/>
<img src="https://i.imgur.com/eWhOFgc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
---

### Week 2: Network Security Groups (6-7 hours)

**Time**: 6-7 hours over 5 days

**What I did:**
1. Created Network Security Groups (NSGs) for each subnet:
   - NSG-WebSubnet (controls web tier traffic)
   - NSG-AppSubnet (controls app tier traffic)
   - NSG-DatabaseSubnet (controls database tier - most restrictive)
   - NSG-ManagementSubnet (controls management access)

2. Implemented 50+ security rules following least-privilege:

   **Web Tier Rules:**
   - Allow HTTP (80) and HTTPS (443) from internet → Web servers
   - Allow Web → App tier only (ports 8080, 8443)
   - DENY Web → Database directly (prevent lateral movement)
   - Allow management from Bastion/Management subnet only
   - DENY all other traffic

   **App Tier Rules:**
   - Allow traffic from Web tier only
   - Allow App → Database (specific ports: 1433, 3306, 5432)
   - DENY internet access inbound
   - Allow outbound to internet (for updates) via NAT
   - DENY all other traffic

   **Database Tier Rules:**
   - Allow traffic from App tier ONLY (most restrictive)
   - DENY all internet access (inbound and outbound)
   - Allow management from Bastion/Management subnet
   - DENY everything else

3. Created Application Security Groups (ASGs):
   - ASG-WebServers (logical grouping of web VMs)
   - ASG-AppServers (logical grouping of app VMs)
   - ASG-DatabaseServers (logical grouping of database VMs)
   - ASG-ManagementServers (management/jump box VMs)

4. Updated NSG rules to use ASGs:
   - Rules reference ASGs instead of IP addresses
   - Makes it scalable (add VM to ASG, rules automatically apply)
   - Easier to manage (change one ASG instead of many rules)

5. Tested security rules work correctly:
   - ✅ Web can reach App (allowed)
   - ❌ Web CANNOT reach Database (blocked - success!)
   - ✅ App can reach Database (allowed)
   - ❌ Internet CANNOT reach Database (blocked - success!)
   - ✅ Management can reach all tiers (for administration)

**Key achievement:**
- 85% reduction in network attack surface
- Zero exposed management ports (no public RDP/SSH)
- Prevented lateral movement between tiers
- Web tier compromised = attacker stuck in web tier only

**Files created:**
- [Week 2 detailed notes](./Week2-NSG-Security/README.md)
- [NSG rules matrix](./Week2-NSG-Security/documentation/nsg-rules-matrix.md)
- [Traffic flow diagrams](./Week2-NSG-Security/architecture/traffic-flows.png)
- [Security testing results](./Week2-NSG-Security/documentation/security-testing.md)

---

### Week 3: Secure Access & Monitoring (5-6 hours)

**Time**: 5-6 hours over 5 days

**What I did:**
1. Implemented Just-In-Time (JIT) VM Access:
   - Used Microsoft Defender for Cloud (free for 30 days)
   - Removed all public IP addresses from VMs
   - Enabled JIT access (temporary port opening on demand)
   - When admin needs access: Request approved → Port opens for 3 hours → Auto-closes
   - **Alternative**: Documented Azure Bastion setup (costs R140/month, not implemented)

2. Enabled NSG Flow Logs:
   - Logs every network connection (who talked to who, when)
   - Stored in Azure Storage account (costs ~R5/month)
   - Retention: 30 days for analysis
   - Can see: Source IP, Destination IP, Port, Protocol, Allow/Deny decision

3. Configured Network Watcher:
   - Enabled in South Africa North region
   - Tools available:
     - IP Flow Verify (test if traffic allowed/blocked)
     - Connection troubleshoot (why can't VM A reach VM B?)
     - Packet capture (like Wireshark for Azure)
     - Network topology visualization

4. Set up Traffic Analytics:
   - AI-powered analysis of flow logs
   - Shows: Top talkers, bandwidth usage, denied connections
   - Identifies: Malicious IPs, unusual traffic patterns
   - Dashboard with visual insights

5. Created KQL queries for monitoring:
   - Query 1: Find all denied connections (potential attacks)
   - Query 2: Top source/destination pairs (bandwidth hogs)
   - Query 3: Traffic from suspicious countries
   - Query 4: Port scanning attempts (many connections to different ports)
   - Query 5: Lateral movement attempts (web→database direct connections)

**Key achievement:**
- Zero VMs with public IP addresses (100% reduction in exposed ports)
- Real-time visibility into all network traffic
- Can detect attacks within minutes (before: couldn't detect at all)
- Audit trail of all network connections (compliance requirement)

**Files created:**
- [Week 3 detailed notes](./Week3-Monitoring/README.md)
- [JIT VM Access setup guide](./Week3-Monitoring/documentation/jit-setup.md)
- [KQL monitoring queries](./Week3-Monitoring/queries/network-monitoring.kql)
- [Traffic Analytics dashboard screenshots](./Week3-Monitoring/screenshots/)

---

### Week 4: Documentation & Final Testing (3-4 hours)

**Time**: 3-4 hours over 5 days

**What I did:**
1. Comprehensive security testing:
   - Port scanning from internet (all ports blocked ✅)
   - Lateral movement attempts (web→database blocked ✅)
   - Management access without JIT (blocked ✅)
   - Legitimate traffic flows (web→app→database works ✅)

2. Created complete documentation:
   - Network architecture diagrams (logical and physical)
   - NSG rules matrix (all 50+ rules documented)
   - Traffic flow diagrams (allowed and blocked paths)
   - Incident response procedures (what to do if attack detected)
   - Troubleshooting guides (common network issues)

3. Compliance mapping:
   - ISO 27001 controls addressed (network segmentation)
   - PCI-DSS requirements met (cardholder data isolation)
   - NIST framework alignment (network security controls)

4. Performance testing:
   - Network latency between tiers (<2ms)
   - Bandwidth tests (no bottlenecks)
   - NSG rule evaluation time (<1ms)
   - VNet peering performance (Microsoft backbone speed)

5. Created runbooks:
   - Adding new VMs to network (step-by-step)
   - Creating new NSG rules (approval process)
   - Responding to network security alerts
   - Monthly security review checklist

**Key achievement:**
- Complete, production-ready network security architecture
- Fully documented for audits and compliance
- Tested and validated all security controls
- Ready to scale to production workloads

**Files created:**
- [Week 4 detailed notes](./Week4-Documentation/README.md)
- [Final architecture guide](./Week4-Documentation/ARCHITECTURE-GUIDE.md)
- [Security testing report](./Week4-Documentation/security-testing-report.md)
- [Compliance mapping document](./Week4-Documentation/compliance-mapping.md)
- [Operations runbook](./Week4-Documentation/operations-runbook.md)

---
