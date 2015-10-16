Role Name
=========

Configures network interfaces for either static or dhcp.

Requirements
------------

None

Role Variables
--------------
These variables for most occasions should remain as they are. The actual variables should be defined within host_vars/host for each host requiring configurations.
````
---
# defaults file for ansible-config-interfaces
config_network_interfaces: false  #defines if interfaces should be configured...define in host_vars/host
interfaces: [] #define interfaces to configure...define in host_vars/host...unless setting all interfaces for every host to dhcp for example.
#  - name: eth0
#    address:
#    configure: true
#    gateway:
#    method: dhcp
#    netmask:
#    netmask_cidr:
#    network:
#    wireless_network: false  #defines if the interface is a wireless interface...not working so keep false or not defined
#    wpa_ssid: wireless  #defines the wireless SSID to connect to
#    wpa_psk: wpapassword  #defines the wireless key
#  - name: eth1
#    address:
#    configure:
#    gateway:
#    method:
#    netmask:
#    netmask_cidr: 24
#    network:
#  - name: enp0s3
#    address: 192.168.1.100
#    configure: true
#    gateway: 192.168.1.1
#    method: static
#    netmask: 255.255.255.0
#    netmask_cidr: 24
#    network: 192.168.1.0
dns_nameservers: '{{ pri_dns }} {{ sec_dns }}'  #defines all dns servers to configure...define here or globally in group_vars/all
dns_search: '{{ pri_domain_name }}'  #defines your global dns suffix search...define here or globally in group_vars/all
pri_dns:  #defines primary dns server...define here or globally in group_vars/all
sec_dns:  #defines secondary dns server...define here or globally in group_vars/all
````

Dependencies
------------

If interface is wireless you will need to define as such as well as provide the SSID and key.

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: mrlesmithjr.config-interfaces }

License
-------

BSD

Author Information
------------------

Larry Smith Jr.
- @mrlesmithjr
- http://everythingshouldbevirtual.com
- mrlesmithjr [at] gmail.com