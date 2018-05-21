# Basic pod info

![](assets/images/dne-dci-dcloud.png)

| Hostname | Description | IP Address | Credentials |
| --- | --- | --- | --- |
| **wkst1** | Dev Workstation: Windows | 198.18.133.36 | dcloud\demouser/C1sco12345 |
| **ubuntu** | Dev Workstation: Linux | 198.18.134.28 | root/C1sco12345 |
| **nxosv-1** | Nexus 9000v - 7.0.3(I2).1 | 198.18.134.140 | admin/C1sco12345 |
| **nxosv-2** | Nexus 9000v - 7.0.3(I2).1 | 198.18.134.141 | admin/C1sco12345 |
| **centos1** | CentOS 7 Server - Automation Target | 198.18.134.49 | root/C1sco12345 or demouser/C1sco12345 |
| **centos2** | CentOS 7 Server - Automation Target | 198.18.134.50 | root/C1sco12345 or demouser/C1sco12345 |
| **ios-xe-mgmt.cisco.com** | CSR1000v - 16.08.01 | ios-xe-mgmt.cisco.com:8181 | root/D_Vay!_10& |
| ucsctl1 | UCS Central - 1.5(1b) | 198.18.133.90 | admin/C1sco12345 |
| ucsm1 | UCS Manager Emulator | 198.18.133.91 | admin/C1sco12345 |
| apic1 | ACI Simulator - 2.1.1h | 198.18.133.200 | admin/C1sco12345 |
| ucsd | UCS Director - 6.0.1.1 | 198.18.133.112 | admin/C1sco12345 |
| win2012r2 | Windows 2012 Standard Server - Automation Target | 198.18.133.20 | dcloud\administrator/C1sco12345 |
| vc1 | vCenter 6.0 | 198.18.133.30 | administrator@vsphere.local/C1sco12345! |
| vesx1 | vSphere Host | 198.18.133.31 | root/C1sco12345 |
| vesx2 | vSphere Host | 198.18.133.32 | root/C1sco12345 |
| cimc1 | UCS IMC Emulator | 198.18.134.88 | root/C1sco12345 or admin/C1sco12345 |
| na-edge1 | vNetApp | 198.18.133.115 | root/C1sco12345 |
| ad1 | Domain Controller | 198.18.133.1 | administrator/C1sco12345 |


## Getting connected

We will loosely follow Steps 2 and 3 at: https://learninglabs.cisco.com/tracks/devnet-express-dci/devnet-express-dci-prep/dne-dci-prep-01/step/2

1. Run Anyconnect client and fill in url with ```dcloud-lon-anyconnect.cisco.com``` 

1. Click connect, and log in with the credentials from your assigned pod, listed below:

