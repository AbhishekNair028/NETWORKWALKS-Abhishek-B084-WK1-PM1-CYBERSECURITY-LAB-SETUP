# NETWORKWALKS-Abhishek-Sajeev-Nair-WK1-PM1-CYBERSECURITY-LAB-SETUP

# Cybersecurity Lab Setup Using VirtualBox and Kali Linux

**Author:** Abhishek Sajeev Nair  
**Program:** NETWORKWALKS Cybersecurity Internship  
**Week:** 1 (WK1-PM1)  
**Project:** Cybersecurity Lab Environment Setup

---

## 1. Project Overview

As part of the first week of my cybersecurity internship at NETWORKWALKS, I worked on building a virtual cybersecurity lab using Oracle VirtualBox and Kali Linux.

The purpose of this setup was to create a virtual environment where I could understand networking, configure virtual machines, and prepare for future authorized penetration-testing activities.

The Kali Linux virtual machine runs on a Windows host system and is connected through a custom NAT Network named `NATNetwork`.

This documentation covers the tools used, configuration process, network setup, testing, and important things learned during the project.

## 2. Project Task Checklist

| Task | Status | Evidence |
|---|---|---|
| Install VirtualBox | Completed | Screenshots 01, 02 |
| Download and configure Kali Linux | Completed | Screenshots 03, 04 |
| Create NAT Network | Completed | Screenshot 05 |
| Connect Kali Linux to NATNetwork | Completed | Screenshots 06, 07 |
| Verify internet connectivity | Completed | Screenshot 09 |
| Configure Kali IP as 10.0.0.2/24 | Pending verification | Section 7 |
| Enable clipboard and drag-and-drop | Pending verification | — |
| Configure shared folder | Pending verification | — |
| Create a clean VM snapshot | Pending verification | — |

## 3. Tools and Technologies

| Tool | Description |
|---|---|
| 7-Zip | Used to extract the Kali Linux archive |
| VirtualBox 7.2.22 | Virtual machine management |
| Kali Linux 2026.3 | Linux-based cybersecurity environment |
| Windows PowerShell | Network configuration and commands |
| VBoxManage | VirtualBox command-line utility |
| NetworkManager | Linux network configuration |
| Firefox | Internet connectivity testing |

## 4. Preparing the Kali Linux Virtual Machine

I started by downloading the Kali Linux VirtualBox image and installing 7-Zip to extract the compressed archive.

After extraction, the folder contained the virtual machine configuration file (`.vbox`) and virtual disk file (`.vdi`).

The configuration file contains the VM settings, while the virtual disk stores the operating system and its data.

**Screenshot 01 – Extracted Kali Linux Files**

<img width="782" height="77" alt="vm1main" src="https://github.com/user-attachments/assets/578d5360-5446-44e7-8094-2f6430858df4" />

**Screenshot 02 – Kali Linux Virtual Machine Files**

<img width="906" height="146" alt="vm1" src="https://github.com/user-attachments/assets/839d877a-9ded-4b92-854d-81a5c42ea2e7" />

## 5. VirtualBox Installation and VM Import

After preparing the Kali Linux files, I installed Oracle VirtualBox version 7.2.22.

I imported the virtual machine into VirtualBox using the extracted `.vbox` configuration file.

The VM was configured with the following resources:

- Base Memory: 2048 MB
- Processors: 2
- Virtual Disk: Approximately 80 GB
- Operating System Type: Debian (64-bit)

**Screenshot 03 – Virtual Machine Configuration**

<img width="882" height="155" alt="vm5" src="https://github.com/user-attachments/assets/0a80b1d2-bc24-42ee-a575-5c837cfe387a" />

## 6. Creating the NAT Network

The next step was configuring a dedicated network for the cybersecurity lab.

I accessed the network management section through:

`VirtualBox → File → Tools → Network`

The NAT Network was configured with these settings:

| Network Parameter | Value |
|---|---|
| Network Name | NATNetwork |
| IPv4 Address Range | 10.0.0.0/24 |
| DHCP Server | Enabled |
| IPv6 | Disabled |

A NAT Network allows multiple virtual machines to communicate through a shared virtual subnet while providing external network connectivity.

**Screenshot 04 – VirtualBox Network Manager**

<img width="1917" height="1020" alt="vm2" src="https://github.com/user-attachments/assets/db39254c-b9aa-41b6-9555-746574f0d6d7" />

**Screenshot 05 – NAT Network Configuration**

