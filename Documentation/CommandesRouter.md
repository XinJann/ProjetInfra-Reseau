# Router

conf t  
hostname Rt  
interface fastethernet0/0  
no shutdown  
exit  
interface fastethernet0/0.1  
encapsulation dot1q 10  
ip address 192.168.10.254 255.255.255.0  
ip nat inside  
no shutdown  
exit  
interface fastethernet0/0.2  
encapsulation dot1q 20  
ip address 192.168.20.254 255.255.255.0  
ip nat inside  
no shutdown  
exit  
interface fastethernet0/0.3  
encapsulation dot1q 30  
ip address 192.168.30.14 255.255.255.240  
ip nat inside  
no shutdown  
exit  
interface fastethernet 1/0  
ip address dhcp  
ip nat outside  
exit  
ip dhcp pool 10  
network 192.168.10.0 255.255.255.0  
dns-server 192.168.30.1  
default-router 192.168.10.254  
exit  
ip dhcp pool 20  
network 192.168.20.0 255.255.255.0  
dns-server 192.168.30.1  
default-router 192.168.20.254  
exit  
access-list 1 permit any  
end  
wr  