| Session Id |  Session Name |  Usernames |  Password |  Start |  Stop |  Public IPs |
| --- | --- | --- | --- | --- | --- | --- |
| 290557 | 1 - Cisco DevNet Express Data Center v2 | v354user1; v354user2; ... v354user16 | 386ad4 | 5/21/18 10:30 | 5/25/18 9:00 | 173.38.222.120 |
| 290556 | 2 - Cisco DevNet Express Data Center v2 | v257user1; v257user2; ... v257user16 | 244138 | 5/21/18 10:34 | 5/25/18 8:56 | 173.38.222.121 |
| 290555 | 3 - Cisco DevNet Express Data Center v2 | v220user1; v220user2; ... v220user16 | a4f64a | 5/21/18 10:38 | 5/25/18 8:52 | 173.38.222.122 |
| 290554 | 4 - Cisco DevNet Express Data Center v2 | v846user1; v846user2; ... v846user16 | 1b3870 | 5/21/18 10:42 | 5/25/18 8:48 | 173.38.222.124 |
| 290553 | 5 - Cisco DevNet Express Data Center v2 | v621user1; v621user2; ... v621user16 | ccb2c5 | 5/21/18 10:46 | 5/25/18 8:44 | 173.38.222.126 |
| 290552 | 6 - Cisco DevNet Express Data Center v2 | v283user1; v283user2; ... v283user16 | 16720b | 5/21/18 10:50 | 5/25/18 8:40 | 173.38.222.128 |
| 290551 | 7 - Cisco DevNet Express Data Center v2 | v261user1; v261user2; ... v261user16 | 111a9c | 5/21/18 10:54 | 5/25/18 8:36 | 173.38.222.79 |
| 290550 | 8 - Cisco DevNet Express Data Center v2 | v320user1; v320user2; ... v320user16 | 35e100 | 5/21/18 10:58 | 5/25/18 8:32 | 173.38.222.130 |
| 290549 | 9 - Cisco DevNet Express Data Center v2 | v886user1; v886user2; ... v886user16 | 8f70ed | 5/21/18 11:02 | 5/25/18 8:28 | 173.38.222.133 |
| 290548 | 10 - Cisco DevNet Express Data Center v2 | v187user1; v187user2; ... v187user16 | 86d358 | 5/21/18 11:06 | 5/25/18 8:24 | 173.38.222.135 |
| 290547 | 11 - Cisco DevNet Express Data Center v2 | v286user1; v286user2; ... v286user16 | 7182ce | 5/21/18 11:10 | 5/25/18 8:20 | 173.38.222.138 |
| 290546 | 12 - Cisco DevNet Express Data Center v2 | v533user1; v533user2; ... v533user16 | 14ec15 | 5/21/18 11:14 | 5/25/18 8:16 | 173.38.222.141 |
| 290545 | 13 - Cisco DevNet Express Data Center v2 | v712user1; v712user2; ... v712user16 | d01035 | 5/21/18 11:18 | 5/25/18 8:12 | 173.38.222.144 |
| 290544 | 14 - Cisco DevNet Express Data Center v2 | v355user1; v355user2; ... v355user16 | c29f5a | 5/21/18 11:22 | 5/25/18 8:08 | 173.38.222.147 |
| 290543 | 15 - Cisco DevNet Express Data Center v2 | v869user1; v869user2; ... v869user16 | 0930fc | 5/21/18 11:26 | 5/25/18 8:04 | 173.38.222.152 |
| 290542 | 16 - Cisco DevNet Express Data Center v2 | v199user1; v199user2; ... v199user16 | b6c973 | 5/21/18 11:30 | 5/25/18 8:00 | 173.38.222.165 |
| 290541 | 17 - Cisco DevNet Express Data Center v2 | v326user1; v326user2; ... v326user16 | e24a9d | 5/21/18 11:34 | 5/25/18 7:56 | 173.38.222.166 |
| 290540 | 18 - Cisco DevNet Express Data Center v2 | v312user1; v312user2; ... v312user16 | 05dc7a | 5/21/18 11:38 | 5/25/18 7:52 | 173.38.222.168 |
| 290539 | 19 - Cisco DevNet Express Data Center v2 | v84user1; v84user2; ... v84user16 | d51266 | 5/21/18 11:42 | 5/25/18 7:48 | 173.38.222.170 |
| 290538 | 20 - Cisco DevNet Express Data Center v2 | v297user1; v297user2; ... v297user16 | 96dfba | 5/21/18 11:46 | 5/25/18 7:44 | 173.38.222.172 |
| 290537 | 21 - Cisco DevNet Express Data Center v2 | v91user1; v91user2; ... v91user16 | 1fdb8f | 5/21/18 11:50 | 5/25/18 7:40 | 173.38.222.174 |
| 290536 | 22 - Cisco DevNet Express Data Center v2 | v551user1; v551user2; ... v551user16 | ac1b94 | 5/21/18 11:54 | 5/25/18 7:36 | 173.38.222.176 |
| 290535 | 23 - Cisco DevNet Express Data Center v2 | v363user1; v363user2; ... v363user16 | 60e104 | 5/21/18 11:58 | 5/25/18 7:32 | 173.38.222.178 |
| 290534 | 24 - Cisco DevNet Express Data Center v2 | v275user1; v275user2; ... v275user16 | 78de49 | 5/21/18 12:02 | 5/25/18 7:28 | 173.38.222.179 |
| 290533 | 25 - Cisco DevNet Express Data Center v2 | v269user1; v269user2; ... v269user16 | 024606 | 5/21/18 12:06 | 5/25/18 7:24 | 173.38.222.39 |
| 290532 | 26 - Cisco DevNet Express Data Center v2 | v444user1; v444user2; ... v444user16 | 0d431f | 5/21/18 12:10 | 5/25/18 7:20 | 173.38.222.181 |
| 290531 | 27 - Cisco DevNet Express Data Center v2 | v344user1; v344user2; ... v344user16 | 37553f | 5/21/18 12:14 | 5/25/18 7:16 | 173.38.222.183 |
| 290530 | 28 - Cisco DevNet Express Data Center v2 | v514user1; v514user2; ... v514user16 | 5add50 | 5/21/18 12:18 | 5/25/18 7:12 | 173.38.222.184 |
| 290529 | 29 - Cisco DevNet Express Data Center v2 | v620user1; v620user2; ... v620user16 | 10e0e6 | 5/21/18 12:22 | 5/25/18 7:08 | 173.38.222.186 |
| 290528 | 30 - Cisco DevNet Express Data Center v2 | v18user1; v18user2; ... v18user16 | 5abbf0 | 5/21/18 12:26 | 5/25/18 7:04 | 173.38.222.188 | 

1. If you do not have a VNC client, RDP to 198.18.133.36 with your preferred client. Log in with user: ```dcloud\demouser``` and password ```C1sco12345```

    1. From Jumphost Download VNC from https://www.realvnc.com/download/file/viewer.files/VNC-Viewer-6.17.1113-Windows.exe
    1. Install VNC viewer on Jumphost

1. Within VNC client, connect to 198.18.134.28:1

1. From Ubuntu Desktop, run "Terminal for coding"
![](assets/images/term-coding.png)

1. Choose "2" for Python 2

1. Run ```pip install ansible --upgrade```

1. Run ``ansible --version`` and confirm you are at verion 2.5.x

1. Run ```cd ~``` to return to your home directory

1. Run ```git clone https://github.com/securenetwrk/ansible-workshop.git``` to pull down the repo for the labs

1. Run ```cd ~/ansible-workshop``` to enter workshop directory

