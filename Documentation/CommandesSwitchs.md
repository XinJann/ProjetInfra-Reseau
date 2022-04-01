# Distrib_1

conf t  
vlan 10  
name dev  
exit  
vlan 20  
name design  
exit  
vlan 30  
name server  
exit  
interface range eth3/1,eth2/3  
switchport trunk encapsulation dot1q  
switchport mode trunk  
switchport trunk allowed vlan 10,20,30  
channel-group 1 mode active  
channel-protocol lacp  
no shutdown  
exit  
interface range eth3/2, eth3/0  
switchport trunk encapsulation dot1q  
switchport mode trunk  
switchport trunk allowed vlan 10,20,30  
channel-group 2 mode active  
channel-protocol lacp  
no shutdown  
exit  
interface eth3/3  
switchport trunk encapsulation dot1q  
switchport mode trunk  
switchport trunk allowed vlan 10,20,30  
no shutdown  
exit  
spanning-tree vlan 10 root primary  
spanning-tree vlan 20 root primary  
spanning-tree vlan 30 root primary  
end  
wr  

# Access_1

vlan 10  
name dev  
exit  
vlan 20  
name design  
exit  
vlan 30  
name server  
exit  
interface eth0/0  
switchport access vlan 10  
no shutdown  
exit  
interface eth0/1  
switchport access vlan 10   
no shutdown    
exit  
interface eth0/2  
switchport access vlan 20  
no shutdown  
exit  
interface range eth3/2-3  
switchport trunk encapsulation dot1q  
switchport mode trunk  
switchport trunk allowed vlan 10,20,30  
channel-group 1 mode active  
channel-protocol lacp  
no shutdown  
exit  
interface range eth3/0-1  
switchport trunk encapsulation dot1q  
switchport mode trunk  
switchport trunk allowed vlan 10,20,30  
channel-group 2 mode active  
channel-protocol lacp  
no shutdown  
exit  
end  
wr  

# Access_2

conf t  
vlan 10  
name dev  
exit  
vlan 20  
name design  
exit  
interface eth0/0  
switchport access vlan 20  
no shutdown  
exit  
interface eth0/1  
switchport access vlan 10  
no shutdown  
exit  
interface eth0/2  
switchport access vlan 20  
no shutdown  
exit  
interface range eth3/2-3  
switchport trunk encapsulation dot1q  
switchport mode trunk  
switchport trunk allowed vlan 10,20  
channel-group 1 mode active  
channel-protocol lacp  
no shutdown  
exit  
interface eth3/0  
switchport trunk encapsulation dot1q  
switchport mode trunk  
switchport trunk allowed vlan 10,20  
spanning-tree vlan 10 cost 80  
spanning-tree vlan 20 cost 80  
no shutdown  
exit  
interface eth3/1  
switchport trunk encapsulation dot1q  
switchport mode trunk  
switchport trunk allowed vlan 10,20  
spanning-tree vlan 10 cost 80  
spanning-tree vlan 20 cost 80  
no shutdown  
exit  
end  
wr  

# Access_3

conf t  
vlan 10  
name dev  
exit  
vlan 20  
name design  
exit  
interface eth0/0  
switchport access vlan 20  
no shutdown  
exit  
interface eth0/1  
switchport access vlan 10  
no shutdown  
exit  
interface eth0/2  
switchport access vlan 10  
no shutdown  
exit 
interface eth3/3  
switchport trunk encapsulation dot1q  
switchport mode trunk  
switchport trunk allowed vlan 10,20  
spanning-tree vlan 10 cost 80  
spanning-tree vlan 20 cost 80  
no shutdown  
exit  
interface eth3/2  
switchport trunk encapsulation dot1q  
switchport mode trunk  
switchport trunk allowed vlan 10,20  
spanning-tree vlan 10 cost 100  
spanning-tree vlan 20 cost 100  
no shutdown  
exit  
end  
wr  

# Access_4

conf t  
vlan 10  
name dev  
exit  
vlan 20  
name design  
exit  
interface eth0/0  
switchport access vlan 20  
no shutdown  
exit  
interface eth0/1  
switchport access vlan 10  
no shutdown  
exit  
interface eth0/2  
switchport access vlan 20  
no shutdown  
exit 
interface eth3/3  
switchport trunk encapsulation dot1q  
switchport mode trunk  
switchport trunk allowed vlan 10,20  
spanning-tree vlan 10 cost 80  
spanning-tree vlan 20 cost 80  
no shutdown  
exit  
interface eth3/2  
switchport trunk encapsulation dot1q  
switchport mode trunk  
switchport trunk allowed vlan 10,20  
spanning-tree vlan 10 cost 100  
spanning-tree vlan 20 cost 100  
no shutdown  
exit  
end  
wr  

# Access_5

conf t  
vlan 30  
name server  
exit  
interface eth0/0  
switchport access vlan 30  
no shutdown  
exit  
interface eth0/1  
switchport access vlan 30  
no shutdown  
exit  
interface range eth3/2-3  
switchport trunk encapsulation dot1q  
switchport mode trunk  
switchport trunk allowed vlan 30  
channel-group 1 mode active  
channel-protocol lacp  
no shutdown  
exit  
end  
wr  