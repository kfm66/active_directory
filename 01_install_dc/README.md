# 01 Insatll DC 

1. use "SConfig" to:
  - chnage the hostname
  - change the IP address to static
  - change the DNS server to our own IP address

2. install the Active Directory Windows Feature 


'''shell
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
'''