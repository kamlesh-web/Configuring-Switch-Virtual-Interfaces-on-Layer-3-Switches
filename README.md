    Switch>
    Switch>
    Switch>enable
    Switch#
    Switch#
    Switch#configure terminal
    Enter configuration commands, one per line.  End with CNTL/Z.
    Switch(config)#
    Switch(config)#hostname MSW0
    MSW0(config)#
    MSW0(config)#enable secret CCNA
    MSW0(config)#
    MSW0(config)#do show interface status
    Port      Name               Status       Vlan       Duplex  Speed Type
    Fa0/1                        connected    1          a-full  a-100 10/100BaseTX
    Fa0/2                        connected    1          a-full  a-100 10/100BaseTX
    Fa0/3                        connected    1          a-full  a-100 10/100BaseTX
    Fa0/4                        connected    1          a-full  a-100 10/100BaseTX
    Fa0/5                        notconnect   1          auto    auto  10/100BaseTX
    Fa0/6                        notconnect   1          auto    auto  10/100BaseTX
    
    (trancated...)
    
    Fa0/23                       notconnect   1          auto    auto  10/100BaseTX
    Fa0/24                       notconnect   1          auto    auto  10/100BaseTX
    Gig0/1                       connected    trunk      a-full  a-100 10/100/1000BaseTX
    Gig0/2                       notconnect   1          auto    auto  10/100/1000BaseTX
    
    MSW0(config)#interface range f0/5-24
    MSW0(config-if-range)#
    MSW0(config-if-range)#description ##Not in use##
    MSW0(config-if-range)#
    MSW0(config-if-range)#shutdown
    
    %LINK-5-CHANGED: Interface FastEthernet0/5, changed state to administratively down
    
    %LINK-5-CHANGED: Interface FastEthernet0/6, changed state to administratively down
    
    (trancated...)
    
    %LINK-5-CHANGED: Interface FastEthernet0/23, changed state to administratively down
    
    %LINK-5-CHANGED: Interface FastEthernet0/24, changed state to administratively down
    MSW0(config-if-range)#
    MSW0(config-if-range)#interface range f0/1-2
    MSW0(config-if-range)#
    MSW0(config-if-range)#switchport mode access
    MSW0(config-if-range)#
    MSW0(config-if-range)#switchport access vlan 40
    % Access VLAN does not exist. Creating vlan 40
    MSW0(config-if-range)#
    MSW0(config-if-range)#interface range f0/3-4
    MSW0(config-if-range)#
    MSW0(config-if-range)#switchport mode access
    MSW0(config-if-range)#
    MSW0(config-if-range)#switchport access vlan 50
    % Access VLAN does not exist. Creating vlan 50
    MSW0(config-if-range)#
    MSW0(config-if-range)#vlan 40
    MSW0(config-vlan)#
    MSW0(config-vlan)#name HR
    MSW0(config-vlan)#
    MSW0(config-vlan)#
    MSW0(config-vlan)#vlan 50
    MSW0(config-vlan)#
    MSW0(config-vlan)#name MANAGEMENT
    MSW0(config-vlan)#
    MSW0(config-vlan)#vlan 30
    MSW0(config-vlan)#
    MSW0(config-vlan)#name IT
    MSW0(config-vlan)#
    MSW0(config-vlan)#vlan 20
    MSW0(config-vlan)#	
    MSW0(config-vlan)#name ENGINEERING
    MSW0(config-vlan)#
    MSW0(config-vlan)#vlan 10
    MSW0(config-vlan)#
    MSW0(config-vlan)#name SALES
    MSW0(config-vlan)#
    MSW0(config-vlan)#exit
    MSW0(config)#
    MSW0(config)#do show vlan brief
    
    VLAN Name                             Status    Ports
    ---- -------------------------------- --------- -------------------------------
    1    default                          active    Fa0/5, Fa0/6, Fa0/7, Fa0/8
                                                    Fa0/9, Fa0/10, Fa0/11, Fa0/12
                                                    Fa0/13, Fa0/14, Fa0/15, Fa0/16
                                                    Fa0/17, Fa0/18, Fa0/19, Fa0/20
                                                    Fa0/21, Fa0/22, Fa0/23, Fa0/24
                                                    Gig0/2
    10   SALES                            active    
    20   ENGINEERING                      active    
    30   IT                               active    
    40   HR                               active    Fa0/1, Fa0/2
    50   MANAGEMENT                       active    Fa0/3, Fa0/4
    1002 fddi-default                     active    
    1003 token-ring-default               active    
    1004 fddinet-default                  active    
    1005 trnet-default                    active    
    MSW0(config)#
    MSW0(config)#
    
    ----------------------------------------------------------------------------------------------------------------------------------------------------------------------
    
    MSW0>
    MSW0>
    MSW0>enable
    Password: 
    Password: 
    MSW0#
    MSW0#
    MSW0#show interfaces status
    Port      Name               Status       Vlan       Duplex  Speed Type
    Fa0/1                        connected    40         a-full  a-100 10/100BaseTX
    Fa0/2                        connected    40         a-full  a-100 10/100BaseTX
    Fa0/3                        connected    50         a-full  a-100 10/100BaseTX
    Fa0/4                        connected    50         a-full  a-100 10/100BaseTX
    Fa0/5     ##Not in use##     disabled 1          auto    auto  10/100BaseTX
    Fa0/6     ##Not in use##     disabled 1          auto    auto  10/100BaseTX
    
    (trancated...)
    
    Fa0/23    ##Not in use##     disabled 1          auto    auto  10/100BaseTX
    Fa0/24    ##Not in use##     disabled 1          auto    auto  10/100BaseTX
    Gig0/1                       connected    trunk      a-full  a-100 10/100/1000BaseTX
    Gig0/2                       notconnect   1          auto    auto  10/100/1000BaseTX
    
    MSW0#
    MSW0#configure terminal
    Enter configuration commands, one per line.  End with CNTL/Z.
    MSW0(config)#
    MSW0(config)#
    MSW0(config)#interface vlan 10
    MSW0(config-if)#
    %LINK-5-CHANGED: Interface Vlan10, changed state to up
    
    %LINEPROTO-5-UPDOWN: Line protocol on Interface Vlan10, changed state to up
    
    MSW0(config-if)#ip address 192.168.255.14 255.255.255.240
    MSW0(config-if)#
    MSW0(config-if)#no shutdown
    MSW0(config-if)#
    MSW0(config-if)#interface vlan 20
    MSW0(config-if)#
    %LINK-5-CHANGED: Interface Vlan20, changed state to up
    
    %LINEPROTO-5-UPDOWN: Line protocol on Interface Vlan20, changed state to up
    
    MSW0(config-if)#ip address 192.168.255.30 255.255.255.240
    MSW0(config-if)#
    MSW0(config-if)#no shutdown
    MSW0(config-if)#
    MSW0(config-if)#interface vlan 30
    MSW0(config-if)#
    %LINK-5-CHANGED: Interface Vlan30, changed state to up
    
    %LINEPROTO-5-UPDOWN: Line protocol on Interface Vlan30, changed state to up
    
    MSW0(config-if)#ip address 192.168.255.46 255.255.255.240
    MSW0(config-if)#
    MSW0(config-if)#no shutdown
    MSW0(config-if)#
    MSW0(config-if)#interface vlan 40
    MSW0(config-if)#
    %LINK-5-CHANGED: Interface Vlan40, changed state to up
    
    %LINEPROTO-5-UPDOWN: Line protocol on Interface Vlan40, changed state to up
    
    MSW0(config-if)#ip address 192.168.255.54 255.255.255.240
    MSW0(config-if)#
    MSW0(config-if)#no shutdown
    MSW0(config-if)#
    MSW0(config-if)#interface vlan 50
    MSW0(config-if)#
    %LINK-5-CHANGED: Interface Vlan50, changed state to up
    
    %LINEPROTO-5-UPDOWN: Line protocol on Interface Vlan50, changed state to up
    
    MSW0(config-if)#ip address 192.168.255.78 255.255.255.240
    MSW0(config-if)#
    MSW0(config-if)#no shutdown
    MSW0(config-if)#
    MSW0(config-if)#exit
    MSW0(config)#
    MSW0(config)#
    MSW0(config)#ip routing
    MSW0(config)#
    MSW0(config)#interface g0/2
    MSW0(config-if)#
    MSW0(config-if)#no switchport
    MSW0(config-if)#
    MSW0(config-if)#ip address 192.168.255.81 255.255.255.252
    MSW0(config-if)#no shutdown
    MSW0(config-if)#
    MSW0(config-if)#exit
    MSW0(config)#
    MSW0(config)#ip route 0.0.0.0 0.0.0.0 192.168.255.82
    MSW0(config)#
    MSW0(config)#do show ip int br
    Interface              IP-Address      OK? Method Status                Protocol 
    
    (trancated...)
    
    GigabitEthernet0/1     unassigned      YES unset  up                    up 
    GigabitEthernet0/2     192.168.255.81  YES manual up                    up 
    Vlan1                  unassigned      YES unset  administratively down down 
    Vlan10                 192.168.255.14  YES manual up                    up 
    Vlan20                 192.168.255.30  YES manual up                    up 
    Vlan30                 192.168.255.46  YES manual up                    up 
    Vlan40                 192.168.255.62  YES manual up                    up 
    Vlan50                 192.168.255.78  YES manual up                    up
    MSW0(config)#
    MSW0(config)#do write
    Building configuration...
    [OK]
    MSW0(config)#
    %LINK-5-CHANGED: Interface GigabitEthernet0/2, changed state to up
    
    %LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/2, changed state to up