<img width="1917" height="1012" alt="vm3" src="https://github.com/user-attachments/assets/f579a00c-89ba-4638-bf62-8a6aa7673136" />

## 7. Configuring the Kali Linux Network Adapter

Once the NAT Network was created, I opened the Kali virtual machine settings and navigated to:

`Settings → Network → Adapter 1`

The adapter was configured using the following options:

| Setting | Configuration |
|---|---|
| Network Adapter | Enabled |
| Attached To | NAT Network |
| Network Name | NATNetwork |
| Adapter Type | Intel PRO/1000 MT Desktop |
| Promiscuous Mode | Allow All |
| Cable Connected | Enabled |

This connected the Kali Linux virtual machine to the previously created virtual network.

**Screenshot 06 – Kali Linux Network Adapter Settings**

<img width="1917" height="865" alt="vm4" src="https://github.com/user-attachments/assets/74c415ea-8309-4d78-a70d-beb608c91f2c" />

## 8. Checking Network Configuration in Kali Linux

After connecting the adapter, I started Kali Linux and inspected its wired network connection.

I used the following command to open the network connection editor:

```bash
nm-connection-editor
```

The connection editor displayed the wired network interface as `eth0`.

This helped me inspect the network configuration inside the Linux environment.

**Screenshot 07 – Kali Linux Network Connection Editor**

<img width="1917" height="827" alt="vm6" src="https://github.com/user-attachments/assets/d8f75f91-59e9-4d19-a842-3618a0d08219" />

## 9. Testing Internet Connectivity

To verify that the network configuration was working, I opened Firefox inside Kali Linux and accessed Google.

The website loaded successfully, confirming that the virtual machine had internet access.

I also explored basic network connectivity and DNS resolution as part of the setup process.

**Screenshot 09 – Internet Connectivity Test**

<img width="1917" height="950" alt="vm8" src="https://github.com/user-attachments/assets/f93eea38-2fd5-4dce-9072-cafd762a7b5b" />

## 10. Challenges and Troubleshooting

During the setup process, several configuration-related issues were encountered.

| No. | Issue | Resolution |
|---|---|---|
| 1 | Virtual machine showed an Inaccessible status. | Removed the broken VM entry and imported it again from the extracted folder. |
| 2 | VirtualBox installation stopped unexpectedly. | Restarted the system and ran the installer again. |
| 3 | Network configuration option was difficult to locate. | Used the VirtualBox network management tools and VBoxManage. |
| 4 | PowerShell did not recognize VBoxManage. | Executed the utility from the VirtualBox installation directory. |
| 5 | VM settings could not be modified because the machine was locked. | Shut down the running virtual machine before making changes. |
| 6 | An incorrectly configured virtual network caused removal errors. | Updated the VM adapter configuration before removing the old network. |
| 7 | Wired network settings were difficult to locate in Kali Linux. | Opened NetworkManager using the terminal. |
| 8 | High RAM usage affected VM performance. | Closed unnecessary applications before launching the virtual machine. |

## 11. Important Concepts Learned

Through this project, I developed a better understanding of the following concepts:

**1. Virtualization**

Virtualization allows multiple operating systems to run on a single physical computer.

**2. NAT vs NAT Network**

NAT provides network access to an individual virtual machine, whereas NAT Network allows multiple VMs to communicate through a shared network.

**3. IP Addressing**

IP addresses help identify devices and enable communication across networks.

**4. Network Configuration**

Virtual network adapters connect virtual machines to different network environments.

**5. Virtual Machine Snapshots**

Snapshots help preserve VM states and make recovery easier during experiments.

**6. Troubleshooting**

Understanding error messages and checking configurations helps identify technical problems.

## 12. Conclusion

Completing this project provided me with practical exposure to setting up a cybersecurity lab environment.

I gained hands-on experience with Kali Linux, VirtualBox, virtual networking, and basic connectivity testing.

This setup serves as the foundation for the next stages of my cybersecurity internship, where I look forward to learning more about reconnaissance, network scanning, and vulnerability assessment.

---

## Project Information

| Field | Details |
|---|---|
| Project | Cybersecurity Lab Environment Setup |
| Organization | NETWORKWALKS |
| Internship | Week 1 |
| Project Code | WK1-PM1 |
| Author | Abhishek Sajeev Nair |
| Virtualization Software | Oracle VirtualBox 7.2.22 |
| Operating System | Kali Linux 2026.3 |
| Archive Utility | 7-Zip |

**GitHub Repository:** Add your repository URL here.

**Internship:** NETWORKWALKS Cybersecurity Internship
