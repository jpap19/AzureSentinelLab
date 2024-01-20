
<h1>Configure SIEM security operations using Microsoft Sentinel </h1>

<h2>Description</h2>
In this Lab, we setup Azure Sentinel (SIEM) and connect it to a live virtual machine acting as a honey pot. We will observe live attacks (RDP Brute Force) from all around the world. We will use a custom PowerShell script to look up the attackers Geolocation information and plot it on the Azure Sentinel Map!
<br />

<h2>Resources And Links To Required Tools:</h2>

- <b>PowerShell Script for the Lab</b>   (https://github.com/joshmadakor1/Sentinel-Lab/blob/main/Custom_Security_Log_Exporter.ps1)
- <b>Azure Trial</b>    (https://azure.microsoft.com/en-us/free/)
- <b>Sentinel Map Query</b> : FAILED_RDP_WITH_GEO_CL | summarize event_count=count() by sourcehost_CF, latitude_CF, longitude_CF, country_CF, label_CF, destinationhost_CF
| where destinationhost_CF != "samplehost"
| where sourcehost_CF != ""


<h2>Program walk-through:</h2>

This is the high level overview of what we are going to setup in this Lab:

<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/VmwareInstalled.png" height="100%" width="100%" alt="Azure Sentinel SIEM Home Lab"/>
<br />
<br />
<p align="center">
 
The implementation will be in done in 4 Steps:

STEP 1: Create and configure a Microsoft Sentinel workspace.

STEP 2: Deploy a Microsoft Sentinel content hub solution.

STEP 3: Configure analytics rules in Microsoft Sentinel.

STEP 4: Configure automation in Microsoft Sentinel.

<br />

STEP 1: Create and configure a Microsoft Sentinel workspace:
Use the link above to create a subscription, then in portal.azure.com, create a Virtual Machine (VM), make it very vulnerable by disabling all firewall. 
This will characterize the vm as a honeypot (resource intentionally set to be very less secure, serve as a bait in order to trap attackers and detect them)
 
1.1 Azure Virtual Machine created: <br/>

<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/VmwareInstalled.png" height="100%" width="100%" alt="Azure Sentinel SIEM Home Lab"/>
<br />
<br />

1.2 RDP connection to the Virtual Machine from our local computer: <br/>

Copy the public IP address of the VM, open start menu from our local computer and rdp into the VM using credentials set up during VM creation in azure portal.

<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/VmwareInstalled.png" height="100%" width="100%" alt="Azure Sentinel SIEM Home Lab"/>
<br />
<br />

1.3  Set up a Honeypot Virtual Machine and run PowerShell Script: <br/>
Disabling Firewall on Azure VM to make it to accept ping, thus vulnerable.



<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
