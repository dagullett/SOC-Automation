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

## Installed Wazuh, Wazuh Agent, and theHive

![Screenshot 2024-01-31 181739](https://github.com/dagullett/SOC-Automation/assets/75142644/6eb7197b-ca87-4d15-acc7-328392f096be)

![Screenshot 2024-01-31 180559](https://github.com/dagullett/SOC-Automation/assets/75142644/e08ca2c4-f24c-45e1-980c-b9df925706b9)

![Screenshot 2024-01-31 182004](https://github.com/dagullett/SOC-Automation/assets/75142644/47bb9fac-b513-467e-8895-7c28ea470322)

## Infected the Windows Machine with Mimikatz

![Screenshot 2024-01-31 183613](https://github.com/dagullett/SOC-Automation/assets/75142644/08fcc740-9731-4d58-a51c-4e70d5bf4bff)

I downloaded and installed Mimikatz from https://github.com/gentilkiwi/mimikatz/releases/tag/2.2.0-20220919 to simulate a malware infection. Mimikatz is a tool used by security professionals in Ethical Hacking or Red Teaming. Although it is a tool used by security professionals, your web browser and computer will alert you. When I downloaded it, I had to turn off security blockers in the Edge browser. I also had to add the downloads folder as an exception. Windows Defender catches it instantly and blocks you from infecting your system. Once it was downloaded, it was a matter of triggering the malware seen in the screen shot. This allowed logs to be sent to the Wazuh Dashboard.


