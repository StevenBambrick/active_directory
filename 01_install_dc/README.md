# 01 Installing the Domain Controller

Use `SConfig` to:
    - change hostname
    - change IP address to static
    - change DNS server to own IP

# Configure PS-Remoting on Server
```shell
start-service winrm
enable-psremoting -force
```

# Configure PS-Remoting on client (temporarily)
``` shell
start-service winrm
set-item wsman:\localhost\client\TrustedHosts -value {server IP}
enter-pssession -computername {server IP} -credential (Get-Credential)
```

# Install the Active Directory Windows feature
``` shell
Install-WindowsFeature AD-DomainServices -IncludeManagementTools
Import-Module ADDSDeployment
Install-ADDSForest
https://i.imgur.com/wN6ENsn.png
```

# Change the DNS address after the server reboots
```shell
get-netipaddress -ipaddress 192.168.57.155
get-dnsclientserveraddress
set-dnsclientserveraddress -interfaceindex 4 -serveraddresses 192.168.57.155
get-dnsclientserveraddress
```

# Shutdown and take a snapshot
`shutdown /s /t 0`


# Add a client to the domain
```shell
get-dnsclientserveraddress
set-dnsclientserveraddress -interfaceindex 4 -serveraddresses 192.168.57.155
add-computer -domainname xyz -credential xyz\administrator -restart -force
```
Check that the new client is on the same network as the DC - it may not be depending on how the VM network settings are configured


