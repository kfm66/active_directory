# 01 Insatll DC 

1. use "SConfig" to:
  - chnage the hostname
  - change the IP address to static
  - change the DNS server to our own IP address

2. install the Active Directory Windows Feature 


```shell
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
```

 3. chnage the DNS server IP from loopback to the DC IP (192.168.80.160) make it return to its IP address
    - get the interface of the IP address DC uses
    - grap the (InterfaceIndex) value 
    - Get the DNS server client Address, the check the interface Index value ( most likeliy will be 127.0.0.1)
    - Change the DNS server setting by the command (Set-DNSClientServerAddress)
```shell 
# Get-NetIPAddress -IPAddress 192.168.80.160
get the DNS client Address 
Get-DNSClientServerAddress
# change the DNS client
Set-DNSClientServerAddress -InterfaceIndex 4 -ServerAddress 192.168.80.160
```

# 02 Joining the Worksation to the domain 

 1.  chnage the DNS server IP client to the DC IP (192.168.80.160) so machien can find the DC in the network
    - get the interface of the IP address DC uses
    - grap the (InterfaceIndex) value 
    - Get the DNS server client Address, the check the interface Index value ( most likeliy will be 127.0.0.1)
    - Change the DNS server setting by the command (Set-DNSClientServerAddress)

  2. Joine the Machine to the Domain


```shell
# get the Interface 
Get-NetIPAddress -IPAddress 192.168.80.160
# get the DNS client Address 
Get-DNSClientServerAddress
# change the DNS client
Set-DNSClientServerAddress -InterfaceIndex 4 -ServerAddress 192.168.80.160
# Join the machine to the Domain
Add-Computer -Domainname xyz.com -Credential xyz\Administrator -Force -Restrat 
```