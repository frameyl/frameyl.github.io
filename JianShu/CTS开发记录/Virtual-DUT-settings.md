Cisco Router Telnet:
```
interface GigabitEthernet0/0
 ip address 10.61.68.141 255.255.255.0
 duplex auto
 speed auto
 media-type rj45
!
line vty 0 4
 password spirent
 login
 transport input all
line vty 5 15
 password spirent
 login
 transport input all
!
```

ConnectToIut
```

    ###############################################################################################
    ## This procedure connects to IUT using Tcl Expect telnet. Modify this procedure in case the ##
    ## connection to IUT needs to use a different method e.g. a console connection or serial port##
    ###############################################################################################          
    package require ctsExpect 1.0    

    variable spawn_id
    variable expectRetValue
    variable sndCmdDelay

    set sndCmdDelay    350
    set timeout 10
    
	 set evalPrompt $IutPromptPrefix
    set evalPrompt [regsub {\[} $evalPrompt "\\\["]
    set evalPrompt [regsub {\]} $evalPrompt "\\\]"]
    set evalPrompt [regsub {\(} $evalPrompt "\\\("]
    set evalPrompt [regsub {\)} $evalPrompt "\\\)"]
    append evalPrompt (.*)\[$IutPromptChars\] 

	
    #set logInCmds [list "$LoginPrompt" "" "$PasswordPrompt" "" "$evalPrompt" ""]
    set logInCmds [list "$PasswordPrompt" "$Password" "$evalPrompt" "enable" "$PasswordPrompt" "$Password" "$evalPrompt" ""]
    exp_spawn telnet $IutAddress
    exp_send "\r"

    foreach {output input} $logInCmds {
        expect {
            -re $output {
                append expectRetValue $expect_out(buffer)
                if {$input != ""} {
                    exp_send "$input\r"
                    after $sndCmdDelay
                }
            }
            -re {(.+)} {
                append expectRetValue $expect_out(buffer)
                exp_continue
            }
            timeout { 
                LogInfo "$output not received from IUT"
                return -1
            }
        }
    }
      
```

```
IOSv_L3_68.142(config)#interface gi0/1
IOSv_L3_68.142(config-if)#ip address  128.96.50.145 255.255.255.0
IOSv_L3_68.142(config-if)#interface gi0/2
IOSv_L3_68.142(config-if)#ip address 128.96.51.146 255.255.255.0
IOSv_L3_68.142(config-if)#router ospf 11
IOSv_L3_68.142(config-router)#router-id 10.80.52.103
IOSv_L3_68.142(config-router)#network 6.43.0.0 0.0.255.255 area 36.0.0.0
IOSv_L3_68.142(config-router)#router bgp 2
IOSv_L3_68.142(config-router)#bgp router-id 128.96.52.147
IOSv_L3_68.142(config-router)#nei 128.96.50.2 remote-as 2
IOSv_L3_68.142(config-router)#nei 128.96.51.3 remote-as 102
IOSv_L3_68.142(config-router)#address-family ipv4 unicast
IOSv_L3_68.142(config-router-af)#nei 128.96.50.2 activate
IOSv_L3_68.142(config-router-af)#nei 128.96.51.3 activate
```

IutPromptPrefix IOSv_L3_68.142
IutPromptChars #>
