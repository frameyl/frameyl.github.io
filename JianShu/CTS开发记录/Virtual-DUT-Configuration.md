Save configuration:
```
copy run start
```

```
!
! Last configuration change at 17:02:41 UTC Wed Jun 13 2018
!
version 15.6
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
!
hostname IOSv_L3_68.124
!
boot-start-marker
boot-end-marker
!
!
enable secret 5 $1$Eyl7$MfqBJNEq68vVYeSgQbfrv.
enable password ttcn3
!
no aaa new-model
ethernet lmi ce
!
!
!
mmi polling-interval 60
no mmi auto-configure
no mmi pvc
mmi snmp-timeout 180
!
!
ip cef
ipv6 unicast-routing
ipv6 cef
!
multilink bundle-name authenticated
!
!
redundancy
!
!
interface GigabitEthernet0/0
 ip address 10.61.68.124 255.255.255.0
 duplex auto
 speed auto
 media-type rj45
 no mop enabled
!
interface GigabitEthernet0/1
 ip address 128.96.50.145 255.255.255.0
 shutdown
 duplex auto
 speed auto
 media-type rj45
 ipv6 address FE80::C1:1 link-local
 ipv6 address 3FFE:C1::1/64
!
interface GigabitEthernet0/2
 ip address 128.96.51.146 255.255.255.0
 shutdown
 duplex auto
 speed auto
 media-type rj45
 ipv6 address FE80::C2:2 link-local
 ipv6 address 3FFE:C2::2/64
!
interface GigabitEthernet0/3
 ip address 128.96.52.147 255.255.255.0
 shutdown
 duplex auto
 speed auto
 media-type rj45
 ipv6 address FE80::C3:3 link-local
 ipv6 address 3FFE:C3::3/64
!
router bgp 2
 bgp router-id 128.96.52.147
 bgp log-neighbor-changes
 bgp graceful-restart restart-time 60
 bgp graceful-restart stalepath-time 60
 bgp graceful-restart
 neighbor 3FFE:C1::1000 remote-as 1
 neighbor 3FFE:C2::2000 remote-as 2
 neighbor 128.96.50.2 remote-as 1
 neighbor 128.96.51.3 remote-as 2
 neighbor FE80::C1:1000%GigabitEthernet0/1 remote-as 1
 neighbor FE80::C2:2000%GigabitEthernet0/2 remote-as 2
 !
 address-family ipv4
  no neighbor 3FFE:C1::1000 activate
  no neighbor 3FFE:C2::2000 activate
  neighbor 128.96.50.2 activate
  neighbor 128.96.50.2 capability orf prefix-list both
  neighbor 128.96.51.3 activate
  neighbor 128.96.51.3 capability orf prefix-list both
  neighbor FE80::C1:1000%GigabitEthernet0/1 activate
  neighbor FE80::C2:2000%GigabitEthernet0/2 activate
 exit-address-family
 !
 address-family ipv6
  neighbor 3FFE:C1::1000 activate
  neighbor 3FFE:C2::2000 activate
  neighbor FE80::C1:1000%GigabitEthernet0/1 activate
  neighbor FE80::C2:2000%GigabitEthernet0/2 activate
 exit-address-family
!
ip forward-protocol nd
!
!
no ip http server
no ip http secure-server
ip route 10.0.0.0 255.0.0.0 10.61.68.1
ip ssh version 1
!
!
!
!
control-plane
!
banner exec ^C
**************************************************************************
* IOSv is strictly limited to use for evaluation, demonstration and IOS  *
* education. IOSv is provided as-is and is not supported by Cisco's      *
* Technical Advisory Center. Any use or disclosure, in whole or in part, *
* of the IOSv Software or Documentation to any third party for any       *
* purposes is expressly prohibited except as otherwise authorized by     *
* Cisco in writing.                                                      *
**************************************************************************^C
banner incoming ^C
**************************************************************************
* IOSv is strictly limited to use for evaluation, demonstration and IOS  *
* education. IOSv is provided as-is and is not supported by Cisco's      *
* Technical Advisory Center. Any use or disclosure, in whole or in part, *
* of the IOSv Software or Documentation to any third party for any       *
* purposes is expressly prohibited except as otherwise authorized by     *
* Cisco in writing.                                                      *
**************************************************************************^C
banner login ^C
**************************************************************************
* IOSv is strictly limited to use for evaluation, demonstration and IOS  *
* education. IOSv is provided as-is and is not supported by Cisco's      *
* Technical Advisory Center. Any use or disclosure, in whole or in part, *
* of the IOSv Software or Documentation to any third party for any       *
* purposes is expressly prohibited except as otherwise authorized by     *
* Cisco in writing.                                                      *
**************************************************************************^C
!
line con 0
line aux 0
line vty 0 4
 password spirent
 login
 transport input all
line vty 5 15
 password spirent
 login
 transport input all
!
no scheduler allocate
!
end
```
