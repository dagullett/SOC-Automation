# SOC Automation set-up using Wazuh, TheHive, and Shuffle
![SOCLabDiagram1](https://github.com/dagullett/SOC-Automation/assets/75142644/88ed7ae6-e730-4c7f-94e7-aabc1e1aa4b1)

## Introduction

In this project I created a fully functional SOC environment that monitors users being infected with malware and sends alerts to the SOC analyst through theHive. It also sends an automated email message to the Analyst in the event the Analyst is not actively monitoring the event. In this lab we:

- Set up 3 virtual machines using Virtual Box and Digital Ocean cloud service
- Added the virtual machines to firewalls to protect them from IP scanning
- Infected a machine with Mimikatz malware to create alerts
- Configured Shuffle with Virus Total
- Used Shuffle to send alerts to theHive and send Emails

## Setting Up Virtual Machines

- Virtual Box Machine

![Screenshot 2024-01-31 172116](https://github.com/dagullett/SOC-Automation/assets/75142644/5d1bb223-782b-4085-a88f-0b2163fb69ca)

- Digital Ocean Wazuh Virtual Machine

![Screenshot 2024-01-31 172358](https://github.com/dagullett/SOC-Automation/assets/75142644/53166205-757f-4a35-b15e-04dffb19c45f)

- Digital Ocean theHive Virtual Machine

![Screenshot 2024-01-31 172436](https://github.com/dagullett/SOC-Automation/assets/75142644/5c9f927c-3059-411b-9ffd-b0db3b280ec5)

The first step was setting up the virtual machines. I downloaded virtual box to my computer and allocated enough resources to run the lab. This machine used Windows 10 Professional. I then created 2 virtual machines on Digital Oceans cloud service. Both of these machines were set up with Linux uBuntu. I used the virtual box as a working virtual desktop, while I only accessed the uBuntu VMs through the terminal.

## Set Up a Firewall to Prevent IP Scans on the VMs.


![Screenshot 2024-01-31 173356](https://github.com/dagullett/SOC-Automation/assets/75142644/1531bd69-61e9-4694-a9bf-c8bfc3234f99)

I created a firewall that only allowed access from my home computer. This allowed me to access both virtual machines through the terminal with ssh. This is also how I installed the necessary software on each of my cloud virtual machines. After all the virtual machines were created and protected, I had to download and configure the software on each machine. The windows machine would have Sysmon and the Wazuh agent installed onto it. One uBuntu machine would have Wazuh dashboard installed while the other uBuntu machine would have theHive installed. I used this repository to configure Sysmon.

https://github.com/olafhartong/sysmon-modular/blob/master/sysmonconfig.xml
