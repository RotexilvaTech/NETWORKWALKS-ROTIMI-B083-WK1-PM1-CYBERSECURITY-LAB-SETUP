# NETWORKWALKS-ROTIMI-B083-WK1-PM1-CYBERSECURITY-LAB-SETUP
My first lab environment setup involving Kali Linux and Windows 10 OS on Virtual Box


Task 1 Downloading and Installation of Oracle virtual Box
I couldn't see Network icon when I wanted to set the Network for the VM, because I didn't choose between user experience of VirtualBox. been first time using VirtualBox. I later discovered that I have to choose mode which i chose Expert mode out of two options (Basic and Expert mode).

<img width="4032" height="3024" alt="20261119_233238" src="https://github.com/user-attachments/assets/164a1940-9c52-45d4-8903-42db6f27da9e" />


Task 2 Downloading and installation of Kali Linux, extracted to be added as VM on VirtualBox.
Next step involve  Setting up the Kali NATnetwork.

<img width="3024" height="4032" alt="20261119_234000" src="https://github.com/user-attachments/assets/351ed37b-9278-461c-836f-31168b13d378" />

Next step - Running Kali and setting up it ipv4 Network to have access to Internet. by setting up IP address. mask, gateway, and dns( I used 10.0.0.1 as my dns).

<img width="3024" height="4032" alt="20261119_234345" src="https://github.com/user-attachments/assets/f6a14b9d-c257-4dc7-a0f5-75a1c27502b7" />


Task 3. Checking Kali Internet Access. by going to browser and make a search on Google.com

<img width="3024" height="4032" alt="20261119_234617" src="https://github.com/user-attachments/assets/6b128bda-562b-42ae-90bd-03b0e62636da" />


Task 4 Windows 10 lab setup.
Downloaded Windows 10 OS from Microsoft, Created new VM in VirualBox. named Windows 10 - Lab
Windows storage detail : RAM - 4GB, DRIVE - 45GB.
Then Attached and Installed OS 

<img width="3024" height="2426" alt="20261117_004745" src="https://github.com/user-attachments/assets/7bb45ae2-c668-4028-9387-de33ad6705c4" />


Task 5 Setting Windows 10 VM Network to same NAT Network as Kali VM.

<img width="3024" height="4032" alt="20261120_000416" src="https://github.com/user-attachments/assets/7c2eabb6-a82f-4210-af7e-21fc93872129" />

Then setting the Windows Network IP, Subnet mask, Default gateway and DNS. (Had a little ip addres conflict here but troubleshoot it and got it solved after some minutes.

<img width="3024" height="4032" alt="20261120_001047" src="https://github.com/user-attachments/assets/a9bd1d66-637b-4860-b694-b6374e2fe45b" />

Testing Windows Network (Pinging Kali VM and Windows Network access test)

<img width="3024" height="4032" alt="20261120_001047" src="https://github.com/user-attachments/assets/70358d54-c6d0-4c10-84a2-ef14317b2448" />

Task 6: Testing Network connection between the two VMs (Kali to Windows 10 OS)

<img width="3024" height="4032" alt="20261119_225802" src="https://github.com/user-attachments/assets/e8ce4fd1-9981-4f3f-a4c4-723af2bc11e3" />
