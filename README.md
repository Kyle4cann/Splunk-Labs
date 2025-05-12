# Securing-Infrastructure-LAB1
### NAME: VINCENT CANN.
### STUDENT ID: 4381913
### COURSE: CYBS 1007 SECURING INFRASTRUCTURE.


## Lab 1 Part 1: Create AWS account. 

### 1. Configure DNS Agent to use DNS Over HTTP on your Windows VM.
- open https://aws.amazon.com/console/ in your browser
- click on AWS management console
- click on Create a new AWS Account
- Fill in: Root user email address and AWS account name the click of verify email address
- Open your mail to verify account


![image](https://github.com/user-attachments/assets/a458f12c-d091-4340-af1c-6dd447958907) 
Screenshot for Windows

### 2. Configure DNS Agent to use DNS Over HTTP on your Linux VM.
![image](https://github.com/user-attachments/assets/e32c4c72-a023-4996-b5b5-59ec2ca00306)
Screenshot for Linux

### 3. Install DNS Server on your Windows VM, config it to use DNSSEC and connect to Google DNS Server. Obtain results from nslookup.
![image](https://github.com/user-attachments/assets/df06dd68-acac-4a36-8bcd-b5adc75e318b)
![image](https://github.com/user-attachments/assets/b062a35e-07c2-4368-bf10-486ccc292dca)  
Screenshot nslookup for Windows  

### 4.  Install DNS Server on your LINUX VMs, config it to use DNSSEC and connect to Google DNS Server. Obtain results from nsLookup.
![image](https://github.com/user-attachments/assets/c10f018f-244b-401f-97be-c480184140df)
Screenshot nslookup for Linux

### 5. Install DHCP on your Windows VM. 
![image](https://github.com/user-attachments/assets/5f02f9ae-f70a-4465-98e4-839862b98f22)
Screenshot of the Windows DHCP configuration file.

### 6. Install DHCP on your Linux VM.
![image](https://github.com/user-attachments/assets/26cabb3d-5594-47bf-b38d-97c9e4307ece)
Configure the DHCP Server
 
Add the following lines to the dhcpd.conf file. Replace 192.168.1.0 with your VMs network address, and 192.168.1.10 192.168.1.50 with your desired IP address range:
  subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.10 192.168.1.50;
  option domain-name-servers ns1.example.org, ns2.example.org;
  option domain-name "example.org";
 		 option routers 192.168.1.1;
 		 option broadcast-address 192.168.1.255;
 		 default-lease-time 600;
 		 max-lease-time 7200;
}

Save and close the file.
Restart the DHCP Server
Verify the DHCP Server
### Question: What devices/endpoints must have a static IP Address? 
### ANSWER: 
Some network devices and endpoints should always have a static IP address to ensure stability and reliability. These include:
### 1.	Network Infrastructure Devices
-	Routers & Gateways" They manage network traffic, so changing their IP could disrupt connectivity.
-	Switches (Managed): If they support remote management, they need a fixed IP for configuration access.
-	Firewalls: To ensure proper security enforcement and rule application.
### 2.	Servers
-	DNS Servers: A static IP prevents network-wide DNS resolution failures.
-	DHCP Servers: If DHCP had a dynamic IP, clients wouldn’t always find it.
-	Web Servers: Hosting websites requires a consistent address for domain resolution.
-	File & Database Servers: Clients need a stable connection to access resources.
-	Mail Servers: Ensures mail delivery without disruptions.
-	Active Directory Domain Controllers: Essential for network authentication.
### 3.	Networked Devices
-	Printers: Ensures that users can always find and print to them.
-	CCTV Cameras: For stable monitoring and remote access.
-	VoIP Phones: To avoid call interruptions or dropped connections.
### 4.	Special Use Devices
-	VPN Servers: Provides remote access without frequent configuration changes.
-	IoT Devices (Smart Security Systems, Automation Controllers, etc.): Ensures seamless operation.
  
### Question: How would you assign these static IP hosts in the dhcp.conf file?
![image](https://github.com/user-attachments/assets/1570bd1f-8a41-407a-a92e-078666a23383)
Screenshot of the Linux DHCP configuration file and that the DHCP server is running.

## Lab1  Part 2: System Hardening
### 1.   Watch the youtube videos in slide deck for installing a PXE server on Windows and Linux.
Question(s): What is the main benefit of PXE?
PXE Explained: PreBoot Execution Environment, how to deploy an operating system. – YouTube
PXE WDS windows server 2019 - YouTube
### ANSWER: 
PXE (Preboot Execution Environment) allows computers to boot from a network without needing local storage (hard drive, USB, or CD/DVD).
### The main Benefits:
-	Automated OS Deployment: Quickly install operating systems on multiple machines over the network.
-	No Need for Boot Media: Eliminates the need for USBs or DVDs to install OS.
-	Centralized Management: IT teams can manage and update systems remotely.
-	Faster System Recovery: Easily reinstall or repair OS in case of system failure.
### Scalability 
- Ideal for setting up large numbers of computers (e.g., in enterprises, schools, or data centers).

### 2. Install and configure Microsoft Windows Deployment Services from the Server Manager on Windows. Configure MDS as a standalone server with not installing images at this time.
 ![image](https://github.com/user-attachments/assets/916d5f0f-9830-456c-aa6d-b59e62e1342f)
![image](https://github.com/user-attachments/assets/e0e79fbf-6269-472f-88c0-b5243750c6a9)
Take a screenshot of the Install Images folder from within WDS

### Question(s): What should go in here?
### ANSWER: 
The Install Images folder in Windows Deployment Services (WDS) stores the operating system installation files used for deploying Windows to client computers via PXE boot.
What Goes in the Install Images Folder?
-	Windows Installation Images (.WIM files): These files, typically extracted from a Windows ISO (sources\install.wim), contain the operating system setup.
-	Custom Captured Images: If deploying a pre-configured system, custom .WIM images captured from existing installations can be added.
-	Multiple OS Versions: The folder can store various Windows versions (e.g., Windows 10, Windows 11, Windows Server 2022) to support different deployment needs.

### 3.   Download and view both a Windows and Linux benchmark from CIS.  
The CIS link is in the slide deck (Benchmarks). You will have to register with an email address.
Review the contents and provide an example network setting safeguard from CIS Control 13

### Question(s): Should you use them? Which Level are you comfortable using?
The safeguard in your screenshot is related to encrypting sensitive data at rest (CIS Control 3.11) and encrypting or hashing all authentication credentials (CIS Control 16.4).
An example network setting safeguard from CIS Control 13 is:
### ANSWER:
Ensure 'Prohibit use of Internet Connection Sharing on your DNS domain network' is set to 'Enabled'
-	Profile Applicability: Level 1 - Domain Controller, Level 1 - Member Server
-	Description: This setting prevents unauthorized users from turning on Internet Connection Sharing (ICS), which could expose internal network resources to external devices.
-	Rationale: Preventing ICS ensures that end-users cannot unintentionally or maliciously share their internet connection, reducing attack vectors.
-	Remediation: Configure the following Group Policy setting:
-	Computer Configuration\Policies\Administrative Templates\Network\Network Connections\Prohibit use of Internet Connection Sharing on your DNS domain network
-	Recommended Value: Enabled.
Should you use CIS Benchmarks?
### ANSWER: 
Yes, you should use them, as they provide industry-recognized security best practices that help reduce vulnerabilities and enhance network security.
Which Level should you use?
### ANSWER:
-	Level 1: Basic security that balances usability and security. Suitable for general enterprise environments.
-	Level 2: More restrictive settings for high-security environments.
If you prioritize security over usability and are working in a highly sensitive environment, Level 2 is preferable. Otherwise, Level 1 is a good baseline.

![image](https://github.com/user-attachments/assets/90f0b690-19ee-4035-9bd9-23a3dd4ffac2)
Linux Safeguard Screenshot:  

### Safeguard: Implement Network-Based Intrusion Detection Systems (NIDS)
### Description: 
Deploy a network-based intrusion detection system (NIDS) to monitor network traffic for malicious activity.
### Rationale: 
Helps detect unauthorized access, malware, and unusual network behaviors before they cause harm.
### Implementation: 
Use tools like Snort, Suricata, or Zeek to analyze network traffic.

![image](https://github.com/user-attachments/assets/6063e93a-9a9c-4667-88c4-0eba345a7eb7)
Windows Safeguard Screenshot:

### 4.   Download the DOD STIG for Windows 2022 Server
Goto DOD STIP website in the slide deck. Security Technical Implementation Guides (STIGs) – DoD Cyber Exchange
Look for:   DoD WinSvr 2022 MS and DC v1r4/Reports/
Look for and open the report: DoD WinSvr 2022 MS STIG Comp v1r4.html
Open Account Policies/Password Policies
### What is the minimum password length?
### ANSWER: 
14 characters minimum. 
![image](https://github.com/user-attachments/assets/daf47e41-dde0-4e66-8dd5-885ff8cb0932)
Take screenshot of the STIG

### Question(s): Would you use these STIGs? Why & Why not?
### ANSWER: 
Yes, I would use DoD STIGs (Security Technical Implementation Guides) because they establish stringent security configurations that enhance system protection, ensure compliance with frameworks like NIST and CIS, and reduce cyber risks through strong password policies, access controls, and network security measures. They are especially valuable in high-security environments such as government and enterprise systems. However, STIGs can be complex to implement, overly restrictive, and may affect usability, making them less suitable for smaller organizations or general-purpose systems. While they are crucial for securing critical infrastructure, a more balanced approach—such as CIS Level 1 Benchmarks—might be better suited for environments that need to balance security with usability.
