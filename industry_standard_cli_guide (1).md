# Celestica Enterprise SONiC Industry Standard CLI Guide

## Table of Contents

  - [Document History](#document-history)
  - [Introduction](#introduction)
  - [Getting Started](#getting-started)
    - [Login](#login)
  - [Getting Help](#getting-help)
    - [Command Modes](#command-modes)
    - [Auto completion](#auto-completion)
    - [Common mode commands](#common-mode-commands)
    - [Pipe options](#pipe-options)
  - [Basic Commands](#basic-commands)
    - [terminal length](#terminal-length)
    - [show terminal length](#show-terminal-length)
    - [show running-config](#show-running-config)
    - [show startup-config](#show-startup-config)
    - [hostname](#hostname)
    - [reboot](#reboot)
    - [show history](#show-history)
    - [show users](#show-users)
    - [show version](#show-version)
    - [show reboot history](#show-reboot-history)
    - [show reboot-cause](#show-reboot-cause)
    - [show environment](#show-environment)
    - [show log](#show-log)
    - [show uptime](#show-uptime)
    - [show services](#show-services)
    - [show clock](#show-clock)
    - [show techsupport](#show-techsupport)
    - [show techsupport status](#show-techsupport-status)
    - [show interface autoneg status](#show-interface-autoneg-status)
    - [show interface fec status](#show-interface-fec-status)
    - [show interface link-training status](#show-interface-link-training-status)
    - [platform show commands](#platform-show-commands)
      - [psustatus](#psustatus)
      - [fan](#fan)
      - [temperature](#temperature)
      - [syseeprom](#syseeprom)
      - [firmware status](#firmware-status)
      - [ssdhealth](#ssdhealth)
      - [summary](#summary)
      - [pcieinfo](#pcieinfo)
      - [porttransceiver](#porttransceiver)
      - [show port transceiver lpmode](#show-port-transceiver-lpmode)
    - [show system](#show-system)
      - [system status](#system-status)
      - [system-health monitor-list](#system-health-monitor-list)
    - [show secure-boot commands](#secure-boot)
      - [show secure-boot status](#secure-boot-status)
      - [show secure-boot certificate](#secure-boot-certificate)
  - [Advanced Commands](#advanced-commands)
      - [Execute file](#execute-file)
  - [Guidelines](#guidelines)
     - [Encryption guidelines](#encryption-guidelines)
     - [Telemetry configuration guidelines](#telemetry-configuraiton-guidelines)
  - [Config File Commands](#config-file-commands)
    - [Copy running-config to startup-config](#copy-running-config-to-startup-config)
    - [Copy running-config to local file](#copy-running-config-to-local-file)
    - [Copy startup-config to local file](#copy-startup-config-to-local-file)
    - [Copy local file config to startup-config](#copy-local-file-config-to-startup-config)
    - [Copy local file config to running-config](#copy-local-file-config-to-running-config)
    - [Remove startup-config](#remove-startup-config)
  - [Access Control Lists](#access-control-lists)
    - [IPv4 ACL Commands](#ipv4-acl-commands)
      - [IPv4 Access-list create and delete](#ipv4-access-list-create-and-delete)
      - [IPv4 Access-list rules create and delete](#ipv4-access-list-rules-create-and-delete)
      - [IPv4 Access-list bind to interface](#ipv4-access-list-bind-to-interface)
      - [IPv4 Access-list show command](#ipv4-access-list-show-command)
      - [IPv4 Access-group show command](#ipv4-access-group-show-command)
      - [IPv4 Access-list clear command](#ipv4-access-list-clear-command)
    - [IPv6 ACL Commands](#ipv6-acl-commands)
      - [IPv6 Access-list create and delete](#ipv6-access-list-create-and-delete)
      - [IPv6 Access-list rules create and delete](#ipv6-access-list-rules-create-and-delete)
      - [IPv6 Access-list bind to interface](#ipv6-access-list-bind-to-interface)
      - [IPv6 Access-list show command](#ipv6-access-list-show-command)
      - [IPv6 Access-group show command](#ipv6-access-group-show-command)
      - [IPv6 Access-list clear command](#ipv6-access-list-clear-command)
    - [MAC ACL Commands](#mac-acl-commands)
      - [MAC Access-list create and delete](#mac-access-list-create-and-delete)
      - [MAC Access-list rules create and delete](#mac-access-list-rules-create-and-delete)
      - [MAC Access-list bind to interface](#mac-access-list-bind-to-interface)
      - [MAC Access-list show command](#mac-access-list-show-command)
      - [MAC Access-group show command](#mac-access-group-show-command)
      - [MAC Access-list clear command](#mac-access-list-clear-command)
  - [USER MANAGEMENT](#user-management)
    - [Password](#password)
  - [BANNER](#banner)
    - [MOTD Banner](#motd-banner)
    - [Login Banner](#login-banner)
  - [RADIUS](#radius)
    - [RADIUS Config Commands](#radius-config-commands)
      - [RADIUS timeout](#radius-timeout)
      - [RADIUS passkey](#radius-passkey)
      - [RADIUS authtype](#radius-authtype)
      - [RADIUS retransmit](#radius-retransmit)
      - [RADIUS host](#radius-host)
    - [RADIUS Show commands](#radius-show-commands)
      - [show radius](#show-radius)
  - [TACACS](#tacacs)
    - [TACACS Config Commands](#tacacs-config-commands)
      - [TACACS timeout](#tacacs-timeout)
      - [TACACS authtype](#tacacs-authtype)
      - [TACACS passkey](#tacacs-passkey)
      - [TACACS host](#tacacs-host)
    - [TACACS Show commands](#tacacs-show-commands)
      - [show tacacs](#show-tacacs)
  - [NTP](#ntp)
    - [NTP Config Commands](#ntp-config-commands)
      - [NTP source-interface](#ntp-source-interface)
      - [NTP vrf](#ntp-vrf)
      - [NTP server](#ntp-server)
    - [NTP Show commands](#ntp-show-commands)
      - [show ntp status](#show-ntp-status)
      - [show ntp associations](#show-ntp-associations)
  - [Syslog](#syslog)
    - [Syslog Config Commands](#syslog-config-commands)
      - [syslog server](#syslog-server)
  - [Interfaces](#interfaces)
    - [Common Interface Commands](#common-interface-commands)
      - [Interface create and delete](#interface-create-and-delete)
      - [`description`](#description)
      - [clear interface counters](#clear-interface-counters)
      - [show interface](#show-interface)
      - [show interface status](#show-interface-status)
      - [show interface description](#show-interface-description)
      - [show interface counters](#show-interface-counters)
      - [show interface transceiver](#show-interface-transceiver)
    - [Breakout](#breakout)
      - [config interface breakout](#config-interface-breakout)
      - [show interface breakout](#show-interface-breakout)
    - [Ethernet Interface commands](#ethernet-interface-commands)
      - [Interface Shutdown command](#shutdown)    
      - [MTU configuration command](#mtu)    
      - [TPID configuration command](#tpid)                    
      - [channel-group](#channel-group)    
      - [wred queue](#wred-queue)    
      - [advertise speeds](#advertise-speed)
      - [advertise type](#advertise-type)
      - [type](#type)
    - [PortChannel Interface commands](#portchannel-interface-commands)
    - [VLAN Interface commands](#vlan-interface-commands)
    - [Loopback Interface commands](#loopback-interface-commands)
    - [Tunnel Interface commands](#tunnel-interface-commands)
      - [Tunnel source-ip configuration command](#tunnel-source-ip)    
      - [Tunnel destination-ip configuration command](#tunnel-destination-ip) 
      - [Tunnel destination-ip configuration command](#tunnel-ip) 
  - [Layer 2](#layer-2)
     - [VLAN](#vlan)
       - [Switchport access vlan](#switchport-access-vlan)
       - [Switchport trunk vlan](#switchport-trunk-allowed-vlan-add)
       - [Show vlan](#show-vlan)            
     - [Port Channel](#portchannel)
       - [Show portchannel summary](#show-portchannel-summary)           
     - [LLDP](#lldp)
       - [LLLDP enable](#lldp-enable)
       - [LLDP timer](#lldp-timer)
       - [LLDP system-description](#lldp-system-description)
       - [LLDP tlv-selct](#lldp-tlv-select)
       - [Interface lldp enable](#interface-lldp-enable)
       - [LLDP MED](#lldp-med)
       - [Show lldp table](#show-lldp-table)
       - [Show lldp neighbor](#show-lldp-neighbor)
       - [Show lldp med](#show-lldp-med)
     - [MCLAG](#mclag)
       - [MCLAG domain](#mclag-domain)
       - [MCLAG source-ip](#source-ip)
       - [MCLAG peer-ip](#peer-ip)   
       - [MCLAG keepalive](#keepalive)
       - [MCLAG session-timeout](#session-timeout)
       - [MCLAG peer-link](#peer-link)       
       - [MCLAG system-mac](#system-mac)
       - [MCLAG session-vrf](#session-vrf)
       - [MCLAG interface](#mclag-interface)   
       - [MCLAG unique-ip](#unique-ip)  
       - [Show mclag brief](#show-mclag-brief)     
     - [FDB](#fdb)
       - [Clear mac address](#clear-mac-address-table-dynamic)
       - [Show mac address](#show-mac-address-table)
  - [Mirroring](#mirroring)
    - [Mirror Config commands](#mirror-config-commands)
     - [Mirror session create and delete](#mirror-session-create-and-delete)
     - [SPAN session config](#span-session-config)
     - [Everflow SPAN session config](#everflow-span-session-config)
     - [ERSPAN session config](#erspan-session-config)
     - [Everflow ERSPAN session config](#everflow-erspan-session-config)
    - [Mirror Show commands](#mirror-show-commands)
  - [SFLOW](#sflow)
    - [SFLOW Config commands](#sflow-config-commands)
     - [SFLOW global config commands](#sflow-global-config-commands)
      - [SFLOW enable](#sflow-enable)
      - [SFLOW polling-interval](#sflow-polling-interval)
      - [SFLOW agent-id](#sflow-agent-id)
      - [SFLOW collector](#sflow-collector)
      - [SFLOW interface disable](#sflow-interface-disable)
     - [SFLOW interface level config commands](#sflow-interface-level-config-commands)
      - [SFLOW interface enable](#sflow-interface-enable)
      - [SFLOW interface sampling-rate](#sflow-interface-sampling-rate)
    - [SFLOW Show commands](#sflow-show-commands)
      - [SFLOW show](#sflow-show)
      - [SFLOW show interfaces](#sflow-show-interfaces)
  - [Port security](#port-security)
    - [BUM Storm Control](#bum-storm-control)
    - [Config commands](#config-commands)
    - [Show commands](#show-commands)
  - [AAA](#aaa)
    - [Show aaa](#show-aaa)
    - [AAA Authentication login](#aaa-authentication-login)
    - [AAA Authentication failthrough](#aaa-authentication-failthrough)
    - [AAA Authorization](#aaa-authorization)
    - [AAA Accounting](#aaa-accounting)
  - [Static Anycast Gateway](#static-anycast-gateway)
    - [sag mac](#sag-mac)
    - [sag ip](#sag-ip)
    - [show sag mac](#show-sag-mac)
    - [show sag interface ](#show-sag-interface)     
  - [Dynamic Load-balancing](#dynamic-load-balancing)
    - [DLB idle-time](#dlb-hash-idle-time)
    - [DLB load current enable](#dlb-hash-load-current-enable)
    - [DLB load past enable](#dlb-hash-load-past-enable)
    - [DLB load future enable](#dlb-hash-load-future-enable)
    - [DLB load current weight](#dlb-hash-load-current-weight)
    - [DLB load past weight](#dlb-hash-load-past-weight)
    - [DLB load future weight](#dlb-hash-load-future-weight)    
    - [DLB max flows](#dlb-hash-max-flows)
    - [DLB random seed](#dlb-hash-random-seed)
    - [DLB sampling interval](#dlb-hash-sampling-interval)
    - [DLB quantization band minimum](#dlb-hash-quant-band-min)
    - [DLB quantization band maximum](#dlb-hash-quant-band-max)
    - [DLB Reassign probability](#dlb-hash-reassign-probability)
    - [DLB Reassign quality delta](#dlb-hash-reassign-quality-delta)        
    - [DLB mode](#dlb-hash-mode)
    - [show dlb-hash brief ](#show-dlb-hash-brief) 
  - [Tunnel](#tunnel)
    - [Show tunnel summary ](#show-tunnel-summary)    
  - [SNMP](#snmp)
    - [SNMP Contact](#snmp-contact)
    - [SNMP Location](#snmp-location)
    - [SNMP Community](#snmp-community)
    - [SNMP User](#snmp-user)
    - [SNMP Host](#snmp-host)
    - [SNMP Agentaddress](#snmp-agentaddress)
    - [Show SNMP contact and location](#show-snmp-contact-and-location)
    - [Show SNMP community](#show-snmp-community)
    - [Show SNMP user](#show-snmp-user)
    - [Show SNMP host](#show-snmp-host)
    - [Show SNMP agentaddress](#show-snmp-agentaddress)
  - [DHCP Relay](#dhcp-relay)
    - [DHCPv4 Relay Configuration](#dhcpv4-relay-configuration)
    - [Show DHCPv4 relay address](#show-dhcpv4-relay-address)
    - [DHCPv6 Relay Configuration](#dhcpv6-relay-configuration)
    - [Show DHCPv6 relay address](#show-dhcpv6-relay-address)
    - [Show DHCPv6 relay counters](#show-dhcpv6-relay-counters)
    - [Clear DHCPv6 relay counters](#clear-dhcpv6-relay-counters)
  - [CRM](#crm)
    - [CRM polling interval](#crm-polling-interval)
    - [CRM threshold resource](#crm-threshold-resource)
    - [show crm summary](#show-crm-summary)
    - [show crm resource](#show-crm-resource)
    - [show crm threshold](#show-crm-threshold)
  - [Feature](#feature)
    -  [Show Feature](#show-feature)
    -  [Config Feature](#config-feature)
  - [System management](#system-management)
    - [Image management](#image-management)
      - [Image install](#image-install)
      - [Image remove](#image-remove)
      - [Set default image](#set-default-image)
      - [Display image install status](#display-image-install-status)
      - [Display image list](#display-image-list)
    - [Process and Memory statistics](#process-and-memory-statistics)
      - [Display memory statistics](#display-memory-statistics)
      - [Display process statistics](#display-process-statistics)
    - [Bootloader Management](#bootloader-management)
      - [Set Credential](#set-credential)
      - [Clear Credential](#clear-credential)
      - [Boot Authentication](#boot-authentication)
  - [ZTP](#ztp)
    - [ZTP Enable](#ztp-enable)
    - [ZTP Disable](#ztp-disable)
    - [ZTP Run](#ztp-run)
    - [Show ZTP status](#show-ztp-status)
    - [Show ZTP status detail](#show-ztp-status-detail)
  - [ARP and NDP commands](#arp-and-ndp-commands)
    -  [show arp](#show-arp)
    -  [show ndp](#show-ndp)
    -  [clear arp](#clear-arp)
    -  [clear ndp](#clear-ndp)
  - [Miscellaneous Show commands](#miscellaneous-show-commands)
    -  [show vrf](#show-vrf)
    -  [show managment_interface address](#show-management_interface-address)
    -  [show mgmt-vrf](#show-mgmt-vrf)
    -  [show ip interfaces](#show-ip-interfaces)
    -  [show ipv6 interface](#show-ipv6-interfaces)
  - [Quality of Service (QoS)](#quality-of-service-qos)
    - [Congestion avoidance (Weighted Early Random Detection)](#congestion-avoidance-weighted-early-random-detection)
      - [qos wred-profile](#qos-wred-profile)
      - [random-detect color](#random-detect-color)
      - [random-detect ecn](#random-detect-ecn)
      - [show qos wred-profile](#show-qos-wred-profile)
      - [show qos wred interface](#show-qos-wred-interface)
    - [Qos Maps](#qos-maps)
      - [Create Dot1p to Traffic Class map](#create-dot1p-to-traffic-class-map)
      - [Configure Dot1p to Traffic Class map entries](#configure-dot1p-to-traffic-class-map-entries)
      - [Create DSCP to Traffic Class map](#create-dscp-to-traffic-class-map)
      - [Configure DSCP to Traffic Class map entries](#configure-dscp-to-traffic-class-map-entries)
      - [Create Traffic Class to Dot1p map](#create-traffic-class-to-dot1p-map)
      - [Configure Traffic Class to Dot1p map entries](#configure-traffic-class-to-dot1p-map-entries)
      - [Create Traffic Class to DSCP map](#create-traffic-class-to-dscp-map)
      - [Configure Traffic Class to DSCP map entries](#configure-traffic-class-to-dscp-map-entries)
      - [Create Traffic Class to Queue map](#create-traffic-class-to-queue-map)
      - [Configure Traffic Class to Queue map entries](#configure-traffic-class-to-queue-map-entries)
      - [Create Traffic Class to Priority Group map](#create-traffic-class-to-priority-group-map)
      - [Configure Traffic Class to Priority Group map entries](#configure-traffic-class-to-priority-group-map-entries)
      - [Create PFC Priority to Queue map](#create-pfc-priority-to-queue-map)
      - [Configure PFC Priority to Queue map entries](#configure-pfc-priority-to-queue-map-entries)
      - [Show qos maps](#show-qos-maps)
      - [Attach qos map to interface](#attach-qos-map-to-interface)
      - [Show qos maps attached to interface](#show-qos-maps-attached-to-interface)
    - [Scheduler](#scheduler-configuration)
      - [Enter scheduler configuration mode](#enter-scheduler-configuration-mode)
      - [Configure scheduler policy per queue](#configure-scheduler-policy-per-queue)
      - [Configure scheduler algorithm](#configure-scheduler-algorithm)
      - [Configure weight for queue scheduling](#configure-weight-for-queue-scheduling)
      - [Attach scheduler policy to interface](#attach-scheduler-policy-to-interface)
      - [Show scheduler policy](#show-scheduler-policy)
      - [Show scheduler policy interface](#show-scheduler-policy-interface)
    - [Buffer Management](#buffer-management)
      - [Enable Buffer management](#enable-buffer-management)
      - [Create Buffer profile](#create-buffer-profile)
      - [Attach Buffer profile to priority group](#attach-buffer-profile-to-priority-group)
      - [Attach Buffer profile to queue](#attach-buffer-profile-to-queue)
      - [Enable Pfc](#enable-pfc)  
      - [Show Buffer pool](#show-buffer-pool)
      - [Show Buffer profile](#show-buffer-profile)
      - [Show priority group](#show-priority-group)
      - [Show interface Priority group](#show-interface-priority-group)
      - [Show interface Queue Profile](#show-interface-queue-profile)
      - [Show PFC interface status](#show-pfc-interface-status)
    - [Queue](#queue)
      - [Show queue counters](#show-queue-counters)
      - [Show queue watermark](#show-queue-watermark)
   - [Telemetry](#Telemetry)
     - [Telemetry mode](#telemetry-mode)
     - [Server port](#server-port)
     - [Server certificate](#server-certificate)
     - [Authentication type](#authentication-type)
     - [CA certificate](#ca-certificate)
     - [Retry interval](#retry-interval)
     - [Destination group](#destination-group)
       - [Destination address](#destination-address)
     - [Subscription group](#subscription-group)
       - [Report interval](#report-interval)
       - [Associate destination group](#associate-destination-group)
       - [Collection paths](#collection-paths)
       - [Report type](#report-type)
       - [Target DB](#target-db)
     - [Show telemetry server](#show-telemetry-server)
     - [Show destination group](#show-destination-group)
     - [Show subscription group](#show-subscription-group)
   - [VxLAN](#vxlan)
     - [VxLAN Config commands](#vxlan-config-commands)
      - [VxLAN global config commands](#vxlan-global-config-commands)
        - [Vxlan-profile enable](#vxlan-profile-enable)
        - [Vxlan interface create and delete](#vxlan-interface-create-and-delete)
      - [VxLAN interface level config commands](#vxlan-interface-level-config-commands)
        - [Source-vtep-ip ](#source-vtep-ip)
        - [Map-vni-vlan](#map-vni-vlan)
    - [VxLAN Show commands](#vxlan-show-commands)
      - [Show vxlan interface](#show-vxlan-interface)
      - [Show vxlan vlanvnimap](#show-vxlan-vlanvnimap)
      - [Show vxlan tunnel](#show-vxlan-tunnel)
      - [Show vxlan counters](#show-vxlan-counters)
      - [Show vxlan remote mac](#show-vxlan-remote-mac)
      - [Show vxlan remote vni](#show-vxlan-remote-vni)
    - [VxLAN Clear commands](#vxlan-clear-commands)
      - [Clear vxlan counters](#clear-vxlan-counters)
  - [BGP config commands](#bgp-config-commands)
        - [BGP router config](#bgp-router-config)
        - [Router id](#router-id)
        - [Always-compare-med](#always-compare-med)
        - [Bestpath as-path confed](#bestpath-as-path-confed)
        - [Bestpath as-path multipath-relax](#bestpath-as-path-multipath-relax)
        - [Bestpath bandwidth](#bestpath-bandwidth-default-weight-for-missing)
        - [Bestpath compare-routerid](#bestpath-compare-routerid)
        - [Bestpath med](#bestpath-as-med-confed)
        - [Bestpath peer-type multipath-relax](bestpath-peer-type-multipath-relax)
        - [BGP community-list](#bgp-community-list)
        - [BGP extcommunity-list](#bgp-extcommunity-list)
        - [BGP large-community-list](#large-community-list)
        - [BGP client-to-client reflection](#bgp-clientto-client-reflection)
        - [BGP cluster-id](#bgp-clutser-id)
        - [BGP confederation](#bgp-confederation)
        - [BGP dampening](#bgp-dampening)
        - [BGP default](#bgp-default)
        - [BGP deterministic-med](#bgp-deterministic-med)
        - [BGP disable-ebgp-connected-route-check](#bgp-disable-ebgp-connected-route-check)
        - [Ebgp requires policy](#ebgp-requires-policy)
        - [BGP fast-external-failover](#bgp-fast-external-failover)
        - [BGP graceful-restart](#bgp-graceful-restart)
        - [BGP graceful-restart-disable](#bgp-graceful-restart-disable)
        - [BGP graceful-shutdown](#bgp-graceful-shutdown)
        - [BGP listen](#bgp-listen)
        - [Log neighbor changes](#log-neighbor-changes)
        - [BGP max-med](#bgp-max-med)
        - [BGP network](#bgp-network)
        - [BGP reject-as-sets](#bgp-reject-as-sets)
        - [BGP route-map](#bgp-route-map-delay-timer)
        - [BGP route-reflector](#bgp-route-reflector-allow-outbound-policy)
        - [BGP route-id A.B.C.D](#bgp-route-id-<A.B.C.D>)
        - [BGP session-dscp](#bgp-session-dscp-val)
        - [BGP shutdown](#bgp-shutdown-message)
        - [address-family](#address-family-ipv4|ipv6-unicast)
        - [aggregate-address](#aggregate-address)
        - [coalesce-timer](#coalesce-time)
        - [exit-address-family](#exit-address-family)
        - [Maximum paths](#maximum-paths<path-count>)
        - [Neighbor remote as](#neighbor-remote-as)
        - [Neighbor activate](#neighbor-activate)
        - [Neigbhor addpath-rx-all-paths](#neigbhor-addpath-tx-all-paths)
        - [Neighbor addpath-tx-bestpath-per-AS](#neighbor-addpath-tx-bestpath-per-AS)
        - [Neigbhbor advertisement-interval](#neighbor-advertisement-interval)
        - [Neigbhbor allowas-in](#neighbor-allowas-in)
        - [Neighbor as-override](#neighbor-as-override)
        - [Neighbor attribute-unchanged](#neighbor-attribute-unchanged)
        - [Neigbhor capability](#neighbor-capability)
        - [Neighbor default-originate](#neighbor-default-originate)
        - [Neighbor description](#neighbor-description)
        - [Neighbor disable-connected-check](#neighbor-disable-connected-check)
        - [Neighbor distribute-list](#neighbor-distribute-list)
        - [Neighbor dont-capability-negotiate](#neighbor-dont-capability-negotiate)
        - [Neighbor ebgp-multihop](#neighbor-ebgp-multihop)
        - [Neigbhor enforce-first-as](#neigbhor-enforce-first-as)
        - [Neighbor enforce-multihop](#neighbor-enforce-multihop)
        - [Neighbor filter-list](#neighbor-filter-list)
        - [Neigbhor graceful-restart](#neighbor-greaceful-restart)
        - [Neighbor graceful-restart-disable](#neighbor-graceful-restart-disable)
        - [Neighbor local-as](#neighbor-local-as)
        - [Neighbor maximum-prefix](#neighbor-maximum-prefix)
        - [Neighbor maximum-prefix-out](#neighbor-maximum-prefix-out)
        - [Neighbor next-hop-self](#neighbor-next-hop-self)
        - [Neighbor next-hop-loacl](#neighbor-next-hop-local)
        - [Neighbor override-capability](#neighbor-override-capability)
        - [Neighbor passive](#neighbor-passive)
        - [Neighbor password](#neighbor-password)
        - [Neighbor peer-group](#beighbor-peer-group)
        - [Neighbor port](neighbor-port)
        - [Neighbor prefix-list](#neighbor-prefix-list)
        - [Neighbor remote-private-as](#neighbor-remote-private-as)
        - [Neighbor route-map](#neighbor-route-map)
        - [Route Reflector Client](#route-reflector-client)
        - [Neighbor route-server-client](#neighbor-route-server-client)
        - [Neighbor send-community](#neighbor-send-community)
        - [Neighbor sender-as-path-loop-detection](#neighbor-sender-as-path-loop-detection)
        - [Neighbor shutdown](#neighbor-shutdown)
        - [Neighbor soft-reconfiguration](#neighbor-soft-reconfiguration)
        - [Neighbor solo](#neighbor-solo)
        - [Neighbor strict-capability-match](#neighbor-strict-capability-match)
        - [Neighbor timers](#neighbor-timers)
        - [Neighbor ttl-security](#neighbor-ttl-security)
        - [Neigbhor unsuppress-map](#neighbor-unsuppress-map)
        - [Neighbor update-source](#neigbhor-update-source)
        - [Neigbhor weight](#neighbor-weight)
        - [Neighbor vni](#neighbor-vni)
        - [network](#network)
        - [redistribute](#redistibute)
        - [table-map](table-map)
        - [timers](#timers)
        - [update-delay](#update-delay)
        - [Neighbor remote as](#neighbor-remote-as)
        - [IPv4 AFI extension](#ipv4-afi-extension)
        - [Network announcement](#network-announcement)
        - [IPv6 AFI extension](#ipv6-afi-extension)
        - [L2VPN AFI extension](#l2vpn-afi-extension)
        - [Advertise all vni](#advertise-all-vni)
      - [BGP EVPN show commands](#bgp-evpn-show-commands)
        - [Show bgp l2vpn evpn](#show-bgp-l2vpn-evpn)
        - [Show bgp l2vpn evpn all overlay](#show-bgp-l2vpn-evpn-all-overlay)
        - [Show bgp l2vpn evpn all tags](#show-bgp-l2vpn-evpn-all-tags)
        - [Show bgp l2vpn evpn import-rt](#show-bgp-l2vpn-evpn-import-rt)
        - [Show bgp l2vpn evpn neighbors advertised-routes](#show-bgp-l2vpn-evpn-neighbors-advertised-routes)
        - [Show bgp l2vpn evpn neighbors routes](#show-bgp-l2vpn-evpn-neighbors-routes)
        - [Show bgp l2vpn evpn route](#show-bgp-l2vpn-evpn-route)
        - [Show bgp l2vpn evpn route detail](#show-bgp-l2vpn-evpn-route-detail)
        - [Show bgp l2vpn evpn route vni](#show-bgp-l2vpn-evpn-route-vni)
        - [Show bgp l2vpn evpn statistics](#show-bgp-l2vpn-evpn-statistics)
        - [Show bgp l2vpn evpn summary](#show-bgp-l2vpn-evpn-summary)
        - [Show bgp l2vpn evpn update-groups](#show-bgp-l2vpn-evpn-update-groups)
        - [Show bgp l2vpn evpn vni](#show-bgp-l2vpn-evpn-vni)
   - [Layer 3](#layer3)
    - [OSPF](#ospf)
      - [OSPF Config commands](#ospf-config-commands)
      - [OSPF Interface commands](#ospf-interface-commands)
      - [OSPF Show commands](#ospf-show-commands)
      - [OSPF Clear commands](#ospf-clear-commands)
      - [OSPF Debug commands](#ospf-debug-commands)
    - [OSPF6](#ospf6)
      - [OSPF6 Config commands](#ospf6-config-commands)
      - [OSPF6 Interface commands](#ospf6-interface-commands)
      - [OSPF6 Show commands](#ospf6-show-commands)
      - [OSPF6 Clear commands](#ospf6-clear-commands)
      - [OSPF6 Debug commands](#ospf6-debug-commands)
  - [POE](#poe)
    - [POE Conifg Commands](#poe-config-commands)
      - [POE global config commands](#poe-global-config-commands)
      - [POE interface level config commands](#poe-interface-level-config-command)
    - [POE Clear commands](#poe-clear-commands)
    - [POE Show commands](#poe-show-commands)
  - [PNAC](#pnac)
    - [Dot1X and MAB](#dot1x-and-mab)
      - [Dot1X config commands](#dot1x-config-commands)
        - [Dot1X Interface level config commands](#dot1x-interface-config-commands)
      - [Dot1X show commands](#dot1x-show-commands)
    - [Edge security](#edge-security)
      - [Edge security config commands](#edge-security-config-commands)
      - [Edge security clear commands](#edge-security-clear-commands)
      - [Edge security show commands](#edge-security-show-commands)
  - [Crypto PKI](#crypto-pki)
    - [show ssh host-key](#show-ssh-host-key)
    - [ssh generate host-key](#ssh-generate-host-key)
  - [STP](#stp)
    - [stp config commands](#stp-config-commands)
      - [stp Interface level config commands](#stp-interface-config-commands)
    - [stp show commands](#stp-show-commands)
  - [CLI translate](#cli-translate)
    - [CLI translate config commands](#cli-translate-config-commands)
  - [UDF hash support and enhancements](#udf-hash-support-and-enhancements)
    - [ip switch-hash ecmp ipv4](#ip-switch-hash-ecmp-ipv4)
    - [ip switch-hash ecmp ipv6](#ip-switch-hash-ecmp-ipv6)
    - [ip switch-hash ecmp src-port](#ip-switch-hash-ecmp-src-port)
    - [ip switch-hash ecmp algorithm](#ip-switch-hash-ecmp-algorithm)
    - [ip switch-hash ecmp hash-seed](#ip-switch-hash-ecmp-hash-seed)
    - [ip switch-hash ecmp hash-offset](#ip-switch-hash-ecmp-hash-offset)
    - [ip switch-hash ecmp dst-queue-pair](#ip-switch-hash-ecmp-dst-queue-pair)
    - [show ip switch-hash ecmp brief](#show-ip-switch-hash-ecmp-brief)
    - [ip switch-hash lag ipv4](#ip-switch-hash-lag-ipv4)
    - [ip switch-hash lag ipv6](#ip-switch-hash-lag-ipv6)
    - [show ip switch-hash lag brief](#show-ip-switch-hash-lag-brief)
  - [MACSEC](#macsec)
    - [MACsec Config Commands](#macsec-config-commands)
    - [MACsec Clear commands](#macsec-clear-commands)
    - [MACsec Show commands](#macsec-show-commands)
    
## Document History
This section covers the change history in each release.

| Release | Date | Feature | Description |
| - | - | - | - |
| 1.0.0 | TBD | Industry standard CLI addition | Added commands to manage AAA, ACL, TACACS, RADIUS, NTP, Syslog, SNMP, Image management, Interface (Ethernet, Portchannel, VLAN, Loopback), L2(LLDP, MCLAG, FDB), Port security, CRM

## Introduction
This document is intended for system administrators to manage Celestica Enterprise SONiC using industry standard commands.

The following table lists the Advanced Celestica SONiC releases and the corresponding base community SONiC releases.
| **Advanced Celestica SONiC Release** | **Base Community SONiC Release** |
|:--------------------------------:|:-----------------------:|
| 1.0.0 | 202111 |
| 1.1.0 | 202111 |
| 2.0.0 | 202311 |

## Getting Started
Refer below public links to install SONiC image in ONIE, setup management IP address, SSH login to device, etc.

[Quick Start](https://github.com/sonic-net/SONiC/wiki/Quick-Start)

[SONIC-User-Manual](https://github.com/sonic-net/SONiC/blob/master/doc/SONiC-User-Manual.md)

### Login
Execute `sonic-cli` in admin user prompt to login into SONIC CLI interface. You will receive another prompt with `<hostname>#`
```
admin@sonic:~$ sonic-cli
sonic#
```

## Getting Help
Use `?` to list all available commands in any mode
```
sonic#
  configure  Enter configuration mode
  exit       Exit from the CLI
  image      Image related operations
  no         No commands under exec mode
  show       Show running system information
  system     System command

sonic#
```
```
sonic(config)#
  aaa             Configures AAA
  buffer-init     Platform based Default Qos buffer config
  end             Exit to EXEC mode
  exit            Exit from current mode
  feature         Configure feature commands
  hostname        Enter name of the host
  interface       Select an interface
  ip              Global IPv4 configuration commands
  ipv6            Global IPv6 configuration commands
  lldp            Configure lldp
  logging         Configures logging
  mac             Global MAC configuration commands
  mclag           Global mclag configuration commands
  mirror-session  Mirror session configuration
  no              Negate a command or set its defaults
  ntp             Configures NTP
  qos             Global QoS configuration commands
  radius-server   Configures RADIUS client
  sflow           Configure sFlow
  snmp-server     Configures SNMP server
  tacacs-server   Configures TACACS servers
  wred            Configures a weighted random early detection (WRED) profile

sonic(config)#
```

### Command Modes
SONIC CLI has two modes at top level.<br>
EXEC : This is the root mode, returned to the user initially. All troubleshooting, monitoring and status related commands are available.<br>
CONFIG : All configurations are grouped here which is accessible using `configure terminal` command in EXEC mode.<br>

### Auto completion
Use `TAB` or `SPACEBAR` to autocomplete partial commands and to list possible valid options.

### Common mode commands
Few commands are available in all modes for easy navigation.<br>
- `exit` - Navigate to previous mode. Executing `exit` from EXEC mode logout the SONIC CLI
- `end` - Goto EXEC mode
- `do` - EXEC mode commands are accessible from other modes via `do ` prefix. Examples : `do show running-config`, `do show version`

### Pipe options
Below post processing options are available to deal with show command output.<br>
Use the pipe symbol after the command `| ` to make use of pipes. Maximum 5 pipes are allowed in a single command.<br>
- `display-json [path <path-value>]` : Display the raw JSON output. Use the optional keyword `path` to filter based on JSON path expression.
- `except` : Filter lines not matching with regex pattern. Use `ignore-case` for case insensitive search.
- `grep` : Filter lines matching with regex pattern. Use `ignore-case` for case insensitive search.
- `find` : Search for the first occurence of a pattern and display all subsequent lines. Use `ignore-case` for case insensitive search.
- `no-more` : Display all lines without pagination
- `save` : Save the output to file inside mgmt-framework container. Use `append` to append on top of existing file. Files are stored in mgmt-framework docker. Use absolute path always. Relative path files are stored in `/home/cliadmin` directory.

```
sonic# show running-config |
  display-json  Show JSON content
  except        Show only text that does not match a pattern
  find          Search for the 1st occurrence of a pattern and display all the subsequent configs
  grep          Show only text that matches a pattern
  no-more       Don't paginate output
  save          Save output to a file

sonic# show running-config | display-json
  |     Pipe through a command
  <cr>

sonic# show running-config | display-json path $..bgp
  |     Pipe through a command
  <cr>

sonic# show running-config | except aaa
  ignore-case  Case insensitive
  |            Pipe through a command
  <cr>

sonic# show running-config | grep aaa
  ignore-case  Case insensitive
  |            Pipe through a command
  <cr>

sonic# show running-config | no-more
  |     Pipe through a command
  <cr>

sonic# show running-config | save /tmp/2.txt
  append  Append output
  |       Pipe through a command
  <cr>

sonic# show running-config | grep pattern1 | except pattern2 | find pattern3 | grep pattern4 | save /tmp/2.txt
  append  Append output
  |       Pipe through a command
  <cr>


```


## Basic Commands
#### terminal length
Set terminal length for the current session while displaying show command output.

**Syntax** : `terminal length <count>`

**Command mode** : EXEC

**Parameters** :
- `count` : Number of lines to be displayed (0 = disable pagination, default = 24)

**Usage** : Use this command to set terminal length

**Supported Releases** :  1.0.0 or later

**Click command** : None

**Example**
```
sonic# terminal length 20
sonic#
```
#### show terminal length
Displays the terminal length of the current session.

**Syntax** : `show terminal length`

**Command mode** : EXEC

**Usage** : Use this command to retrieve the terminal length of the current session

**Supported Releases** :  1.0.0 or later

**Click command** : None

**Example**
```
sonic# show terminal length
Current terminal length : 24 lines
sonic#
```

#### show running-config

Displays the active configuration on the device.

**Syntax** : `show running-config`

**Command mode** : EXEC

**Usage** : Use this command to retrieve the active configuration.

**Feature specific commands**
- Release 1.0.0
  - `show running-config aaa`
  - `show running-config interface [Ethernet <if-id> | Loopback <id> | PortChannel <id> | Vlan <>]`
  - `show running-config ip access-list [<name>]`
  - `show running-config ipv6 access-list [<name>]`
  - `show running-config lldp`
  - `show running-config logging`
  - `show running-config mac access-list [<name>]`
  - `show running-config mclag`
  - `show running-config mirror-session`
  - `show running-config ntp`
  - `show running-config qos map {dot1p-tc [<name>] | dscp-tc [<name>] | pfc-priority-queue [<name>] | tc-dot1p [<name>] | tc-dscp [<name>] | tc-pg [<name>] | tc-queue [<name>]}`
  - `show running-config qos scheduler-policy`
  - `show running-config qos wred-profile [<profile-name>]`
  - `show running-config radius`
  - `show running-config sflow`
  - `show running-config snmp`
  - `show running-config tacacs`
  - `show running-config telemetry`

**Supported Releases** :  1.0.0 or later

**Click command** : `show runningconfiguration all`

**Example**
```
sonic# show running-config
!
tacacs-server host 1.2.3.4 timeout 10
!
radius-server host 1.2.3.4 auth-port 1000
!
lldp enable
lldp system-description Test
lldp system-name test
lldp timer 20
no lldp tlv-select system-capabilities
!
ip access-list ip1
 seq 10 permit ip 10.1.1.1/24 10.1.1.2/24 dscp 10
!
ipv6 access-list ipv6_1
 seq 100 deny 47 100::1/64 100::2/64
!
mac access-list m1
 seq 80 deny any any 0x88cc
!
interface Vlan 40
 description vlan40
!
interface PortChannel 2
 description PortChannel2
 mtu 9100
 no shutdown
!
interface Ethernet 0
 description Eth0
 mtu 1500
 shutdown
 speed 40000
 no lldp enable
!
interface Ethernet 4
 description Ethernet4
 fec FC
 mtu 1700
 no shutdown
 speed auto
!
interface Ethernet 8
 description "Ethernet 8"
 fec none
 mtu 1500
 no shutdown
 speed auto
!
interface Ethernet 12
 mtu 9100
 no shutdown
 speed 40000
!
interface Ethernet 16
 description "ETHERNET 12"
 fec RS
 mtu 1500
 no shutdown
 speed 40000
 no lldp enable
--more--
```

#### show startup-config

Displays the startup configuration on the device.

**Syntax** : `show startup-config`

**Command mode** : EXEC

**Usage** : Use this command to retrieve the startup configuration.

**Supported Releases** :  1.0.0 or later

**Click command** : None

**Example**
```
sonic# show startup-config
!
tacacs-server host 1.2.3.4 timeout 10
!
radius-server host 1.2.3.4 auth-port 1000
!
lldp enable
lldp system-description Test
lldp system-name test
lldp timer 20
no lldp tlv-select system-capabilities
!
interface Vlan 40
 description vlan40
!
interface PortChannel 2
 mtu 9100
 no shutdown
!
interface Ethernet 0
 mtu 1500
 shutdown
 speed 40000
 no lldp enable
!
interface Ethernet 4
 fec FC
 mtu 1700
 no shutdown
 speed auto
!
interface Ethernet 8
 fec none
 mtu 1500
 no shutdown
 speed auto
!
interface Ethernet 12
 mtu 9100
 no shutdown
 speed 40000
!
interface Ethernet 16
 fec RS
 mtu 1500
 no shutdown
 speed 40000
 no lldp enable
--more--
```

###hostname
Configure system hostname

**Syntax**: `hostname <host_name>`

**Parameters**:
- `host_name` - String with max length of 64 and min length of 1. Does not accpet any special characters including whitespaces

**Command mode**: CONFIG

**Usage**: use `no hostname` to reset Hostname to default. Default Hostname is 'sonic'

**Supported Releases**:  1.0.0 or later

**Click Command**:
- `config hostname <new_hostname>`

**Example**:
```
sonic# configure terminal
sonic(config)# hostname mysystem
sonic(config)# exit
sonic# exit
admin@sonic:~$ sonic-cli
mysystem# configure terminal

mysystem(config)# no hostname
mysystem(config)# exit
mysystem# exit

admin@sonic:~$ sonic-cli
sonic#
```

###reboot
Reboot the switch

**Syntax**: `reboot`

**Parameters**:
- Not Applicable

**Command mode**: EXEC

**Usage**: Will reboot the entire switch

**Supported Releases**:  1.0.0 or later

**Click Command**:
- `reboot`

**Example**:

```
sonic# reboot
  <cr>

sonic# reboot
Success
admin@sonic:~$
```

####show history
Display current session's command history

**Syntax**: `show history [<lines>]`

**Parameters**:
- `lines` - Number of lines to be displayed from recent history, range 1 to 300.

**Command mode**: EXEC

**Supported Releases**:  1.0.0 or later

**Click commands**: None

**Example**:
```
sonic# show history
Index  Timestamp             Command
-----  ---------             -------
1      14-Jul-2023 05:20:27  configure terminal
2      14-Jul-2023 05:20:33  interface Vlan 10
3      14-Jul-2023 05:20:37  show config
4      14-Jul-2023 05:20:49  no interface Vlan 10
5      14-Jul-2023 05:20:59  do show vlan 10
6      14-Jul-2023 05:21:03  end
7      14-Jul-2023 05:21:06  show history
sonic# show history 4
Index  Timestamp             Command
-----  ---------             -------
5      14-Jul-2023 05:20:59  do show vlan 10
6      14-Jul-2023 05:21:03  end
7      14-Jul-2023 05:21:06  show history
8      14-Jul-2023 05:21:12  show history 4
sonic#
```

####show users
Display current active users

**Syntax**: `show users`

**Command mode**: EXEC

**Supported Releases**:  1.0.0 or later

**Click commands**:
`show users`

**Example**:
```
sonic# show users
------------------------------------------------------------------------------------------------
NAME            TERM_NO         DATE            TIME            IP-ADDR
------------------------------------------------------------------------------------------------
admin           pts/0           2023-03-07      09:02           (172.28.144.1)
admin           pts/1           2023-03-07      08:21           (172.28.144.1)

```

####show version
Display version of softwares, hardware and dockers

**Syntax**: `show version`

**Command mode**: EXEC

**Supported Releases**:  1.0.0 or later

**Click commands**:
`show version`

**Example**:
```
SONiC Software Version: SONiC.202111-CLS.0-ade5b1493
Distribution: Debian 11.6
Kernel: 5.10.0-8-2-amd64
Build commit: ade5b1493
Built by: vigneshs@AZUHPSP08
Platform: x86_64-kvm_x86_64-r0
HwSKU: Force10-S6000
ASIC: vs
ASIC Count: 1
Serial Number: N/A
Model Number: N/A
Hardware Revision: N/A
Uptime: 09:04:58 up  2:19,  2 users,  load average: 0.02, 0.09, 0.08
--------------------------------------------------------------------------------------
REPOSITORY                     TAG                       IMAGE-ID        SIZE
--------------------------------------------------------------------------------------
docker-database                202111-CLS.0-ade5b1493    ed018f07aa55    427MB
docker-database                latest                    ed018f07aa55    427MB
docker-dhcp-relay              latest                    7af4d5e8f0ea    440MB
docker-fpm-frr                 202111-CLS.0-ade5b1493    b02ae3a00657    460MB
docker-fpm-frr                 latest                    b02ae3a00657    460MB
docker-gbsyncd-vs              202111-CLS.0-ade5b1493    465f336c0acb    435MB
docker-gbsyncd-vs              latest                    465f336c0acb    435MB
docker-iccpd                   202111-CLS.0-ade5b1493    2473048535bc    442MB
docker-iccpd                   latest                    2473048535bc    442MB
docker-lldp                    202111-CLS.0-ade5b1493    55b0667ebc5e    467MB
docker-lldp                    latest                    55b0667ebc5e    467MB
docker-macsec                  202111-CLS.0-ade5b1493    78e4a9e82a10    444MB
docker-macsec                  latest                    78e4a9e82a10    444MB
docker-mux                     202111-CLS.0-ade5b1493    d6044577bff4    480MB
docker-mux                     latest                    d6044577bff4    480MB
docker-nat                     202111-CLS.0-ade5b1493    3f6157c4ad68    444MB
docker-nat                     latest                    3f6157c4ad68    444MB
docker-orchagent               202111-CLS.0-ade5b1493    1300337e52b9    460MB
docker-orchagent               latest                    1300337e52b9    460MB
docker-platform-monitor        202111-CLS.0-ade5b1493    09fd862251be    691MB
docker-platform-monitor        latest                    09fd862251be    691MB
docker-router-advertiser       202111-CLS.0-ade5b1493    d92c1c86611f    427MB
docker-router-advertiser       latest                    d92c1c86611f    427MB
docker-sflow                   202111-CLS.0-ade5b1493    3f6384eb0dfa    442MB
docker-sflow                   latest                    3f6384eb0dfa    442MB
docker-snmp                    202111-CLS.0-ade5b1493    25cc9835e1e7    471MB
docker-snmp                    latest                    25cc9835e1e7    471MB
docker-sonic-mgmt-framework    202111-CLS.0-ade5b1493    b35b951eea55    645MB
docker-sonic-mgmt-framework    latest                    b35b951eea55    645MB
docker-sonic-telemetry         202111-CLS.0-ade5b1493    dd9b1a2e7584    522MB
docker-sonic-telemetry         latest                    dd9b1a2e7584    522MB
docker-syncd-vs                202111-CLS.0-ade5b1493    5dd189b7cc8e    440MB
docker-syncd-vs                latest                    5dd189b7cc8e    440MB
docker-teamd                   202111-CLS.0-ade5b1493    3286bdc06cc4    441MB
docker-teamd                   latest                    3286bdc06cc4    441MB

```

####show reboot history
Display history of system reboots

**Syntax**: `show reboot history`

**Command mode**: EXEC

**Supported Releases**:  1.0.0 or later

**Click commands**:
`show reboot-cause history`
`show reboot history`

**Example**:
```
sonic# show reboot history
------------------------------------------------------------------------------------------------------
NAME                      CAUSE           TIME                                USER            COMMENT
------------------------------------------------------------------------------------------------------
2023_02_21_08_08_08       reboot          Tue 21 Feb 2023 08:07:25 AM UTC     admin           N/A
2023_02_22_11_17_52       Unknown         N/A                                 N/A             N/A
2023_02_23_04_14_41       Unknown         N/A                                 N/A             N/A
2023_02_23_08_01_06       Unknown         N/A                                 N/A             N/A
2023_02_27_04_55_26       Unknown         N/A                                 N/A             N/A
2023_02_28_04_58_17       Unknown         N/A                                 N/A             N/A
2023_03_01_04_19_24       Unknown         N/A                                 N/A             N/A
2023_03_03_04_47_29       Unknown         N/A                                 N/A             N/A
2023_03_06_05_23_09       Unknown         N/A                                 N/A             N/A
2023_03_07_06_45_39       Unknown         N/A                                 N/A             N/A

```

####show reboot-cause
Display cause of latest reboot

**Syntax**: `show reboot-cause`

**Command mode**: EXEC

**Supported Releases**:  1.0.0 or later

**Click commands**:
`show reboot-cause`

**Example**:
```
sonic# show reboot-cause
Unknown

```

####show environment
Display hardware status

**Syntax**: `show environment`

**Command mode**: EXEC

**Supported Releases**:  1.0.0 or later

**Click commands**:
`show environment`

**Example**:
```
sonic# show environment
acpitz-acpi-0
Adapter: ACPI interface
temp1:         +0.0 C  (crit = +94.0 C)
coretemp-isa-0000
Adapter: ISA adapter
Package id 0:  +28.0 C  (high = +74.0 C, crit = +94.0 C)
Core 2:        +25.0 C  (high = +74.0 C, crit = +94.0 C)
Core 6:        +26.0 C  (high = +74.0 C, crit = +94.0 C)
Core 8:        +25.0 C  (high = +74.0 C, crit = +94.0 C)
Core 12:       +26.0 C  (high = +74.0 C, crit = +94.0 C)

```

####show log
Display system log information

**Syntax**: `show log [pattern <pattern>] [lines <lines>]

**Parameters**:
- `pattern` - String pattern to search in system log. Accepts String of Max 32 characters
- `lines` - Number of lines to be Displayed. Accepts Integer of range 1 to 255. default number of lines = 50

**Command mode**: EXEC

**Supported Releases**:  1.0.0 or later

**Click commands**:
`show logging [OPTIONS] [PROCESS]`

**Example**:
```
sonic# show log pattern mgmt-framework lines 10
Mar  3 08:24:35.788112 sonic INFO mgmt-framework#/supervisord: rest-server I0303 08:24:35.787007      16 handler.go:48] [REST-7] GET /restconf/data/openconfig-system:system/openconfig-system-cls-ext:log/syslog_list="mgmt-framework",10; content-len=0
Mar  3 08:24:35.788273 sonic INFO mgmt-framework#/supervisord: rest-server I0303 08:24:35.787047      16 handler.go:56] [REST-7] Translated path = /openconfig-system:system/openconfig-system-cls-ext:log/syslog_list[process="mgmt-framework"][lines=10]
Mar  3 08:24:35.788342 sonic INFO mgmt-framework#/supervisord: rest-server I0303 08:24:35.787056      16 translib.go:491] Received Get request for path = /openconfig-system:system/openconfig-system-cls-ext:log/syslog_list[process="mgmt-framework"][lines=10]
Mar  3 08:24:35.788420 sonic INFO mgmt-framework#/supervisord: rest-server I0303 08:24:35.787063      16 app_interface.go:129] getAppModule called for path =/openconfig-system:system/openconfig-system-cls-ext:log/syslog_list[process="mgmt-framework"][lines=10]
Mar  3 08:24:35.789948 sonic INFO sonic-host-server: command: ['show', 'logging', '-l', '10', '"mgmt-framework"']
Mar  3 08:24:35.792408 sonic INFO mgmt-framework#/supervisord: rest-server I0303 08:24:35.787542      16 sys_app.go:93] SysApp: initialize:sys:path =/openconfig-system:system/openconfig-system-cls-ext:log/syslog_list[process="mgmt-framework"][lines=10]
Mar  3 08:24:35.792408 sonic INFO mgmt-framework#/supervisord: rest-server I0303 08:24:35.787601      16 sys_app.go:285] SysApp: translateGet:system:path =&{/openconfig-system:system/openconfig-system-cls-ext:log/syslog_list[process="mgmt-framework"][lines=10] /openconfig-system:system/openconfig-system-cls-ext:log/syslog_list{}{} map[lines:10 process:"mgmt-framework"]}
Mar  3 08:24:35.792408 sonic INFO mgmt-framework#/supervisord: rest-server I0303 08:24:35.787609      16 sys_app.go:641] SysApp: processGet Path: /openconfig-system:system/openconfig-system-cls-ext:log/syslog_list[process="mgmt-framework"][lines=10]
Mar  3 08:24:35.792408 sonic INFO mgmt-framework#/supervisord: rest-server I0303 08:24:35.787693      16 sys_app.go:644] Received GET for path /openconfig-system:system/openconfig-system-cls-ext:log/syslog_list[process="mgmt-framework"][lines=10]; template_info: /openconfig-system:system/openconfig-system-cls-ext:log/syslog_list{}{} vars=map[lines:10 process:"mgmt-framework"]
Mar  3 08:24:35.792408 sonic INFO mgmt-framework#/supervisord: rest-server I0303 08:24:35.787721      16 sys_app.go:656] targetUriPath : /openconfig-system:system/openconfig-system-cls-ext:log/syslog_list Args: map[lines:10 process:"mgmt-framework"]

sonic# show log lines 10
May 18 13:48:48.237992 sonic INFO mgmt-framework#/supervisord: rest-server I0518 13:48:48.235726      25 sys_app.go:713] Received GET for path /openconfig-system:system/openconfig-system-cls-ext:log/syslog[process=All][lines=10]; template_info: /openconfig-system:system/openconfig-system-cls-ext:log/syslog{}{} vars=map[lines:10 process:All]
May 18 13:48:48.238133 sonic INFO mgmt-framework#/supervisord: rest-server I0518 13:48:48.235875      25 sys_app.go:725] targetUriPath : /openconfig-system:system/openconfig-system-cls-ext:log/syslog Args: map[lines:10 process:All]
May 18 13:48:48.238273 sonic INFO mgmt-framework#/supervisord: rest-server I0518 13:48:48.236041      25 sys_app.go:922] Handeling logging Get process
May 18 13:48:48.238414 sonic INFO mgmt-framework#/supervisord: rest-server I0518 13:48:48.236055      25 sys_log.go:25] Handleing Getlog Function
May 18 13:48:48.238792 sonic INFO mgmt-framework#/supervisord: rest-server I0518 13:48:48.236070      25 sys_log.go:28] Building Log empty tree
May 18 13:48:48.238936 sonic INFO mgmt-framework#/supervisord: rest-server I0518 13:48:48.236083      25 sys_log.go:80] get logAll info using dbus entry
May 18 13:48:48.239076 sonic INFO mgmt-framework#/supervisord: rest-server I0518 13:48:48.236098      25 host_comm.go:20] HostQuery called
May 18 13:48:48.239213 sonic INFO mgmt-framework#/supervisord: rest-server I0518 13:48:48.236110      25 host_comm.go:35] HostQueryAsync called on endpoint 'system_mgmt.show'
May 18 13:48:48.239351 sonic INFO mgmt-framework#/supervisord: rest-server I0518 13:48:48.236126      25 host_comm.go:42] HostQueryAsync conn established
May 18 13:48:48.239490 sonic INFO mgmt-framework#/supervisord: rest-server I0518 13:48:48.236161      25 host_comm.go:71] HostQueryAsync Before objgo

```

####show uptime
Display time since the system has been up

**Syntax**: `show uptime`

**Command mode**: EXEC

**Supported Releases**:  1.0.0 or later

**Click commands**:
`show uptime`

**Example**:
```
sonic# show uptime
up 2 hours, 32 minutes

```

####show services
Display system services and their process information

**Syntax**: `show services`

**Command mode**: EXEC

**Supported Releases**:  1.0.0 or later

**Click command**:
- `show services`

**Example**:
```

sonic# show services
--------------------------------------------------------------------
bgp                 docker
--------------------------------------------------------------------
User                Pid  %Cpu %Memory   VSZ       RSS       TTY       Stat      Start     Time      Command
root                1    0.0  0.2       30396     24184     pts/0     Ss+       04:52     0:02      /usr/bin/python3 /usr/local/bin/supervisord
root                28   0.0  0.2       25620     19100     pts/0     S         04:52     0:00      python3 /usr/bin/supervisor-proc-exit-listener --container-name bgp
root                31   0.0  0.0       223808    5580      pts/0     Sl        04:52     0:00      /usr/sbin/rsyslogd -n -iNONE
frr                 35   0.0  0.7       675496    61524     pts/0     Sl        04:52     0:02      /usr/lib/frr/zebra -A 127.0.0.1 -s 90000000 -M fpm -M snmp
frr                 55   0.0  0.1       43896     12740     pts/0     S         04:52     0:00      /usr/lib/frr/staticd -A 127.0.0.1
frr                 56   0.0  0.5       295544    44768     pts/0     Sl        04:52     0:07      /usr/lib/frr/bgpd -A 127.0.0.1 -M snmp
root                58   0.0  0.3       37584     26156     pts/0     S         04:52     0:00      /usr/bin/python3 /usr/local/bin/bgpcfgd
root                59   0.0  0.1       19968     15492     pts/0     S         04:52     0:01      /usr/bin/python3 /usr/local/bin/bgpmon
root                60   0.0  0.0       82184     4488      pts/0     Sl        04:52     0:00      fpmsyncd
--------------------------------------------------------------------
database            docker
--------------------------------------------------------------------
User                Pid  %Cpu %Memory   VSZ       RSS       TTY       Stat      Start     Time      Command
root                1    0.0  0.2       29996     23616     pts/0     Ss+       04:52     0:01      /usr/bin/python3 /usr/local/bin/supervisord
root                35   0.0  0.2       25612     19028     pts/0     S         04:52     0:00      python3 /usr/bin/supervisor-proc-exit-listener --container-name database
root                36   0.0  0.0       223808    3576      pts/0     Sl        04:52     0:00      /usr/sbin/rsyslogd -n -iNONE
root                37   0.3  0.6       100592    52024     pts/0     Sl        04:52     0:29      /usr/bin/redis-server 127.0.0.1:6379
--------------------------------------------------------------------
gbsyncd             docker
--------------------------------------------------------------------
User                Pid  %Cpu %Memory   VSZ       RSS       TTY       Stat      Start     Time      Command
root                1    0.0  0.2       30256     24064     pts/0     Ss+       04:52     0:01      /usr/bin/python3 /usr/local/bin/supervisord
root                10   0.0  0.2       25612     19064     pts/0     S         04:52     0:00      python3 /usr/bin/supervisor-proc-exit-listener --container-name gbsyncd
root                13   0.0  0.0       223808    3576      pts/0     Sl        04:52     0:00      /usr/sbin/rsyslogd -n -iNONE
--------------------------------------------------------------------
lldp                docker
--------------------------------------------------------------------
User                Pid  %Cpu %Memory   VSZ       RSS       TTY       Stat      Start     Time      Command
root                1    0.0  0.2       30388     24108     pts/0     Ss+       04:52     0:02      /usr/bin/python3 /usr/local/bin/supervisord
root                12   0.0  0.2       25616     19012     pts/0     S         04:52     0:00      python3 /usr/bin/supervisor-proc-exit-listener --container-name lldp
root                15   0.0  0.0       223808    3412      pts/0     Sl        04:52     0:00      /usr/sbin/rsyslogd -n -iNONE
_lldpd              23   0.0  0.0       28364     7716      pts/0     S         04:52     0:00      lldpd: monitor.
_lldpd              25   0.0  0.0       28492     3756      pts/0     S         04:52     0:01      lldpd: no neighbor.
root                29   0.0  0.2       105000    21504     pts/0     Sl        04:52     0:01      python3 -m lldp_syncd
root                33   0.0  0.1       24452     15752     pts/0     S         04:52     0:00      python3 /usr/bin/lldpmgrd
--------------------------------------------------------------------
mgmt-framework      docker
--------------------------------------------------------------------
User                Pid  %Cpu %Memory   VSZ       RSS       TTY       Stat      Start     Time      Command
root                1    0.0  0.2       29116     22792     pts/0     Ss+       06:30     0:00      /usr/bin/python3 /usr/local/bin/supervisord
root                13   0.0  0.0       223808    3420      pts/0     Sl        06:30     0:00      /usr/sbin/rsyslogd -n -iNONE
root                17   0.2  2.7       1397164   225716    pts/0     Sl        06:30     0:04      /usr/sbin/rest_server -ui /rest_ui -logtostderr -cert /tmp/cert.pem -key /tmp/key.pem
1000                58   0.0  0.0       3736      2708      pts/1     Ss+       06:32     0:00      /bin/bash /usr/sbin/cli/clish_start -t 3605
1000                64   0.0  0.4       157124    40328     pts/1     S+        06:32     0:00      /usr/sbin/cli/clish -o -t 3605
1000                76   0.0  0.0       3736      2788      pts/2     Ss+       07:02     0:00      /bin/bash /usr/sbin/cli/clish_start -t 3605
1000                82   1.3  0.3       144248    26032     pts/2     S+        07:02     0:00      /usr/sbin/cli/clish -o -t 3605
--------------------------------------------------------------------
pmon                docker
--------------------------------------------------------------------
User                Pid  %Cpu %Memory   VSZ       RSS       TTY       Stat      Start     Time      Command
root                1    0.0  0.3       30308     24252     pts/0     Ss+       04:52     0:01      /usr/bin/python3 /usr/local/bin/supervisord
root                21   0.0  0.2       25636     19156     pts/0     S         04:52     0:00      python3 /usr/bin/supervisor-proc-exit-listener --container-name pmon
root                24   0.0  0.0       223808    3608      pts/0     Sl        04:52     0:00      /usr/sbin/rsyslogd -n -iNONE
--------------------------------------------------------------------
radv                docker
--------------------------------------------------------------------
User                Pid  %Cpu %Memory   VSZ       RSS       TTY       Stat      Start     Time      Command
root                1    0.0  0.2       30256     24020     pts/0     Ss+       04:52     0:01      /usr/bin/python3 /usr/local/bin/supervisord
root                13   0.0  0.2       25612     19048     pts/0     S         04:52     0:00      python3 /usr/bin/supervisor-proc-exit-listener --container-name radv
root                17   0.0  0.0       223808    3596      pts/0     Sl        04:52     0:00      /usr/sbin/rsyslogd -n -iNONE
--------------------------------------------------------------------
snmp                docker
--------------------------------------------------------------------
User                Pid  %Cpu %Memory   VSZ       RSS       TTY       Stat      Start     Time      Command
root                1    0.0  0.3       33644     24304     pts/0     Ss+       04:55     0:02      /usr/bin/python3 /usr/local/bin/supervisord
root                10   0.0  0.2       29060     19352     pts/0     S         04:55     0:00      python3 /usr/bin/supervisor-proc-exit-listener --container-name snmp
root                18   0.0  0.0       223808    3340      pts/0     Sl        04:55     0:00      /usr/sbin/rsyslogd -n -iNONE
Debian-+            22   0.0  0.1       30868     12360     pts/0     S         04:55     0:03      /usr/sbin/snmpd -f -LS0-2d -u Debian-snmp -g Debian-snmp -I -smux mteTrigger mteTriggerConf ifTable ifXTable inetCidrRouteTable ipCidrRouteTable ip disk_hw -p /run/snmpd.pid
root                23   0.0  0.3       120552    32192     pts/0     Sl        04:55     0:02      python3 -m sonic_ax_impl
--------------------------------------------------------------------
swss                docker
--------------------------------------------------------------------
User                Pid  %Cpu %Memory   VSZ       RSS       TTY       Stat      Start     Time      Command
root                1    0.0  0.2       30724     24212     pts/0     Ss+       04:52     0:04      /usr/bin/python3 /usr/local/bin/supervisord
root                109  0.0  0.1       88412     8116      pts/0     Sl        04:52     0:00      /usr/bin/tunnelmgrd
root                2547 0.0  0.0       2524      740       pts/0     S         06:57     0:00      sleep 300
root                28   0.0  0.2       25620     19044     pts/0     S         04:52     0:00      python3 /usr/bin/supervisor-proc-exit-listener --container-name swss
root                31   0.0  0.0       223808    5900      pts/0     Sl        04:52     0:00      /usr/sbin/rsyslogd -n -iNONE
root                36   0.0  0.0       81256     5300      pts/0     Sl        04:52     0:00      /usr/bin/portsyncd
root                43   0.3  0.2       402896    20292     pts/0     Sl        04:52     0:25      /usr/bin/orchagent -d /var/log/swss -b 8192 -s -m 52:54:00:12:34:56
root                472  0.0  0.0       5668      1628      pts/0     S         04:52     0:00      /usr/sbin/ndppd
root                59   0.0  0.1       88504     8268      pts/0     Sl        04:52     0:00      /usr/bin/coppmgrd
root                81   0.0  0.0       3964      3016      pts/0     S         04:52     0:00      /bin/bash /usr/bin/arp_update
root                83   0.0  0.0       81124     4436      pts/0     Sl        04:52     0:02      /usr/bin/neighsyncd
root                85   0.0  0.1       88304     8236      pts/0     Sl        04:52     0:00      /usr/bin/fdbmgrd
root                87   0.0  0.1       88444     8384      pts/0     Sl        04:52     0:00      /usr/bin/vlanmgrd
root                88   0.0  0.1       88588     8700      pts/0     Sl        04:52     0:00      /usr/bin/intfmgrd
root                89   0.0  0.1       88408     10424     pts/0     Sl        04:52     0:00      /usr/bin/portmgrd
root                90   0.0  0.1       88500     8348      pts/0     Sl        04:52     0:00      /usr/bin/buffermgrd -l /usr/share/sonic/hwsku/pg_profile_lookup.ini
root                92   0.0  0.1       88440     8440      pts/0     Sl        04:52     0:00      /usr/bin/vrfmgrd
root                93   0.0  0.1       88336     8180      pts/0     Sl        04:52     0:00      /usr/bin/nbrmgrd
root                94   0.0  0.1       88464     8316      pts/0     Sl        04:52     0:00      /usr/bin/vxlanmgrd
root                96   0.0  0.0       81168     4800      pts/0     Sl        04:52     0:01      /usr/bin/fdbsyncd
--------------------------------------------------------------------
syncd               docker
--------------------------------------------------------------------
User                Pid  %Cpu %Memory   VSZ       RSS       TTY       Stat      Start     Time      Command
root                1    0.0  0.2       30256     23984     pts/0     Ss+       04:52     0:02      /usr/bin/python3 /usr/local/bin/supervisord
root                10   0.0  0.2       25612     19040     pts/0     S         04:52     0:00      python3 /usr/bin/supervisor-proc-exit-listener --container-name syncd
root                13   0.0  0.1       223808    9820      pts/0     Sl        04:52     0:00      /usr/sbin/rsyslogd -n -iNONE
root                20   0.0  0.2       732848    20916     pts/0     Sl        04:52     0:04      /usr/bin/syncd -u -s -p /usr/share/sonic/hwsku/sai.profile
--------------------------------------------------------------------
teamd               docker
--------------------------------------------------------------------
User                Pid  %Cpu %Memory   VSZ       RSS       TTY       Stat      Start     Time      Command
root                1    0.0  0.2       30260     23948     pts/0     Ss+       04:52     0:01      /usr/bin/python3 /usr/local/bin/supervisord
root                10   0.0  0.2       25612     19052     pts/0     S         04:52     0:00      python3 /usr/bin/supervisor-proc-exit-listener --container-name teamd
root                16   0.0  0.0       223808    3604      pts/0     Sl        04:52     0:00      /usr/sbin/rsyslogd -n -iNONE
root                20   0.0  0.1       88440     8256      pts/0     Sl        04:52     0:00      /usr/bin/teammgrd
root                21   0.0  0.0       88208     7144      pts/0     Sl        04:52     0:04      /usr/bin/tlm_teamd
root                27   0.0  0.0       16076     3116      ?         S         04:52     0:03      /usr/bin/teamd -r -t PortChannel1 -c {"device":"PortChannel1","hwaddr":"52:54:00:12:34:56","runner":{"active":true,"name":"lacp","min_ports":1}} -L /var/warmboot/teamd/ -g -d
root                33   0.0  0.0       81500     5128      pts/0     Sl        04:52     0:00      /usr/bin/teamsyncd
root                36   0.0  0.0       16072     3308      ?         S         04:52     0:02      /usr/bin/teamd -r -t PortChannel2 -c {"device":"PortChannel2","hwaddr":"52:54:00:12:34:56","runner":{"active":true,"name":"lacp","min_ports":1}} -L /var/warmboot/teamd/ -g -d
root                45   0.0  0.0       15964     2648      ?         S         04:52     0:01      /usr/bin/teamd -r -t PortChannel3 -c {"device":"PortChannel3","hwaddr":"52:54:00:12:34:56","runner":{"active":true,"name":"lacp","min_ports":1}} -L /var/warmboot/teamd/ -g -d
--------------------------------------------------------------------
telemetry           docker
--------------------------------------------------------------------
User                Pid  %Cpu %Memory   VSZ       RSS       TTY       Stat      Start     Time      Command
root                1    0.0  0.2       30256     24136     pts/0     Ss+       04:55     0:02      /usr/bin/python3 /usr/local/bin/supervisord
root                12   0.0  0.0       223808    5476      pts/0     Sl        04:55     0:00      /usr/sbin/rsyslogd -n -iNONE
root                18   0.2  0.8       1177232   71180     pts/0     Sl        04:55     0:20      /usr/sbin/telemetry -logtostderr --noTLS --port 8080 --allow_no_client_auth -v=2
root                41   0.2  0.9       1174316   75768     pts/0     Sl        04:55     0:20      /usr/sbin/dialout_client_cli -insecure -logtostderr -v 2
root                9    0.0  0.2       25612     19068     pts/0     S         04:55     0:00      python3 /usr/bin/supervisor-proc-exit-listener --container-name telemetry

```

#### show clock
Displays the current system clock in UTC.

**Syntax** : `show clock`

**Command mode** : EXEC

**Usage** : None

**Supported Releases** :  1.0.0 or later

**Click command** : `show clock`

**Example**
```
sonic# show clock
Mon 03 Mar 2023 15:13:13 PM UTC
sonic#

```

#### show techsupport
Gathers and compresses information into an archive

**Syntax** : `show techsupport [since <date>] [global-timeout <global-timeout value>] [cmd-timeout <cmd-timeout value>] [verbose] [allow-process-stop] [silent] [debug-dump] [redirect-stderr]`

**Command mode** : EXEC

**Parameters** :
- `since` : Collect logs and core files since a specified date/time. Format : "DD Month YYYY" Eg : "15 May 2023"
- `global-timeout` : Global timeout in minutes.Default 30 mins.  Range : 10-120
- `cmd-timeout` : Individual command timeout in minutes.Default 5 mins. Range : 1-30
- `verbose` : Enable verbose output
- `allow-process-stop` : Dump additional data which may require system interruption
- `silent` : Run techsupport in silentmode`
- `debug-dump` : Collect Debug Dump Output
- `redirect-stderr` : Redirect an intermediate errors to STDERR

**Usage** : Troubleshooting

**Supported Releases** :  1.0.0 or later

**Click command** : `show techsupport`

**Example**:
```
sonic# show techsupport since "15 May 2023"
%Info Use show techsupport status for techsupport progress
sonic#

```

#### show techsupport status
Display the current state for show techsupport command

**Syntax** : `show techsupport status`

**Command mode** : EXEC

**Usage** : Checking the progress of techsupport 

**Supported Releases** :  1.0.0 or later

**Click command** : `None`

**Example**:
```
sonic# show techsupport status
                      Techsupport Status
------------------------------------------------------------
Status      : Completed
Filename    : /var/dump/sonic_dump_sonic_20230531_092859.tar.gz
sonic#

```
#### show interface autoneg status
Display the statue of autoneg state for Ethernet interfaces 

**Syntax** : `show interface autoneg status [Ethernet <interface-id>]`

**Command mode** : EXEC

**Usage** : For Ethernet ports, display the statue of the autoneg state. 

**Supported Releases** :  1.0.0 or later

**Click command** : `show interfaces autoneg status`

**Example**:
```
admin@sonic:~$ sonic-cli
sonic# show interface autoneg status
------------------------------------------------------------------------------------------------------------
Name                Admin     Oper      Speed     autoneg   Type      Adv Speeds     Adv Types
------------------------------------------------------------------------------------------------------------
Ethernet0           up        down      40GB      N/A       N/A       N/A            N/A
Ethernet4           up        down      40GB      N/A       N/A       N/A            N/A
Ethernet8           up        down      40GB      N/A       N/A       N/A            N/A
Ethernet12          up        down      40GB      N/A       N/A       N/A            N/A
Ethernet16          up        down      40GB      N/A       N/A       N/A            N/A
Ethernet20          up        down      40GB      N/A       N/A       N/A            all
Ethernet24          up        down      40GB      disabled  N/A       N/A            N/A
Ethernet28          up        down      40GB      N/A       N/A       N/A            N/A
Ethernet32          up        down      40GB      N/A       N/A       N/A            N/A
Ethernet36          up        down      40GB      N/A       N/A       N/A            N/A
Ethernet40          up        down      40GB      N/A       N/A       N/A            N/A
Ethernet44          up        down      40GB      enabled   N/A       N/A            N/A
Ethernet48          up        down      40GB      N/A       N/A       all            N/A
Ethernet52          up        down      40GB      N/A       N/A       N/A            N/A
Ethernet56          up        down      40GB      N/A       N/A       N/A            N/A
Ethernet60          up        down      40GB      N/A       N/A       N/A            N/A
Ethernet64          up        down      40GB      N/A       N/A       N/A            N/A
Ethernet68          up        down      40GB      N/A       N/A       N/A            N/A
Ethernet72          up        down      40GB      N/A       N/A       N/A            N/A
Ethernet76          up        down      40GB      N/A       N/A       N/A            N/A
Ethernet80          up        down      40GB      N/A       N/A       N/A            N/A
Ethernet84          up        down      40GB      N/A       N/A       10G,20G        N/A
Ethernet88          up        down      40GB      N/A       N/A       N/A            N/A
Ethernet92          up        down      40GB      N/A       N/A       N/A            N/A
Ethernet96          up        down      40GB      N/A       N/A       N/A            N/A
Ethernet100         up        down      40GB      N/A       CR        N/A            N/A
Ethernet104         up        down      40GB      N/A       CR2       N/A            N/A
Ethernet108         up        down      40GB      N/A       N/A       N/A            N/A
Ethernet112         up        down      40GB      N/A       N/A       N/A            N/A
Ethernet116         up        down      40GB      N/A       N/A       N/A            N/A
Ethernet120         up        down      40GB      N/A       N/A       N/A            N/A
Ethernet124         up        down      40GB      N/A       N/A       N/A            N/A
sonic#
```
###platform show commands
#### show interface fec status
Display the status of fec state for Ethernet interfaces 

**Syntax** : `show interface fec status`

**Command mode** : EXEC

**Usage** : For Ethernet ports, display the statue of the fec state. 

**Supported Releases** :  4.0.0 or later

**Click command** : `show interfaces fec status`

**Example**:
```
admin@sonic:~$ sonic-cli
Celestica-DS1000# show interface fec status
---------------------------------------------------------------------------------
Interface           FEC Oper  FEC Admin
---------------------------------------------------------------------------------
Ethernet0           N/A       DISABLED
Ethernet1           N/A       RS
Ethernet2           N/A       DISABLED
Ethernet3           N/A       DISABLED
Ethernet4           N/A       DISABLED
Ethernet5           N/A       DISABLED
Ethernet6           N/A       DISABLED
Ethernet7           N/A       DISABLED
Ethernet8           N/A       DISABLED
Ethernet9           N/A       DISABLED
Ethernet10          N/A       DISABLED
Ethernet11          N/A       DISABLED
Ethernet12          N/A       DISABLED
Ethernet13          N/A       DISABLED
Ethernet14          N/A       DISABLED
Ethernet15          N/A       DISABLED
Ethernet16          N/A       DISABLED
Ethernet17          N/A       DISABLED
Ethernet18          N/A       DISABLED
Ethernet19          N/A       DISABLED
Ethernet20          N/A       DISABLED
Ethernet21          N/A       DISABLED
Ethernet22          N/A       DISABLED
Ethernet23          N/A       DISABLED
Ethernet24          N/A       DISABLED
Ethernet25          N/A       DISABLED
Ethernet26          N/A       DISABLED
Ethernet27          N/A       DISABLED
Ethernet28          N/A       DISABLED
Ethernet29          N/A       DISABLED
Ethernet30          N/A       DISABLED
Ethernet31          N/A       DISABLED
Ethernet32          N/A       DISABLED
Ethernet33          N/A       DISABLED
Ethernet34          N/A       DISABLED
Ethernet35          N/A       DISABLED
Ethernet36          N/A       DISABLED
Ethernet37          N/A       DISABLED
Ethernet38          N/A       DISABLED
Ethernet39          N/A       DISABLED
Ethernet40          N/A       DISABLED
Ethernet41          N/A       DISABLED
Ethernet42          N/A       DISABLED
Ethernet43          N/A       DISABLED
Ethernet44          N/A       DISABLED
Ethernet45          N/A       DISABLED
Ethernet46          N/A       DISABLED
Ethernet47          N/A       DISABLED
Ethernet48          N/A       DISABLED
Ethernet49          N/A       DISABLED
Ethernet50          N/A       DISABLED
Ethernet51          N/A       DISABLED
Ethernet52          N/A       DISABLED
Ethernet53          N/A       DISABLED
Ethernet54          N/A       DISABLED
Ethernet55          N/A       DISABLED

```
#### show interface link-training status
Display the status of link-training state for Ethernet interfaces 

**Syntax** : `show interface link-training status`

**Command mode** : EXEC

**Usage** : For Ethernet ports, display the statue of the fec state. 

**Supported Releases** :  4.0.0 or later

**Click command** : `show interfaces link-training status`

**Example**:
```
admin@Celestica-DS1000:~$ sonic-cli
Celestica-DS1000# show interface link-training status
-----------------------------------------------------------------------------------------------------------------------------------------------
Interface           LT Oper   LT Admin  Oper      Admin
-----------------------------------------------------------------------------------------------------------------------------------------------
Ethernet0           N/A       N/A       DOWN      UP
Ethernet1           off       off       DOWN      UP
Ethernet2           N/A       N/A       DOWN      UP
Ethernet3           N/A       N/A       DOWN      UP
Ethernet4           N/A       N/A       DOWN      UP
Ethernet5           N/A       N/A       DOWN      UP
Ethernet6           N/A       N/A       DOWN      UP
Ethernet7           N/A       N/A       DOWN      UP
Ethernet8           N/A       N/A       DOWN      UP
Ethernet9           N/A       N/A       DOWN      UP
Ethernet10          N/A       N/A       DOWN      UP
Ethernet11          off       off       DOWN      UP
Ethernet12          N/A       N/A       DOWN      UP
Ethernet13          N/A       N/A       DOWN      UP
Ethernet14          N/A       N/A       DOWN      UP
Ethernet15          N/A       N/A       DOWN      UP
Ethernet16          N/A       N/A       DOWN      UP
Ethernet17          N/A       N/A       DOWN      UP
Ethernet18          N/A       N/A       DOWN      UP
Ethernet19          N/A       N/A       DOWN      UP
Ethernet20          N/A       N/A       DOWN      UP
Ethernet21          N/A       N/A       DOWN      UP
Ethernet22          N/A       N/A       DOWN      UP
Ethernet23          N/A       N/A       DOWN      UP
Ethernet24          N/A       N/A       DOWN      UP
Ethernet25          N/A       N/A       DOWN      UP
Ethernet26          N/A       N/A       DOWN      UP
Ethernet27          N/A       N/A       DOWN      UP
Ethernet28          N/A       N/A       DOWN      UP
Ethernet29          N/A       N/A       DOWN      UP
Ethernet30          N/A       N/A       DOWN      UP
Ethernet31          N/A       N/A       DOWN      UP
Ethernet32          N/A       N/A       DOWN      UP
Ethernet33          N/A       N/A       DOWN      UP
Ethernet34          N/A       N/A       DOWN      UP
Ethernet35          N/A       N/A       DOWN      UP
Ethernet36          N/A       N/A       DOWN      UP
Ethernet37          N/A       N/A       DOWN      UP
Ethernet38          N/A       N/A       DOWN      UP
Ethernet39          N/A       N/A       DOWN      UP
Ethernet40          N/A       N/A       DOWN      UP
Ethernet41          N/A       N/A       DOWN      UP
Ethernet42          N/A       N/A       DOWN      UP
Ethernet43          N/A       N/A       DOWN      UP
Ethernet44          N/A       N/A       DOWN      UP
Ethernet45          N/A       N/A       DOWN      UP
Ethernet46          N/A       N/A       DOWN      UP
Ethernet47          N/A       N/A       DOWN      UP
Ethernet48          N/A       N/A       DOWN      UP
Ethernet49          N/A       N/A       DOWN      UP
Ethernet50          N/A       N/A       DOWN      UP
Ethernet51          N/A       N/A       DOWN      UP
Ethernet52          N/A       N/A       DOWN      UP
Ethernet53          N/A       N/A       DOWN      UP
Ethernet54          N/A       N/A       DOWN      UP
Ethernet55          N/A       N/A       DOWN      UP

```
####psustatus
Display platform PSU information

**Syntax**: `show platform psustatus`

**Command mode**: EXEC

**Supported Releases**: 1.0.0 or later

**Click command**: 
- `show platform psustatus`

**Example**:
```

sonic# show platform psustatus
PSU       Model          Serial No      Hw Revision    Voltage(V)  Current(A)  Power(W)  Status    Led
---------------------------------------------------------------------------------------------------------
PSU 1     FSP550-20FM     S2161000595   N/A            0.0         0.0         0.0       NOT OK    amber
PSU 2     FSP550-20FM     S2161000587   N/A            12.119      3.015       38.5      OK        green

```

####fan
Display platform fan information

**Syntax**: `show platform fan`

**Command mode**: EXEC

**Supported Releases**: 1.0.0 or later

**Click command**: 
- `show platform fan`

**Example**:
```

sonic# show platform fan
Drawer    Led       Fan            Speed(%)  Direction      Presence       Status    Timestamp
---------------------------------------------------------------------------------------------------------
Fantray1  green     Fantray1_1     40        EXHAUST        True           True      20230320 07:30:26
Fantray2  green     Fantray2_1     40        EXHAUST        True           True      20230320 07:30:26
Fantray3  green     Fantray3_1     40        EXHAUST        True           True      20230320 07:30:26
N/A       green     PSU1_FAN1      25        EXHAUST        True           True      20230320 07:30:26
N/A       green     PSU2_FAN1      11        INTAKE         True           True      20230320 07:30:27

```

####temperature
Display platform sensor temperature information

**Syntax**: `show platform temperature`

**Command mode**: EXEC

**Supported Releases**: 1.0.0 or later

**Click command**: 
- `show platform temperature`

**Example**:
```

sonic# show platform temperature
Sensor                        Temperature(C)  High TH(C)  Low TH(C)   Crit High TH(C)  Crit Low TH(C)   Warning   Timestamp
-----------------------------------------------------------------------------------------------------------------------------------
BCM inlet U60 temp            33.5            100.0       N/A         105.0            N/A              False     20230413 13:14:18
CPU core temp                 31.0            88.0        N/A         91.0             N/A              False     20230413 13:14:18
Inlet U10 temp (EXHAUST)      30.0            50.0        N/A         N/A              N/A              False     20230413 13:14:18
Inlet U4 temp (EXHAUST)       25.0            50.0        N/A         N/A              N/A              False     20230413 13:14:18
Inlet U7 temp (INTAKE)        27.0            50.0        N/A         N/A              N/A              False     20230413 13:14:18
PSU1_TEMP1                    22.0            62          N/A         N/A              N/A              False     20230413 13:14:18
PSU2_TEMP1                    30.0            62          N/A         N/A              N/A              False     20230413 13:14:19

```

####syseeprom
Display platform eeprom information

**Syntax**: `show platform syseeprom`

**Command mode**: EXEC

**Supported Releases**: 1.0.0 or later

**Click command**: 
- `show platform syseeprom`

**Example**:
```

TLV Name            Code      Length    Value
------------------------------------------------------------
Product Name        0x21      5         E1070
Part Number         0x22      14        R3059-F9010-01
Serial Number       0x23      22        E1070F2B063203GD200151
Base MAC Address    0x24      6         34:AD:61:F1:B4:47
Manufacture Date    0x25      19        08/02/2023 03:58:14
Device Version      0x26      1         6
Label Revision      0x27      7         Belgite
Platform Name       0x28      21        x86_64-cel_belgite-r0
ONIE Version        0x29      5         2.0.0
MAC Addresses       0x2a      2         57
Manufacturer        0x2b      9         Celestica
Manufacture Country 0x2c      3         THA
Vendor Name         0x2d      9         Celestica
Diag Version        0x2e      5         3.2.0
Service Tag         0x2f      2         LB
CRC-32              0xfe      4         0xBAD5C8FD

```

####firmware
Display platform firmware information

**Syntax**: `show platform firmware status` 

**Command mode**: EXEC

**Supported Releases**: 1.0.0 or later

**Click command**: 
- `show platform firmware status`

**Example**:
```

sonic# show platform firmware status
Chassis   Module    Component      Version                  Description
----------------------------------------------------------------------------------------------------
E1070     N/A       BIOS           COMe-Dnvt.3.01.00_B      Basic Input/Output System
                    ONIE           2019.02.01.2.0.0         Open Network Install Environment
                    SSD            L20B12i                  Solid State Drive - M.2 (S80) 3IE4
                    SWCPLD         2.6                      For managing the chassis and SFP+ ports (49-56)

```

####ssdhealth
Display platform storage information

**Syntax**: `show platform ssdhealth`

**Command mode**: EXEC

**Supported Releases**: 1.0.0 or later

**Click command**: 
- `show platform ssdhealth`

**Example**:
```

sonic# show platform ssdhealth
Device Model : M.2 (S80) 3IE4
Health       : 99.905%
Temperature  : 32C

```

####summary
Display platform chassis information

**Syntax**: `show platform summary`

**Command mode**: EXEC

**Supported Releases**: 1.0.0 or later

**Click command**: 
- `show platform summary`

**Example**:
```

sonic# show platform summary
Platform          : x86_64-cel_belgite-r0
HwSKU             : CELESTICA-BELGITE
ASIC              : broadcom
ASIC Count        : 1
Serial Number     : E1070F2B063203GD200158
Model Number      : R3059-F9010-01
Hardware Revision : 6

```

####pcieinfo
Display PCIe information

**Syntax**: `show platform pcieinfo`

**Command mode**: EXEC

**Supported Releases**: 1.0.0 or later

**Click command**: 
- `show platform pcieinfo`

**Example**:
```

Bus  Device Function  Id        Name
----------------------------------------------------------------------
00   00     0         0x1980    Host bridge: Intel Corporation Atom Processor C3000 Series System Agent (rev 11)
00   04     0         0x19a1    Host bridge: Intel Corporation Atom Processor C3000 Series Error Registers (rev 11)
00   05     0         0x19a2    Generic system peripheral [0807]: Intel Corporation Atom Processor C3000 Series Root Complex Event Collector (rev 11)
00   06     0         0x19a3    PCI bridge: Intel Corporation Atom Processor C3000 Series Integrated QAT Root Port (rev 11)
00   09     0         0x19a4    PCI bridge: Intel Corporation Atom Processor C3000 Series PCI Express Root Port #0 (rev 11)
00   0b     0         0x19a6    PCI bridge: Intel Corporation Atom Processor C3000 Series PCI Express Root Port #2 (rev 11)
00   0e     0         0x19a8    PCI bridge: Intel Corporation Atom Processor C3000 Series PCI Express Root Port #4 (rev 11)
00   12     0         0x19ac    System peripheral: Intel Corporation Atom Processor C3000 Series SMBus Contoller - Host (rev 11)
00   14     0         0x19c2    SATA controller: Intel Corporation Atom Processor C3000 Series SATA Controller 1 (rev 11)
00   15     0         0x19d0    USB controller: Intel Corporation Atom Processor C3000 Series USB 3.0 xHCI Controller (rev 11)
00   16     0         0x19d1    PCI bridge: Intel Corporation Atom Processor C3000 Series Integrated LAN Root Port #0 (rev 11)
00   18     0         0x19d3    Communication controller: Intel Corporation Atom Processor C3000 Series ME HECI 1 (rev 11)
00   1a     0         0x19d8    Serial controller: Intel Corporation Atom Processor C3000 Series HSUART Controller (rev 11)
00   1a     1         0x19d8    Serial controller: Intel Corporation Atom Processor C3000 Series HSUART Controller (rev 11)
00   1a     2         0x19d8    Serial controller: Intel Corporation Atom Processor C3000 Series HSUART Controller (rev 11)
00   1f     0         0x19dc    ISA bridge: Intel Corporation Atom Processor C3000 Series LPC or eSPI (rev 11)
00   1f     2         0x19de    Memory controller: Intel Corporation Atom Processor C3000 Series Power Management Controller (rev 11)
00   1f     4         0x19df    SMBus: Intel Corporation Atom Processor C3000 Series SMBus controller (rev 11)
00   1f     5         0x19e0    Serial bus controller [0c80]: Intel Corporation Atom Processor C3000 Series SPI Controller (rev 11)
01   00     0         0x19e2    Co-processor: Intel Corporation Atom Processor C3000 Series QuickAssist Technology (rev 11)
02   00     0         0xb277    Ethernet controller: Broadcom Inc. and subsidiaries Device b277 (rev 02)
03   00     0         0x1533    Ethernet controller: Intel Corporation I210 Gigabit Network Connection (rev 03)
05   00     0         0x15c2    Ethernet controller: Intel Corporation Ethernet Connection X553 Backplane (rev 11)
05   00     1         0x15c2    Ethernet controller: Intel Corporation Ethernet Connection X553 Backplane (rev 11)

```

####porttransceiver
port transceiver related command
**Syntax**: `port transceiver <interface-id> {lpmode <enabled/disabled> | reset}

**Command mode**: EXEC

**Supported Releases**: 1.0.0 or later

**Click command**: 
- `config interface transceiver lpmode <interface_name> (enable | disabled)`
- `config interface transceiver reset <interface_name>`

**Example**:
```
sonic# port transceiver 53 lpmode enabled
sonic# port transceiver 53 lpmode disabled
```

####show port transceiver lpmode
Display port transceiver lpmode details
**Syntax**: `show port transceiver lpmode [<port-id>]`

**Parameters** :
- `port-id` - Port identifier to get the lpmode details

**Command mode**: EXEC

**Supported Releases**: 1.0.0 or later

**Click command**: 
- `show interface transceiver lpmode [<interface_name>]`

**Example**:
```

sonic# show port transceiver lpmode
Port           Lpmode
------------------------------
Ethernet0      Off
Ethernet1      Off
Ethernet2      Off

```

###show system
####system-health monitor-list
Display status of system components

**Syntax**: `show system-health monitor-list`

**Command mode**: EXEC

**Supported Releases**: 1.0.0 or later

**Click command**: 
- `show system-health monitor-list`

**Example**:
```

sonic# show system-health monitor-list
--------------------------------------------------
Name                          Status    Type
--------------------------------------------------
Fantray1_1                    OK        Fan
Fantray2_1                    OK        Fan
Fantray3_1                    OK        Fan
PSU 1                         Not OK    PSU
PSU 2                         OK        PSU
bgp:bgpcfgd                   OK        Process
bgp:bgpd                      OK        Process
bgp:fpmsyncd                  OK        Process
bgp:staticd                   OK        Process
bgp:zebra                     OK        Process
container_checker             OK        Program
container_memory_telemetry    OK        Program
database:redis                OK        Process
diskCheck                     OK        Program
lldp:lldp-syncd               OK        Process
lldp:lldpd                    OK        Process
lldp:lldpmgrd                 OK        Process
root-overlay                  OK        Filesystem
routeCheck                    OK        Program
rsyslog                       OK        Process
snmp:snmp-subagent            OK        Process
snmp:snmpd                    OK        Process
sonic                         OK        System
swss:buffermgrd               OK        Process
swss:coppmgrd                 OK        Process
swss:fdbmgrd                  OK        Process
swss:fdbsyncd                 OK        Process
swss:intfmgrd                 OK        Process
swss:nbrmgrd                  OK        Process
swss:neighsyncd               OK        Process
swss:orchagent                OK        Process
swss:portmgrd                 OK        Process
swss:portsyncd                OK        Process
swss:tunnelmgrd               OK        Process
swss:vlanmgrd                 OK        Process
swss:vrfmgrd                  OK        Process
swss:vxlanmgrd                OK        Process
syncd:syncd                   OK        Process
teamd:teammgrd                OK        Process
teamd:teamsyncd               OK        Process
teamd:tlm_teamd               OK        Process
telemetry:dialout             OK        Process
telemetry:telemetry           OK        Process
var-log                       OK        Filesystem
vnetRouteCheck                OK        Program

```

####system status
Display status of the services

**Syntax**: `show system status`

**Command mode**: EXEC

**Supported Releases**: 2.0 or later

**Click command**: 
- `show system-health sysready-status`

**Example**:
```

Celestica-DS3000# show system status
System is not ready - one or more services are not up
----------------------------------------------------------------------------------
Service-Name                   Service-Status    App-Ready-Status   Down-Reason
----------------------------------------------------------------------------------
auditd                         OK                OK                 -
bgp                            OK                OK                 -
caclmgrd                       OK                OK                 -
config-chassisdb               OK                OK                 -
config-setup                   OK                OK                 -
containerd                     OK                OK                 -
cron                           OK                OK                 -
database                       OK                OK                 -
determine-reboot-cause         OK                OK                 -
docker                         OK                OK                 -
eventd                         OK                OK                 -
gnmi                           Down              Down               Inactive
kdump-tools                    OK                OK                 -
lldp                           OK                OK                 -
macsec                         OK                OK                 -
mgmt-framework                 OK                OK                 -
mstp                           OK                OK                 -
netfilter-persistent           OK                OK                 -
ntp                            OK                OK                 -
opennsl-modules                OK                OK                 -
pddf-platform-init             OK                OK                 -
pmon                           OK                OK                 -
procdockerstatsd               OK                OK                 -
radv                           OK                OK                 -
ras-mc-ctl                     OK                OK                 -
rsyslog                        OK                OK                 -
smartmontools                  OK                OK                 -
snmp                           OK                OK                 -
ssh                            OK                OK                 -
swss                           OK                OK                 -
syncd                          OK                OK                 -
sysstat                        OK                OK                 -
teamd                          OK                OK                 -
ztp                            OK                OK                 -
Celestica-DS3000#
```

###show secure-boot
####show secure-boot status
Show Secure Boot Active status

**Syntax**: `show secure-boot status`

**Command mode**: EXEC

**Supported Releases**: 4.0.0 or later

**Click command**: 
- `show secure-boot state`

**Example**:
```
Celestica-ES1050-48C# show secure-boot status
Secure Boot State:  DISABLED
Celestica-ES1050-48C#
```

####show secure-boot certificate
Display secure-boot certificate details

**Syntax**: `show secure-boot certificate [uefi <authorized|forbidden>] [mok <authorized|forbidden>]`

**Command mode**: EXEC

**Supported Releases**: 4.0.0 or later

**Click command**: 
- `show secure-boot certificate`

**Example**:
```
Celestica-ES1050-48C# show secure-boot certificate mok forbidden
-------------------------------------------------------------------------------
MOK Forbidden Keys:
-------------------------------------------------------------------------------
Key Name:         KEY_1
SHA256 Hash:      13a1f37bedfb5417b6b737e2a3816c8fd587d74d836914b2b2edc9fd6ca30e58
-------------------------------------------------------------------------------
Key Name:         KEY_2
Issuer:           C=CA, ST=Ontario, L=Toronto, O=Celestica Inc, OU=HPS, CN=CSHCSD22 SONiC local-Dev CA-Cert2
Subject:          C=CA, ST=Ontario, L=Toronto, O=Celestica Inc, OU=HPS, CN=CSHCSD22 SONiC local-Dev CA-Cert2
Version:          3 (0x2)
Signature Algorithm: sha256WithRSAEncryption
Key Algorithm:    rsaEncryption
Public Key Size:  4096
SHA1 Fingerprint: 21:7a:24:15:8b:2f:55:1b:5b:61:3e:db:7b:55:9e:ec:8a:0e:b5:71
Validity Before:  Dec 16 18:05:35 2024 GMT
Validity After:   Dec 17 18:05:35 2044 GMT
-------------------------------------------------------------------------------
Key Name:         KEY_3
Issuer:           C=CA, ST=Ontario, L=Toronto, O=Celestica Inc, OU=HPS, CN=CSHCSD22 SONiC local-Dev Cert
Subject:          C=CA, ST=Ontario, L=Toronto, O=Celestica Inc, OU=HPS, CN=CSHCSD22 SONiC local-Dev Key2
Version:          1 (0x0)
Signature Algorithm: sha256WithRSAEncryption
Key Algorithm:    rsaEncryption
Public Key Size:  4096
SHA1 Fingerprint: 09:96:3b:49:75:6b:7b:05:42:57:5c:1f:1a:6a:a6:17:d5:3c:cf:81
Validity Before:  Dec 16 18:21:10 2024 GMT
Validity After:   Dec 14 18:21:10 2034 GMT
-------------------------------------------------------------------------------
Celestica-ES1050-48C#

```

## Advanced Commands
#### Execute file
Execute the commands from the file.

**Syntax** : `exec-file <file-path> [stop-on-error]`

**Command mode** : EXEC

**Parameters** :
- `<file-path>` : Absoulte file path
- `stop-on-error` : Stop execution when error encountered

**Usage** : File shall be available in mgmt-framework container

**Supported Releases** :  1.0.0 or later

**Click command** : None

**Example**
```
root@sonic:/# cat /tmp/1.txt
configure terminal
interface Vlan 10
description "Vlan 10"
no description
no interface Vlan 10
root@sonic:/#

sonic# exec-file /tmp/1.txt
sonic# configure terminal
sonic(config)# interface Vlan 10
sonic(conf-if-Vlan10)# description "Vlan 10"
sonic(conf-if-Vlan10)# no description
sonic(conf-if-Vlan10)# no interface Vlan 10
sonic(config)#
```

## Guidelines

### Encryption guildlines
The encryption for the plaintext passwords in few configurations (RADIUS, TACACS, SNMP, etc) is done internally by system generated key only. The password encrypted outside shall not be configured in the system. The commands allow flexibility to accept either plaintext or encrypted text as inputs. The `show running-config` and `show startup-config` print the encrypted password always.

### Telemetry configuration guidelines
Few configurations (`server port <port-value>`, `server certificate file <cert-file> <key-file>` and `ca-certificate <cert-file>`) require restarting telemetry service to apply the configuration. Follow the steps below to minimize the number of telemetry service restarts
- Transfer the certificates and key files (server certificate, server key, CA certificate) into host system from external server
- Transfer the certificates and key files from host system to telemetry container. Use `docker cp <local-file> telemetry:<absoulte-file-path>` in admin or root user shell
- Disable the telemetry feature using `config feature state gnmi disabled`
- Configure the certificate, port number, authentication modes in sonic-cli
- Enable the telemetry feature using `config feature state gnmi enabled`

## Config File Commands
### Copy running-config to startup-config
Copy the running configuration to startup configuration file

**Syntax** : `copy running-config startup-config`

**Command mode** : EXEC

**Parameters** : None

**Usage** : Use this command to save running configuration to startup configuration file.

**Supported Releases** :  1.0.0 or later

**Click command** : config save

**Example**
```
sonic# copy running-config startup-config
Success
sonic#
```

### Copy running-config to local file
Copy the running configuration to local configuration file

**Syntax** : `copy running-config <destination_file_path>`

**Command mode** : EXEC

**Parameters** :
`destination_file_path`  -  Destination file absolute path (local://<filepath>)

**Usage** : Use this command to save running configuration to local configuration file.

**Supported Releases** :  1.0.0 or later

**Click command** : config save <filename>

**Example**
```
sonic# copy running-config local://home/admin/sample_conf.json
Success
sonic# 
```

### Copy startup-config to local file
Copy the startup configuration to local configuration file

**Syntax** : `copy startup-config <destination_file_path>`

**Command mode** : EXEC

**Parameters** :
`destination_file_path`  -  Destination file absolute path (local://<filepath>)

**Usage** : Use this command to copy startup configuration to local configuration file.

**Supported Releases** :  1.0.0 or later

**Click command** : None

**Example**
```
sonic# copy startup-config local://home/admin/sample_conf.json
Success
sonic# 
```

### Copy local file config to startup-config
Copy the local file configuration to startup configuration.

**Syntax** : `copy <source_file_path> startup-config`

**Command mode** : EXEC

**Parameters** :
`source_file_path`  -  Source file absolute path (local://<filepath>)

**Usage** : Use this command to copy local file configuration to startup configuration.

**Supported Releases** :  1.0.0 or later

**Click command** : None

**Example**
```
sonic# copy local://home/admin/sample_conf.json startup-config
Success
sonic#

```

### Copy local file config to running-config
Copy the local file configuration to running configuration.

**Syntax** : `copy <source_file_path> running-config`

**Command mode** : EXEC

**Parameters** :
`source_file_path`  -  Source file absolute path (local://<filepath>)

**Usage** : Use this command to copy local file configuration to running configuration.

**Supported Releases** :  1.0.0 or later

**Click command** : config load <filename>

**Example**
```
sonic# copy local://home/admin/sample_conf.json running-config
Success
sonic#

```

### Remove startup-config
Remove the startup configuration file.

**Syntax** : `write erase`

**Command mode** : EXEC

**Parameters** : None

**Usage** : Use this command to remove startup configuration file.

**Supported Releases** :  1.0.0 or later

**Click command** : None

**Example**
```
sonic# write erase
Success
sonic#

```

## Access Control Lists
### IPv4 ACL Commands
#### IPv4 Access-list create and delete
Create a new IPv4 access-list(if not present). Enters into "config-ipv4-acl" mode.

**Syntax** : 
`ip access-list <acl-name>`

**Parameters** :
`acl-name` - String(Max: 63 characters)  IPV4 access list name

**Command mode** : CONFIG

**Usage**       : Use `no ip access-list <acl-name>` to remove the access-list.

**Supported Releases** :  1.0.0 or later

**Click commands** :
- config acl add table [OPTIONS] <table_name> <table_type>  
Options:
  -d, --description TEXT
  -p, --ports TEXT
  -s, --stage [ingress|egress]


**Example**
```
sonic(config)# ip access-list ip_access_name
sonic(config-ipv4-acl)#

sonic# configure terminal
sonic(config)# no ip access-list ip_access_name
```

#### IPv4 Access-list rules create and delete
Add new rules for the IPv4 access-list from the "config-ipv4-acl" mode.

**Syntax for L3 protocols {protocol-number | ip | icmp}** : 
`sequence <seq-number> {permit | deny} {protocol-number | ip | icmp} <source-ip-address> <destination-ip-address> [dscp <dscp-value>]`

**Parameters** :
- `seq-number` - Sequence number for the ACL rule. Range:1-65535.
- `permit` - Configure permit for "forwarding the traffic" 
- `deny` - Configure deny for "dropping the traffic"
- `protocol-number` - Supported protocol number(1,2,6,17,46,47,51,58,103,115). Range: 0-255
- `ip`   - IP packets
- `icmp` - ICMP packets
- `source-ip-address` - Can be one of the below value:  
  -  `A.B.C.D/mask` - Source IPv4 prefix
  -  `any` - 'any' keyword for matching any IPv4 address
  -  `src-host <ipv4-address>` - Source Host IPv4 address
- `destination-ip-address` - Can be one of the below value:  
  -  `A.B.C.D/mask` - Destination IPv4 prefix
  -  `any` - 'any' keyword for matching any IPv4 address
  -  `dst-host` <ipv4-address> - Destination Host IPv4 address
- `dscp-value` - Consider only packets matching DSCP value. Range:0-63.

**Syntax for L4 protocols {tcp | udp}** : 
`sequence <seq-number> {permit | deny} {tcp | udp} <source-ip-address> [src-eq <src-l4-port>| src-gt <src-start-l4-port> | src-lt <src-end-l4-port> | src-range <src-start-l4-port> <src-end-l4-port>] <destination-ip-address> [dst-eq <dst-l4-port>| dst-gt <dst-start-l4-port> | dst-lt <dst-end-l4-port> | dst-range <dst-start-l4-port> <dst-end-l4-port>] [ack | fin | psh | rst | syn | urg] [dscp <dscp-value>]`

**Parameters** :
- `src-l4-port` - L4 port number. Range: 0 - 65535.
- `src-start-l4-port` - Matches all L4 source port number greater than the given L4 port number. Range: 0-65534.
- `src-end-l4-port` - Matches all L4 source port number lesser than the given L4 port number. Range: 1-65535.
- `dst-l4-port` - L4 port number. Range: 0 - 65535.
- `dst-start-l4-port` - Matches all L4 destination port number greater than the given L4 port number. Range: 0-65534.
- `dst-end-l4-port` - Matches all L4 destination port number lesser than the given L4 port number. Range: 1-65535.
- `ack | fin | psh | rst | syn | urg` - Match TCP flags. Applicable only for TCP protocol. 


**Command mode** : ACL IPv4 mode

**Usage**       : Use `no sequence <sequence-number>` to remove the access-list rule corresponding to given sequence number.

**Supported Releases** :  1.0.0 or later

**Click commands** :
- config acl update {full | incremental} <filename>  
  - full         - Full update of ACL rules configuration.
  - incremental  - Incremental update of ACL rule configuration.


**Example**
```
sonic(config)# ip access-list ip_access_name
sonic(config-ipv4-acl)# sequence 1 permit ip 1.1.1.1/24 2.2.2.2/16 dscp 63
sonic(config-ipv4-acl)# sequence 2 deny tcp src-host 1.1.1.1 src-eq 1000 dst-host 2.2.2.2 dst-range 2000 4000 ack urg dscp 63

sonic# configure terminal
sonic(config)# ip access-list ip_access_name
sonic(config-ipv4-acl)# no sequence 1
sonic(config-ipv4-acl)# no sequence 2

```
#### IPv4 Access-list bind to interface
Bind access-list of type IPv4 to interface in interface mode.

**Syntax** : 
`ip access-group <acl-name> {in | out}`

**Parameters** :
`acl-name` - String(Max: 63 characters)  Access list name

**Command mode** : Interface modes (Ethernet, PortChannel and VLAN)

**Usage**       : Use below command to unbind the access-list from the interface `no ip access-group <acl-name> {in | out}` 

**Supported Releases** :  1.0.0 or later

**Click commands** :
- config acl add table `-p <port-name-list> -s <ingress | egress>` <table_name> <table_type>  
Options: -p and -s help to bind access-list to interface.

**Example**
```
L3V4/IPv4 : 
sonic(config)# interface Ethernet 1
sonic(conf-if-Ethernet1)# ip access-group ip_access_in in
sonic(conf-if-Ethernet1)# ip access-group ip_access_out out

sonic(config)# interface Ethernet 1
sonic(conf-if-Ethernet1)# ip access-group ip_access_in in
sonic(conf-if-Ethernet1)# ip access-group ip_access_out out

```

#### IPv4 Access-list show command
Display details of IPv4 access-list and rules , along with packets and bytes count of each rule.

**Syntax** : 
`show ip access-lists [<acl-name>]`

**Parameters** :
`acl-name` - String(Max: 63 characters)  Access list name

**Command mode** : EXEC

**Usage**       : Use `show ip access-lists [<acl-name>]` to display the access-list.

**Supported Releases** :  1.0.0 or later

**Click commands** :
- show acl table
- show acl rule

**Example**
```
sonic# show ip access-lists
ip access-list ip_access_name
     sequence 1 permit ip 1.1.1.1/24 2.2.2.2/16 dscp 63 (0 packets) [0 octets]
     sequence 2 deny tcp 1.1.1.1/32 eq 1000 2.2.2.2/32 eq 2000-4000 ack urg dscp 63 (0 packets) [0 octets]

```

#### IPv4 Access-group show command
Display details of IPv4 access-group bindings.

**Syntax** : 
`show ip access-group`

**Command mode** : EXEC

**Usage**       : Use `show ip access-group`.

**Supported Releases** :  1.0.0 or later

**Click commands** :
- show acl table

**Example**
```
sonic# show ip access-group
IP access-list ip-access-in configured on Ethernet1 in Ingress direction
sonic# show ip access-group
IP access-list ip-access-out configured on Ethernet1 in Egress direction
```

#### IPv4 Access-list clear command
Clears packets and bytes count of each IPV4 rule for the specified access-list name or if name not specified then for all access-lists of type IPv4.

**Syntax** : 
`clear ip access-list counters [<acl-name>]`

**Parameters** :
`acl-name` - Name of the IPv4 access-list (Max size 63)

**Command mode** : EXEC

**Usage**       : Use `clear ip access-list counters [<acl-name>]` to clear the access-list rules counters.

**Supported Releases** :  1.0.0 or later

**Click commands** :
- aclshow -c

**Example**
```
sonic# clear ip access-list counters 
Success
```

### IPv6 ACL Commands
#### IPv6 Access-list create and delete
Create a new IPv6 access-list (if not present). Enters into "config-ipv6-acl" mode.

**Syntax** : 
`ipv6 access-list <acl-name>`

**Parameters** :
`acl-name` - String(Max: 63 characters)  IPv6 access list name

**Command mode** : CONFIG

**Usage**       : Use `no ipv6 access-list <acl-name>` to remove the access-list.

**Supported Releases** :  1.0.0 or later

**Click commands** :
- config acl add table [OPTIONS] <table_name> <table_type>  
Options:
  -d, --description TEXT
  -p, --ports TEXT
  -s, --stage [ingress|egress]


**Example**
```
sonic(config)# ipv6 access-list ipv6_access_name
sonic(config-ipv6-acl)#

sonic# configure terminal
sonic(config)# no ipv6 access-list ipv6_access_name

```

#### IPv6 Access-list rules create and delete
Add new rules for the IPv6 access-list from the "config-ipv6-acl" mode.

**Syntax for L3 protocols {protocol-number | ipv6 | icmpv6}** : 
`sequence <seq-number> {permit | deny} {protocol-number | ipv6 | icmpv6} <source-ipv6-address> <destination-ipv6-address> [dscp <dscp-value>]`

**Parameters** :
- `seq-number` - Sequence number for the ACL rule. Range:1-65535.
- `permit` - Configure permit for "forwarding the traffic" 
- `deny` - Configure deny for "dropping the traffic"
- `protocol-number` - Supported protocol number(1,2,6,17,46,47,51,58,103,115). Range: 0-255
- `ipv6`   - IPV6 packets
- `icmpv6` - ICMPV6 packets
- `source-ipv6-address` - Can be one of the below value:  
  -  `A::B/mask` - Source IPv6 prefix
  -  `any` - 'any' keyword for matching any IPv6 address
  -  `src-host <ipv6-address>` - Source Host IPv6 address
- `destination-ipv6-address` - Can be one of the below value:  
  -  `A::B/mask` - Destination IPv6 prefix
  -  `any` - 'any' keyword for matching any IPv6 address
  -  `dst-host <ipv6-address>` - Destination Host IPv6 address
- `dscp-value` - Consider only packets matching DSCP value. Range:0-63.

**Syntax for L4 protocols {tcp | udp}** : 
`sequence <seq-number> {permit | deny} {tcp | udp} <source-ipv6-address> [src-eq <src-l4-port>| src-gt <src-start-l4-port> | src-lt <src-end-l4-port> | src-range <src-start-l4-port> <src-end-l4-port>] <destination-ipv6-address> [dst-eq <dst-l4-port>| dst-gt <dst-start-l4-port> | dst-lt <dst-end-l4-port> | dst-range <dst-start-l4-port> <dst-end-l4-port>] [ack | fin | psh | rst | syn | urg] [dscp <dscp-value>]`

**Parameters** :
- `src-l4-port` - L4 port number. Range: 0 - 65535.
- `src-start-l4-port` - Matches all L4 source port number greater than the given L4 port number. Range: 0-65534.
- `src-end-l4-port` - Matches all L4 source port number lesser than the given L4 port number. Range: 1-65535.
- `dst-l4-port` - L4 port number. Range: 0 - 65535.
- `dst-start-l4-port` - Matches all L4 destination port number greater than the given L4 port number. Range: 0-65534.
- `dst-end-l4-port` - Matches all L4 destination port number lesser than the given L4 port number. Range: 1-65535.
- `ack | fin | psh | rst | syn | urg` - Applicable only for TCP protocol. 

**Command mode** : ACL IPv6 mode

**Usage**       : Use `no sequence <sequence-number>` to remove the access-list rule corresponding to given sequence number.

**Supported Releases** :  1.0.0 or later

**Click commands** :
- config acl update {full | incremental} <filename>  
  - full         Full update of ACL rules configuration.
  - incremental  Incremental update of ACL rule configuration.


**Example**
```
sonic(config)# ipv6 access-list ipv6_access_name
sonic(config-ipv6-acl)# sequence 1 permit ipv6 1::1/64 2::2/64 dscp 63
sonic(config-ipv6-acl)# sequence 2 deny tcp src-host 1::1 src-eq 1000 dst-host 2::2 dst-range 2000 4000 ack urg dscp 63

sonic# configure terminal
sonic(config)# ipv6 access-list ipv6_access_name
sonic(config-ipv6-acl)# no sequence 1
sonic(config-ipv6-acl)# no sequence 2

```
#### IPv6 Access-list bind to interface
Bind access-list of type IPv6 to interface in interface mode.

**Syntax** : `ipv6 access-group <acl-name> {in | out}`

**Parameters** :
`acl-name` - String(Max: 63 characters)  Access list name

**Command mode** : Interface modes (Ethernet, PortChannel and VLAN)

**Usage**       : Use below command to unbind the access-list from the interface `no ipv6 access-group <acl-name> {in | out}`

**Supported Releases** :  1.0.0 or later

**Click commands** :
- config acl add table `-p <port-name-list> -s <ingress | egress>` <table_name> <table_type>  
Options: -p and -s help to bind access-list to interface.

**Example**
```
sonic(config)# interface Ethernet 1
sonic(conf-if-Ethernet1)# ipv6 access-group newipv6 in
sonic(conf-if-Ethernet1)# ipv6 access-group newipv6out out

sonic(config)# interface Ethernet 1
sonic(conf-if-Ethernet1)# ipv6 access-group newipv6 in
sonic(conf-if-Ethernet1)# ipv6 access-group newipoutv6 out

```

#### IPv6 Access-list show command
Display details of IPv6 access-list and rules  , along with packets and bytes count of each rule.

**Syntax** : 
`show ipv6 access-lists [<acl-name>]`

**Parameters** :
`acl-name` - String(Max: 63 characters)  Access list name

**Command mode** : EXEC

**Usage**       : Use `show ipv6 access-lists [<acl-name>]` to display the access-list.

**Supported Releases** :  1.0.0 or later

**Click commands** :
- show acl table
- show acl rule

**Example**
```
sonic# show ipv6 access-lists
ipv6 access-list ipv6_access_name
     sequence 1 permit ipv6 1::1/64 2::2/64 dscp 63 (0 packets) [0 octets]
     sequence 2 deny tcp 1::1/128 eq 1000 2::2/128 eq 2000-4000 ack urg dscp 63 (0 packets) [0 octets]

```
#### IPv6 Access-group show command
Display details of IPv6 access-group bindings.

**Syntax** : 
`show ipv6 access-group`

**Command mode** : EXEC

**Usage**       : Use `show ipv6 access-group`.

**Supported Releases** :  1.0.0 or later

**Click commands** :
- show acl table

**Example**
```
sonic# show ipv6 access-group
IPV6 access-list ipv6_access_in configured on Ethernet1 in Ingress direction
sonic# show ipv6 access-group
IPV6 access-list ipv6_access_in configured on Ethernet1 in Egress direction

```

#### IPv6 Access-list clear command
Clears packets and bytes count of each IPV6 rule for the specified access-list name or if name not specified then for all access-lists of type IPv6.

**Syntax** : 
`clear ipv6 access-list counters [<acl-name>]`

**Parameters** :
`acl-name` - Name of the IPv6 access-list (Max size 63)

**Command mode** : EXEC

**Usage**       : Use `clear ipv6 access-list counters [<acl-name>]` to clear the access-list rules counters.

**Supported Releases** :  1.0.0 or later

**Click commands** :
- aclshow -c

**Example**
```
sonic# clear ipv6 access-list counters 
Success
```
### MAC ACL Commands
#### MAC Access-list create and delete
Create a new MAC access-list (if not present). Enters into "config-mac-acl" mode.

**Syntax** : 
`mac access-list <acl-name>`

**Parameters** :
`acl-name` - String(Max: 63 characters)  MAC access list name

**Command mode** : CONFIG

**Usage**       : Use `no mac access-list <acl-name>` to remove the access-list.

**Supported Releases** :  1.0.0 or later

**Click commands** :
- config acl add table [OPTIONS] <table_name> <table_type>  
Options:
  -d, --description TEXT
  -p, --ports TEXT
  -s, --stage [ingress|egress]


**Example**
```
sonic(config)# mac access-list mac_access_name
sonic(config-mac-acl)#

sonic# configure terminal
sonic(config)# no mac access-list mac_access_name
```

#### MAC Access-list rules create and delete
Add new rules for the MAC access-list from the "config-mac-acl" mode.

**Syntax** : 
`sequence <seq-number> {permit | deny} {any | <src-mac-address> <src-mask-address>} {any | <dst-mac-address> <dst-mask-address>} [ <Ether-type> | arp |  ip | ipv6]`

**Parameters** :
- `seq-number` - Sequence number for the ACL rule. Range:1-65535.
- `permit` - Configure permit for "forwarding the traffic" 
- `deny` - Configure deny for "dropping the traffic"
-  `any` - 'any' keyword for matching any MAC address
-  `src-mac-address` - Source MAC address of the format nn:nn:nn:nn:nn:nn where 'n'-any number in the range of '0-f'.
- `src-mask-address` - Source mask mac address.
- `dst-mac-address` - Destination MAC address of the format nn:nn:nn:nn:nn:nn where 'n'-any number in the range of '0-f'.
- `dst-mask-address` - Destination mask mac address.
- `Ether-type` - (0x600-0xffff)  Ethertype (0x0800,0x0806,0x86dd,0x8847,0x88cc,0x8915)

**Command mode** : ACL MAC mode

**Usage**       : Use `no sequence <sequence-number>` to remove the access-list rule corresponding to given sequence number.

**Supported Releases** :  1.0.0 or later

**Click commands** :
- config acl update {full | incremental} <filename>  
  - full         Full update of ACL rules configuration.
  - incremental  Incremental update of ACL rule configuration.


**Example**
```
sonic(config)# mac access-list mac_access_name
sonic(config-mac-acl)# sequence 1 permit any any ip
sonic(config-mac-acl)# sequence 2 deny 11:11:11:11:11:11 ff:ff:ff:ff:ff:ff 22:22:22:22:22:22 ff:ff:ff:ff:ff:ff arp

sonic# configure terminal
sonic(config)# mac access-list mac_access_name
sonic(config-mac-acl)# no sequence 1
sonic(config-mac-acl)# no sequence 2

```
#### MAC Access-list bind to interface
Bind access-list of type MAC to interface in interface mode. 

**Syntax** : `mac access-group <acl-name> {in | out}`

**Parameters** :
`acl-name` - String(Max: 63 characters)  Access list name

**Command mode** : Interface modes (Ethernet, PortChannel and VLAN)

**Usage**       : Use below command to unbind the access-list from the interface `no mac access-group <acl-name> {in | out}`

**Supported Releases** :  1.0.0 or later

**Click commands** :
- config acl add table `-p <port-name-list> -s <ingress | egress>` <table_name> <table_type>  
Options: -p and -s help to bind access-list to interface.

**Example**
```
sonic(config)# interface Ethernet 1
sonic(conf-if-Ethernet1)# mac access-group newmac in
sonic(conf-if-Ethernet1)# mac access-group newmac out

sonic(config)# interface Ethernet 1
sonic(conf-if-Ethernet1)# mac access-group newmac in
sonic(conf-if-Ethernet1)# mac access-group newmac out
```

#### MAC Access-list show command
Display details of MAC access-list and rules , along with packets and bytes count of each rule.

**Syntax** : 
`show mac access-lists [<acl-name>]`

**Parameters** :
`acl-name` - String(Max: 63 characters)  Access list name

**Command mode** : EXEC

**Usage**       : Use `show mac access-lists [<acl-name>]` to display the access-list.

**Supported Releases** :  1.0.0 or later

**Click commands** :
- show acl table
- show acl rule

**Example**
```
sonic# show mac access-lists
mac access-list mac_access_name
     sequence 1 permit 00:00:00:00:00:00 00:00:00:00:00:00 00:00:00:00:00:00 00:00:00:00:00:00 ip (0 packets) [0 octets]
     sequence 2 deny 11:11:11:11:11:11 ff:ff:ff:ff:ff:ff 22:22:22:22:22:22 ff:ff:ff:ff:ff:ff arp (0 packets) [0 octets]

```
#### MAC Access-group show command
Display details of MAC access-group bindings.

**Syntax** : 
`show mac access-group`

**Command mode** : EXEC

**Usage**       : Use `show mac access-group`.

**Supported Releases** :  1.0.0 or later

**Click commands** :
- show acl table

**Example**
```
sonic# show mac access-group
MAC access-list mac-access-in configured on Ethernet1 in Ingress direction
sonic# show mac access-group
MAC access-list mac-access-out configured on Ethernet1 in Egress direction
```

#### MAC Access-list clear command
Clears packets and bytes count of each MAC rule for the specified access-list name or if name not specified then for all access-lists of type MAC.

**Syntax** : 
`clear mac access-list counters [<acl-name>]`

**Parameters** :
`acl-name` - Name of the MAC access-list (Max size 63)

**Command mode** : EXEC

**Usage**       : Use `clear mac access-list counters [<acl-name>]` to clear the access-list rules counters.

**Supported Releases** :  1.0.0 or later

**Click commands** :
- aclshow -c

**Example**
```
sonic# clear mac access-list counters 
Success
```
##USER MANAGEMENT
###Password
Configure user password

**Syntax** :
`user <username> { password <plaintext_value> | hashed-password <hashed_value>}`

**Parameters** :
`username` - admin user account only
`plaintext_value` - Password in plaintext
`encrypted_value` - Password string in encrypted format(cipher text)

**Command mode** : CONFIG

**Usage** :
- Use `no user <username> password` to set default password for the user

**Supported Releases** :  1.0.0 or later

**Click commands** :
- `config user { modify { --password | --hash-password } USER_NAME PASSWORD_VALUE | reset USER_NAME }`

**Example**
```

sonic(config)# user admin password admin@123
sonic(config)# user admin hashed-password $6$xam6wdQKfk1VPZD7$wnzmbyWl900M47cgLF1s/jWlO6ah3S5U7R3L07jieCyNpWLDITpPFhWp/kp0h6BmxXTqVbK0WpzjyByebFn0e/
sonic(config)# no user admin password
sonic(config)#

```

##BANNER
###MOTD Banner
Configure MOTD(Message of the Day) Banner

**Syntax** :
`banner motd [message]`

**Parameters** :
`message` - Message to be displayed in the MOTD banner;

**Command mode** : CONFIG

**Usage** : 
- "banner motd" + ENTER key to configure multi-line banner and use "~C" to exit from multi-line banner input mode.
- Use `no banner motd` to set default motd banner message

**Supported Releases** :  1.0.0 or later

**Click commands** :
- `config banner motd <message>`

**Example**
```

sonic(config)# banner motd "hello"
sonic(config)# banner motd
Multi-line Input (End message with ~C in a new line to exit)
> This is a sample message
> good day
> ~C
sonic(config)# no banner motd
sonic(config)#

```

###Login Banner
Configure Login Banner

**Syntax** :
`banner login [message]`

**Parameters** :
`message` - Message to be displayed in the login banner;

**Command mode** : CONFIG

**Usage** : 
- if enter is pressed with [message], multi-line mode is enabled.
- Use `no banner login` to set default motd banner message

**Supported Releases** :  1.0.0 or later

**Click commands** :
- `config banner login <message>`

**Example**
```

sonic(config)# banner login "hello"
sonic(config)# banner login
Multi-line Input (End message with ~C in a new line to exit)
> This is a sample message
> good day
> ~C
sonic(config)# no banner login
sonic(config)#

```

## RADIUS 
### RADIUS Config Commands
#### RADIUS timeout
Configures global timeout for RADIUS

**Syntax** : 
`radius-server timeout <timeout-value>`

**Parameters** :
`timeout-value` - Enter the timeout value in seconds from 1 to 60, default = 5

**Command mode** : CONFIG

**Usage**       : Use `no radius-server timeout` to remove the configured global timeout.

**Supported Releases** :  1.0.0 or later

**Click commands** :
- config radius timeout [OPTIONS] <time_second>

**Example**
```
sonic# configure terminal
sonic(config)# radius-server timeout 4
sonic(config)# no radius-server timeout
sonic(config)#
```

#### RADIUS passkey
Configures global passkey for RADIUS server

**Syntax** : 
`radius-server { passkey <plaintext-value> | encrypted-passkey <encrypted-passkey-value> }`

**Parameters** :
`plaintext-value` - Plaintext passkey string; Accepts Valid Chars: ASCII printable except SPACE, #, and COMMA, Max Len: 65)
`encrypted-passkey-value` - Encrypted passkey (cipher text)

**Command mode** : CONFIG

**Usage**       : Use `no radius-server passkey` to remove the configured global passkey.

**Supported Releases** :  1.0.0 or later

**Click commands** :
- config radius passkey [OPTIONS] <secret_string>

**Example**
```
sonic# configure terminal
sonic(config)# radius-server passkey test456
sonic(config)# no radius-server passkey
sonic(config)#
```

#### RADIUS authtype 
Configures global authentication type for RADIUS

**Syntax** : 
`radius-server authtype {pap | chap | mschapv2}`

**Parameters** :
- `pap` - Password Authentication Protocol authentication type (default)
- `chap` - Challenge-Handshake Authentication Protocol
- `mschapv2` - Microsoft Challenge-Handshake Authentication Protocol, version 2

**Command mode** : CONFIG

**Usage**       : Use `no radius-server authtype` to remove the configured global authentication type.

**Supported Releases** :  1.0.0 or later

**Click commands** :
- config radius authtype [OPTIONS] <[chap | pap | mschapv2]>

**Example**
```
sonic# configure terminal
sonic(config)# radius-server authtype pap
sonic(config)# no radius-server authtype
sonic(config)#
```

#### RADIUS retransmit
Configures global retransmit attempts for RADIUS

**Syntax** : 
`radius-server retransmit <retransmit-attempt-value>`

**Parameters** :
`retransmit-attempt-value` - Enter the retransmit attempts values from 0 to 10, default = 3

**Command mode** : CONFIG

**Usage**       : Use `no radius-server retransmit` to remove the configured global transmit attempts.

**Supported Releases** :  1.0.0 or later

**Click commands** :
- config radius retransmit [OPTIONS] <retry_attempts> 

**Example**
```
sonic# configure terminal
sonic(config)# radius-server retransmit 4
sonic(config)# no radius-server retransmit
sonic(config)#
```

#### RADIUS host
Configures a RADIUS server

**Syntax** : 
`radius-server host <server-ip-address> | auth-port <auth-port-value> | auth-type {pap | chap | mschapv2} | { passkey <plaintext-value> | encrypted-passkey <encrypted-passkey-value> } | priority <priority-value> | retransmit <retransmit-attempts-value> | source-interface {Ethernet <eth-if-id> | PortChannel <po-if-id>  | Loopback <lpbk-if-id> | Vlan <vl-if-id> | Management } | timeout <timeout-value> | vrf mgmt`

**Parameters** :
- `server-ip-address` - IPv4 or IPv6 address
- `auth-port-value` - Enter authentication port number which ranges from 1 to 65535, default = 1812
- `pap` - Password Authentication Protocol authentication type (default)
- `chap` - Challenge-Handshake Authentication Protocol authentication type
- `mschapv2` - Microsoft Challenge-Handshake Authentication Protocol, version 2 authentication type
- `plaintext-value` - Plaintext passkey string; Accepts Valid Chars: ASCII printable except SPACE, #, and COMMA, Max Len: 65)
- `encrypted-passkey-value` - Encrypted passkey (cipher text)
- `priority-value` - Enter the priority of RADIUS server which ranges from 1 to 60, default = 1
- `retransmit-attempts-value` - Enter the retransmit attempts values from 0 to 10, default = 3
- `eth-if-id` - Ethernet interface identifier in multiples of 4
- `po-if-id` - PortChannel identifier within the range of 1 - 256
- `lpbk-if-id` - Loopback interface identifier, range : 0 - 16383
- `vl-if-id` - VLAN interface identifier, range : 1 - 4094
- `timeout-value` - Enter the RADIUS server timeout values from 1 to 60, default = 5
- `mgmt` - Management VRF, default is no VRF

**Command mode** : CONFIG

**Usage**       : Use `no radius-server host` to remove the configured global radius server.

**Supported Releases** :  1.0.0 or later

**Click commands** :
- config radius add [OPTIONS] <ip_address>
- config radius delete [OPTIONS] <ip_address>

**Example**
```
sonic# configure terminal
sonic(config)# radius-server host 1.2.3.4 auth-port 32 passkey abcd123 auth-type chap priority 3 retransmit 3 source-interface Ethernet 0 timeout 4 vrf mgmt
sonic(config)# no radius-server host 1.2.3.4
sonic(config)#
```

### RADIUS Show commands
#### show radius

Show RADIUS information

**Syntax** : 
`show radius`

**Command mode** : EXEC

**Usage**       : Use `show radius`.

**Supported Releases** :  1.0.0 or later

**Click commands** :
- show radius

**Example**
```
sonic# show radius
RADIUS global timeout                : 5
RADIUS global auth-type              : pap
RADIUS global retransmit_attempts    : 3
RADIUS_SERVER  address 1.2.3.4
               auth_port 1812
               priority 1
```

## TACACS
### TACACS Config Commands
#### TACACS timeout
Configure global timeout for TACACS

**Syntax** : 
`tacacs-server timeout <timeout-value>`

**Parameters** :
`timeout-value` - Enter the timeout value in seconds from 1 to 60, default = 5

**Command mode** : CONFIG

**Usage**       : Use `no tacacs-server timeout` to remove the configured global timeout.

**Supported Releases** :  1.0.0 or later

**Click commands** :
- config tacacs timeout [OPTIONS] <time_second>

**Example**
```
sonic# configure terminal
sonic(config)# tacasc-server timeout 4
sonic(config)# no tacas-server timeout
sonic(config)#
```

#### TACACS authtype 
Configures global authentication type for TACACS 

**Syntax** :
`tacacs-server authtype {pap | chap | login}`

**Parameters** :
- `pap` - Password Authentication Protocol authentication type (default)
- `chap` - Challenge-Handshake Authentication Protocol
- `login` - Login method

**Command mode** : CONFIG

**Usage**       : Use `no tacacs-server authtype` to remove the configured global authentication type.

**Supported Releases** :  1.0.0 or later

**Click commands** :
- config tacacs authtype [OPTIONS] <[chap | pap | login]>

**Example**
```
sonic# configure terminal
sonic(config)# tacacs-server authtype login
sonic(config)# no tacacs-server authtype
sonic(config)#
```

#### TACACS passkey
Configures global passkey for TACACS

**Syntax** : 
`tacacs-server { passkey <plaintext-value> | encrypted-passkey <encrypted-passkey-value> }`

**Parameters** :
- `plaintext-value` - Plaintext passkey string; Accepts Valid Chars: ASCII printable except SPACE, #, and COMMA, Max Len: 65)
- `encrypted-passkey-value` - Encrypted passkey (cipher text)

**Command mode** : CONFIG

**Usage**       : Use `no tacacs-server passkey` to remove the configured global passkey.

**Supported Releases** :  1.0.0 or later

**Click commands** :
- config tacacs passkey [OPTIONS] <secret_string>

**Example**
```
sonic# configure terminal
sonic(config)# tacacs-server passkey testing32
sonic(config)# tacacs-server encrypted-passkey U2FsdGVkX18cfkNuRGFefzU6KLbl1nfCtdS/pepGnRU=
sonic(config)# no tacacs-server passkey
sonic(config)#
```

#### TACACS host
Configures a TACACS server

**Syntax** : 
`tacacs-server host <server-ip-address> { passkey <plaintext-value> | encrypted-passkey <encrypted-passkey-value> } | port <auth-port-value> | priority <priority-value> | auth_type {pap | chap | login} | timeout <timeout-value> | vrf mgmt`

**Parameters** :
- `server-ip-address` - IPv4 or IPv6 address
- `plaintext-value` - Plaintext passkey string; Accepts Valid Chars: ASCII printable except SPACE, #, and COMMA, Max Len: 65)
- `encrypted-passkey-value` - Encrypted passkey (cipher text)
- `auth-port-value` - Enter authentication port number which ranges from 1 to 65535, default = 49
- `priority-value` - Enter the priority of TACACS server which ranges from 1 to 60, default = 1
- `pap` - Password Authentication Protocol authentication type (default)
- `chap` - Challenge-Handshake Authentication Protocol authentication type
- `login` - Login method authentication type
- `timeout-value` - Enter the TACACS server timeout values from 1 to 60, default = 5
- `mgmt` - Management VRF, default is no VRF

**Command mode** : CONFIG

**Usage**       : Use `no tacacs-server host` to remove the configured global tacacs server.

**Supported Releases** :  1.0.0 or later

**Click commands** :
- config tacacs add [OPTIONS] <ip_address>
- config tacacs delete [OPTIONS] <ip_address>

**Example**
```
sonic# configure terminal
sonic(config)# tacacs-server host 10.208.120.120 passkey test23 port 23 priority 3 timeout 6 auth_type login vrf mgmt
sonic(config)# no tacacs-server host 10.208.120.120
sonic(config)#
```

### TACACS Show commands
#### show tacacs

Show TACACS information

**Syntax** : 
`show tacacs`

**Command mode** : EXEC

**Usage**       : Use `show tacacs`.

**Supported Releases** :  1.0.0 or later

**Click commands** :
- show tacacs

**Example**
```
sonic# show tacacs
TACACS global timeout : 5
TACACS global auth-type : pap
TACACS_SERVER address 10.208.29.3
              priority 1
              tcp_port 49
              passkey(encrypted) U2FsdGVkX18cfkNuRGFefzU6KLbl1nfCtdS/pepGnRU
```

## NTP
### NTP Config Commands
#### NTP source-interface
Configure NTP source interface to pick the source IP, used for the NTP packets

**Syntax** : 
`ntp source-interface { Ethernet <eth-id> | PortChannel <po-id> | Loopback <lo-id> | Vlan <vl-id> | Management <mgmt-id> }  `

**Parameters** :
`eth-id` - Physical interface identifier
`po-id` - Portchannel number
`lo-id` - Loopback identifier
`vl-id` - Vlan identifier
`mgmt-id` - Management interface identifier

**Command mode** : CONFIG

**Usage**       : Use `no ntp source-interface` to remove the configured ntp source-interface.

**Supported Releases** :  1.0.0 or later

**Click commands** :
Not Applicable

**Example**
```
sonic# configure terminal
sonic(config)# ntp source-interface Management 0
sonic(config)# no ntp source-interface
sonic(config)#
```

#### NTP vrf
Enabling NTP on a VRF

**Syntax** : 
`ntp vrf {default | mgmt }  `

**Parameters** :
Not Applicable

**Command mode** : CONFIG

**Usage**       : Use `no ntp vrf` to remove the configured ntp VRF.

**Supported Releases** :  1.0.0 or later

**Click commands** :
Not Applicable

**Example**
```
sonic# configure terminal
sonic(config)# ntp vrf default
sonic(config)# no ntp vrf
sonic(config)#
```

#### NTP server
Configures NTP server

**Syntax** : 
`ntp server  <ip-address>`

**Parameters** :
`ip-address` - IP address of the NTP server

**Command mode** : CONFIG

**Usage**       : Use `no ntp server <ip-address>` to remove the configured ntp server.

**Supported Releases** :  1.0.0 or later

**Click commands** :
- config ntp add [OPTIONS] <ip_address>
- config ntp del [OPTIONS] <ip_address>

**Example**
```
sonic# configure terminal
sonic(config)# ntp server 1.2.3.4
sonic(config)# no ntp server 1.2.3.4
sonic(config)#
```

### NTP Show commands
#### show ntp status

Shows NTP synchronization status

**Syntax** : 
`show ntp status`

**Command mode** : EXEC

**Usage**       : Use `show ntp status`.

**Supported Releases** :  1.0.0 or later

**Click commands** :
Not Applicable

**Example**
```
sonic# show ntp status
synchronised to NTP server (10.208.32.30) at stratum 4
   time correct to within 48082 ms
   polling server every 64 s
```

#### show ntp associations

Shows NTP association

**Syntax** : 
`show ntp associations`

**Command mode** : EXEC

**Usage**       : Use `show ntp associations`.

**Supported Releases** :  1.0.0 or later

**Click commands** :
Not Applicable

**Example**
```
sonic# show ntp associations
remote                      refid            st   t   when   poll   reach  delay  offset       jitter
========================================================================================================
*10.208.32.30               10.39.4.76       3    u   15     64     3      0.258  +46769.      24.950
* master (synced), # master (unsynced), + selected, - candidate, ~ configured
sonic#
```

## Syslog
### Syslog Config Commands
#### syslog server
Configures syslog server

**Syntax** : 
`syslog server  <ip-address>`

**Parameters** :
`ip-address` - IP address of the syslog server

**Command mode** : CONFIG

**Usage**       : Use `no syslog server <ip-address>` to remove the configured syslog server.

**Supported Releases** :  1.0.0 or later

**Click commands** :
- config syslog add [OPTIONS] <ip_address>

**Example**
```
sonic# configure terminal
sonic(config)# syslog server 1.2.3.4
sonic(config)# no syslog server 1.2.3.4
sonic(config)#
```

## Interfaces
### Common Interface Commands
#### Interface create and delete
Create the interface, if not present and enters into interface mode.

**Syntax** : `interface {Ethernet <eth-if-id> | PortChannel <po-if-id> [fallback] [min-links <min-links-value>] | Loopback <lpbk-if-id> | Vlan <vl-if-id> | Tunnel <tunnel-if-id>}`

**Parameters** :
- `eth-if-id` - Ethernet interface identifier in multiples of 4
- `po-if-id` - PortChannel identifier within the range of 1 - 256
- `fallback` - Enables LACP fallback or not, default is disabled
- `min-links <>` - Sets the minimum number of links within the from of 1 10 255, default is 1
- `lpbk-if-id` - Loopback interface identifier, range : 0 - 16383
- `vl-if-id` - VLAN interface identifier, range : 1 - 4094
- `tunnel-if-id` - VLAN interface identifier, range : 0 - 128

**Command mode** : CONFIG

**Usage**       : Use `no interface <if-id>` to remove the interface. You cannot remove the static interfaces (Ethernet)

**Supported Releases** :  1.0.0 or later

**Click commands** :
- `config portchannel add <portchannel_name> [--min-links <> --fallback <> --fast-rate [true|false] --on <>]`
- `config vlan add <vid>`
- `config loopback add <loopback_name>`
- `config tunnel add <tunnel_name>`

**Example**
```
sonic(config)# interface Ethernet 20
sonic(conf-if-Ethernet20)#

sonic(config)# interface Vlan 10
sonic(conf-if-Vlan10)# no interface Vlan 10
sonic(config)#

sonic(config)# interface PortChannel 10
sonic(conf-if-PortChannel10)# no interface PortChannel 10
sonic(config)#

sonic(config)# interface Loopback 2
sonic(conf-if-Loopback2)# no interface Loopback 2
sonic(config)#
sonic(config)# interface PortChannel 250 
sonic(conf-if-PortChannel250)# 
sonic(config)# interface PortChannel 201 min-links 2 fallback
sonic(conf-if-PortChannel201)# 
sonic(config)#
sonic(config)# interface PortChannel 199 
sonic(conf-if-PortChannel199)#
sonic(config)# interface Tunnel 100
sonic(conf-if-Tunnel100)#


```

#### `description`
Configures the description for the interface

**Syntax** : `description <string>`

**Parameters** :
- `string` - Accepts alpha numeric characters, special characters (- and _)

**Command mode** : All interface modes

**Usage**       : Use `no description` to remove the description.

**Supported Releases** :  1.0.0 or later

**Click command** : None

**Example**
```
sonic(conf-if-Ethernet0)# description "Ethernet 0"
sonic(conf-if-Ethernet0)# no description
sonic(conf-if-Ethernet0)# 

sonic(conf-if-PortChannel1)# description PortChannel1
sonic(conf-if-PortChannel1)# no description
sonic(conf-if-PortChannel1)#
```

####clear interface counters
Clear counters information of all the interfaces

**Syntax**: `clear interface counters`

**Command mode**: EXEC

**Supported Releases**: 1.0.0 or later

**Click command**: 
- `sonic-clear counters`

**Example**:
```
sonic# clear interface counters
sonic#

```

####show interface
Display information for one or all Ethernet interface

**Syntax**: `show interface [Ethernet <if-id>]`

**Parameters**:
- `if-id` - interface identification number

**Command mode**: EXEC

**Usage**: 
- `show interface` to display all the interface information

**Supported Releases**: 1.0.0 or later

**Example**:
```

sonic# show interface Ethernet 0
Ethernet0 is up, line protocol is down
Hardware is Eth
Interface index is 1
Mode of IPV4 address assignment: not-set
Mode of IPV6 address assignment: not-set
IP MTU 9100 bytes
LineSpeed 1GB, Auto-negotiation Enabled
Input statistics:
        0 packets, 0 octets
        0 64 byte pkts, 0 65-127 byte pkts, 0 128-255 byte pkts
        0 256-511 byte pkts, 0 512-1023 byte pkts, 0 1024-1518 byte pkts
        0 Multicasts, 0 Broadcasts, 0 Unicasts
        0 pause, 0 oversize, 0 throttle
        0 fragment, 0 jabber, 0 undersize
        0 error, 0 discarded, 0 unknown-protocol
Output statistics:
        0 packets, 0 octets
        0 64 byte pkts, 0 65-127 byte pkts, 0 128-255 byte pkts
        0 256-511 byte pkts, 0 512-1023 byte pkts, 0 1024-1518 byte pkts
        0 Multicasts, 0 Broadcasts, 0 Unicasts
        0 pause, 0 oversize, 0 throttle
        0 error, 0 discarded


```

####show interface status
Display information of one or all interfaces

**Syntax**: `show interface status [Ethernet <if-id>]`

**Parameters**:
- `if-id` - range of interface identification numbers seperated by comma or hiphen

**Command mode**: EXEC

**Usage**: 
- `show interface status` to display all the interface information

**Supported Releases**: 1.0.0 or later

**Click command**: 
- `show interfaces status [Ethernet<if-id>]`

**Example**:
```

sonic# show interface status
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Name           Admin   Oper    Speed     MTU       FEC     LANES                               ALIAS            VLAN      ASYM PFC  TYPE
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Ethernet0      up      down    400GB     9100      RS      33,34,35,36,37,38,39,40             Eth1/1           routed    N/A       QSFP28 or later
Ethernet8      up      down    400GB     9100      RS      41,42,43,44,45,46,47,48             Eth2/1           trunk     N/A       QSFP28 or later
Ethernet16     up      down    400GB     9100      RS      49,50,51,52,53,54,55,56             Eth3/1           routed    N/A       QSFP28 or later
Ethernet24     up      down    400GB     9100      RS      57,58,59,60,61,62,63,64             Eth4/1           routed    N/A       N/A
Ethernet32     up      down    400GB     9100      RS      65,66,67,68,69,70,71,72             Eth5/1           routed    N/A       N/A
Ethernet40     up      down    400GB     9100      RS      73,74,75,76,77,78,79,80             Eth6/1           routed    N/A       N/A
Ethernet48     up      down    400GB     9100      RS      81,82,83,84,85,86,87,88             Eth7/1           routed    N/A       N/A
Ethernet56     up      down    400GB     9100      RS      89,90,91,92,93,94,95,96             Eth8/1           routed    N/A       N/A
Ethernet64     up      down    400GB     9100      RS      1,2,3,4,5,6,7,8                     Eth9/1           routed    N/A       N/A
Ethernet72     up      down    400GB     9100      RS      9,10,11,12,13,14,15,16              Eth10/1          routed    N/A       N/A
Ethernet80     up      down    400GB     9100      RS      17,18,19,20,21,22,23,24             Eth11/1          routed    N/A       N/A
Ethernet88     up      down    400GB     9100      RS      25,26,27,28,29,30,31,32             Eth12/1          routed    N/A       N/A
Ethernet96     up      down    400GB     9100      RS      97,98,99,100,101,102,103,104        Eth13/1          routed    N/A       N/A
Ethernet104    up      down    400GB     9100      RS      105,106,107,108,109,110,111,112     Eth14/1          routed    N/A       N/A
Ethernet112    up      down    400GB     9100      RS      113,114,115,116,117,118,119,120     Eth15/1          routed    N/A       N/A
Ethernet120    up      down    400GB     9100      RS      121,122,123,124,125,126,127,128     Eth16/1          routed    N/A       N/A
Ethernet128    up      down    400GB     9100      RS      129,130,131,132,133,134,135,136     Eth17/1          routed    N/A       N/A
Ethernet136    up      down    400GB     9100      RS      137,138,139,140,141,142,143,144     Eth18/1          routed    N/A       N/A
Ethernet144    up      down    400GB     9100      RS      145,146,147,148,149,150,151,152     Eth19/1          routed    N/A       N/A
Ethernet152    up      down    400GB     9100      RS      153,154,155,156,157,158,159,160     Eth20/1          routed    N/A       N/A
Ethernet160    up      down    400GB     9100      RS      225,226,227,228,229,230,231,232     Eth21/1          routed    N/A       N/A
Ethernet168    up      down    400GB     9100      RS      233,234,235,236,237,238,239,240     Eth22/1          routed    N/A       N/A
Ethernet176    up      down    400GB     9100      RS      241,242,243,244,245,246,247,248     Eth23/1          routed    N/A       N/A
Ethernet184    up      down    400GB     9100      RS      249,250,251,252,253,254,255,256     Eth24/1          routed    N/A       N/A
Ethernet192    up      down    400GB     9100      RS      161,162,163,164,165,166,167,168     Eth25/1          routed    N/A       N/A
Ethernet200    up      down    400GB     9100      RS      169,170,171,172,173,174,175,176     Eth26/1          routed    N/A       N/A
Ethernet208    up      down    400GB     9100      RS      177,178,179,180,181,182,183,184     Eth27/1          routed    N/A       N/A
Ethernet216    up      down    400GB     9100      RS      185,186,187,188,189,190,191,192     Eth28/1          routed    N/A       N/A
Ethernet224    up      down    400GB     9100      RS      193,194,195,196,197,198,199,200     Eth29/1          routed    N/A       QSFP28 or later
Ethernet232    up      down    400GB     9100      RS      201,202,203,204,205,206,207,208     Eth30/1          routed    N/A       QSFP28 or later
Ethernet240    up      down    400GB     9100      RS      209,210,211,212,213,214,215,216     Eth31/1          routed    N/A       QSFP28 or later
Ethernet248    up      down    400GB     9100      RS      217,218,219,220,221,222,223,224     Eth32/1          routed    N/A       QSFP28 or later
sonic#

```

###show interface description
Display the description information of interfaces

**Syntax**: `show interface description [Ethernet <if-id>]`

**Parameters**:
- `if-id` - range of interface identification numbers seperated by comma or hiphen

**Command mode**: EXEC

**Usage**:
- `show interface description` to display all the interface description

**Supported Releases**: 1.1.0 or later

**Click command**: None

**Example**:
```
sonic# show interface description
---------------------------------------------------------------
Name                Description
---------------------------------------------------------------
Ethernet0           -
Ethernet8           -
Ethernet16          -
Ethernet24          This is a description for Ethernet24
Ethernet32          -
Ethernet40          -
Ethernet48          -
Ethernet56          -
Ethernet64          -
Ethernet72          -
Ethernet80          -
Ethernet88          -
Ethernet96          -
Ethernet104         -
Ethernet112         -
Ethernet120         -
Ethernet128         -
Ethernet136         -
Ethernet144         -
Ethernet152         -
Ethernet160         -
Ethernet168         -
Ethernet176         -
Ethernet184         -
Ethernet192         -
Ethernet200         -
Ethernet208         -
Ethernet216         -
Ethernet224         -
Ethernet232         -
Ethernet240         -
Ethernet248         -
```

####show interface counters
Display Counters information of one or multiple interfaces

**Syntax**: `show interface counters [Ethernet <if-id>]`

**Parameters**:
- `if-id` - range of interface identification numbers seperated by comma or hiphen

**Command mode**: EXEC

**Usage**: 
- `show interface counters` to display all the interface counters information

**Supported Releases**: 1.0.0 or later

**Click command**: 
- `show interface counters`

**Example**:
```

sonic# show interface counters Ethernet 8,16-24,40
---------------------------------------------------------------------------------------------------------------------------------------------------
Interface      State     RX_OK     RX_BPS(B/s) RX_UTIL(%) RX_ERR    RX_DRP    RX_OVR    TX_OK     TX_BPS(B/s) TX_UTIL(%) TX_ERR    TX_DRP    TX_OVR
---------------------------------------------------------------------------------------------------------------------------------------------------
Ethernet8      D         0         0.00        0.00       0         0         0         0         0.00        0.00       0         0         0
Ethernet16     D         0         0.00        0.00       0         0         0         0         0.00        0.00       0         0         0
Ethernet24     D         0         0.00        0.00       0         0         0         0         0.00        0.00       0         0         0
Ethernet40     D         0         0.00        0.00       0         0         0         0         0.00        0.00       0         0         0

```

####show interface transceiver
#####eeprom
Display Transceiver eeprom information of one or all interfaces

**Syntax**: `show interface transceiver eeprom [Ethernet <if-id>]`

**Parameters**:
- `if-id` - interface identification number

**Command mode**: EXEC

**Usage**: 
- `show interface transceiver eeprom` to display all the interface transceiver eeprom information

**Supported Releases**: 1.0.0 or later

**Click command**: 
- `show interfaces transceiver eeprom [Ethernet<if-id>]`

**Example**:
```
Ethernet48: SFP EEPROM detected
        Application Advertisement: N/A
        Connector: LC
        Encoding: 64B/66B
        Extended Identifier: GBIC/SFP defined by two-wire interface ID
        Extended RateSelect Compliance: Unknown
        Identifier: SFP/SFP+/SFP28
        Length Length OM1(10m): 15.0
        Nominal Bit Rate(100Mbs): 103
        Specification compliance:
                10G Ethernet Compliance: Unknown
                ESCON Compliance: Unknown
                Ethernet Compliance: Unknown
                Fibre Channel Link Length: Medium (M)
                Fibre Channel Speed: Unknown
                Fibre Channel Transmission Media: Unknown
                Fibre Channel Transmitter Technology: Unknown
                Infiniband Compliance: Unknown
                SFP+CableTechnology: Unknown
                SONET Compliance Codes: Unknown
        Vendor Date Code(YYYY-MM-DD Lot): 2021-12-23
        Vendor Name: FS
        Vendor OUI: 00-00-00
        Vendor PN: SFP-10GSR-85
        Vendor Rev:
        Vendor SN: F2140099960

```

####dom 
Display transceiver Dom information of one or all interface 

**Syntax**: `show interface transceiver eeprom dom [Ethernet <if-id>]`

**Parameters**:
- `if-id` - interface identification number

**Command mode**: EXEC

**Usage**: 
- `show interface transceiver eeprom dom` to display all the interface transceiver eeprom dom information

**Supported Releases**: 1.0.0 or later

**Click command**: 
- `show interface transceiver eeprom -d [Ethernet<if-id>]`

**Example**:
```
sonic# show interface transceiver eeprom dom Ethernet 48
Ethernet48: SFP EEPROM detected
Application Advertisement: N/A
        Connector: LC
        Encoding: 64B/66B
        Extended Identifier: GBIC/SFP defined by two-wire interface ID
        Extended RateSelect Compliance: Unknown
        Identifier: SFP/SFP+/SFP28
        Length Length OM1(10m): 15.0
        Nominal Bit Rate(100Mbs): 103
        Specification compliance:
                10G Ethernet Compliance: Unknown
                ESCON Compliance: Unknown
                Ethernet Compliance: Unknown
                Fibre Channel Link Length: Medium (M)
                Fibre Channel Speed: Unknown
                Fibre Channel Transmission Media: Unknown
                Fibre Channel Transmitter Technology: Unknown
                Infiniband Compliance: Unknown
                SFP+CableTechnology: Unknown
                SONET Compliance Codes: Unknown
        Vendor Date Code(YYYY-MM-DD Lot): 2021-12-23
        Vendor Name: FS
        Vendor OUI: 00-00-00
        Vendor PN: SFP-10GSR-85
        Vendor Rev:
        Vendor SN: F2140099960
        Monitor Data:
                RX1Power: 0.595dBm
                TX1Bias: 5.904mA
                TX1Power: 0.568dBm
                Temperature: 21.496C
                Vcc: 3.319Volts
        Threshold Data:
                TempHighAlarm     : 80.0C
                TempHighWarning   : 70.0C
                TempLowAlarm      : -10.0C
                TempLowWarning    : 0.0C
                VccHighAlarm      : 3.63Volts
                VccHighWarning    : 3.465Volts
                VccLowAlarm       : 2.97Volts
                VccLowWarning     : 3.135Volts
                RxPowerHighAlarm  : 1.0dBm
                RxPowerHighWarning: -1.0dBm
                RxPowerLowAlarm   : -11.898dBm
                RxPowerLowWarning : -9.901dBm
                TxBiasHighAlarm   : 12.0mA
                TxBiasHighWarning : 10.5mA
                TxBiasLowAlarm    : 1.0mA
                TxBiasLowWarning  : 2.5mA
                TxPowerHighAlarm  : 1.0dBm
                TxPowerHighWarning: -1.0dBm
                TxPowerLowAlarm   : -9.3dBm
                TxPowerLowWarning : -7.3dBm

```

#####presence
Display transceiver presence information of one or all interfaces

**Syntax**: `show interface transceiver presence [Ethernet <if-d>]`

**Parameters**:
- `if-id` - interface identification number

**Command mode**: EXEC

**Usage**: 
- `show interface transceiver presence` to display all the interface transceiver presence information

**Supported Releases**: 1.0.0 or later

**Click command**: 
- `show interfaces transceiver presence [Ethernet<if-id>]`

**Example**:
```
sonic# show interface transceiver presence
Port           Presence
------------------------------
Ethernet0      Not Present
Ethernet1      Not Present
Ethernet2      Not Present
Ethernet3      Not Present
Ethernet4      Not Present
Ethernet5      Not Present
Ethernet6      Not Present
Ethernet7      Not Present
Ethernet8      Not Present
Ethernet9      Not Present
Ethernet10     Not Present
Ethernet11     Not Present
Ethernet12     Not Present
Ethernet13     Not Present
Ethernet14     Not Present
Ethernet15     Not Present
Ethernet16     Not Present
Ethernet17     Not Present
Ethernet18     Not Present
Ethernet19     Not Present
Ethernet20     Not Present
Ethernet21     Not Present
Ethernet22     Not Present
Ethernet23     Not Present
Ethernet24     Not Present
Ethernet25     Not Present
Ethernet26     Not Present
Ethernet27     Not Present
Ethernet28     Not Present
Ethernet29     Not Present
Ethernet30     Not Present
Ethernet31     Not Present
Ethernet32     Not Present
Ethernet33     Not Present
Ethernet34     Not Present
Ethernet35     Not Present
Ethernet36     Not Present
Ethernet37     Not Present
Ethernet38     Not Present
Ethernet39     Not Present
Ethernet40     Not Present
Ethernet41     Not Present
Ethernet42     Not Present
Ethernet43     Not Present
Ethernet44     Not Present
Ethernet45     Not Present
Ethernet46     Not Present
Ethernet47     Not Present
Ethernet48     Present
Ethernet49     Not Present
Ethernet50     Not Present
Ethernet51     Not Present
Ethernet52     Not Present
Ethernet53     Not Present
Ethernet54     Not Present
Ethernet55     Not Present

```

#####error-status
Display transceiver error status information of one or all interfaces

**Syntax**: `show interface transceiver error-status [Ethernet <if-d>]`

**Parameters**:
- `if-id` - interface identification number

**Command mode**: EXEC

**Usage**: 
- `show interface transceiver error-status` to display all the interface transceiver error-status information

**Supported Releases**: 1.0.0 or later

**Click command**: 
- `show interfaces transceiver error-status [Ethernet<if-id>]`

**Example**:
```
sonic# show interface transceiver error-status
Port           Error Status
------------------------------
Ethernet0      Unplugged
Ethernet1      Unplugged
Ethernet2      Unplugged
Ethernet3      Unplugged
Ethernet4      Unplugged
Ethernet5      Unplugged
Ethernet6      Unplugged
Ethernet7      Unplugged
Ethernet8      Unplugged
Ethernet9      Unplugged
Ethernet10     Unplugged
Ethernet11     Unplugged
Ethernet12     Unplugged
Ethernet13     Unplugged
Ethernet14     Unplugged
Ethernet15     Unplugged
Ethernet16     Unplugged
Ethernet17     Unplugged
Ethernet18     Unplugged
Ethernet19     Unplugged
Ethernet20     Unplugged
Ethernet21     Unplugged
Ethernet22     Unplugged
Ethernet23     Unplugged
Ethernet24     Unplugged
Ethernet25     Unplugged
Ethernet26     Unplugged
Ethernet27     Unplugged
Ethernet28     Unplugged
Ethernet29     Unplugged
Ethernet30     Unplugged
Ethernet31     Unplugged
Ethernet32     Unplugged
Ethernet33     Unplugged
Ethernet34     Unplugged
Ethernet35     Unplugged
Ethernet36     Unplugged
Ethernet37     Unplugged
Ethernet38     Unplugged
Ethernet39     Unplugged
Ethernet40     Unplugged
Ethernet41     Unplugged
Ethernet42     Unplugged
Ethernet43     Unplugged
Ethernet44     Unplugged
Ethernet45     Unplugged
Ethernet46     Unplugged
Ethernet47     Unplugged
Ethernet48     OK
Ethernet49     Unplugged
Ethernet50     Unplugged
Ethernet51     Unplugged
Ethernet52     Unplugged
Ethernet53     Unplugged
Ethernet54     Unplugged
Ethernet55     Unplugged

```

#####summary
Display transceiver summary information for all interfaces

**Syntax**: `show interface transceiver summary`

**Command mode**: EXEC

**Usage**: 
- `show interface transceiver summary` to display all the interface transceiver summary information

**Supported Releases**: 4.0.0 or later

**Click command**: 
- `show interfaces transceiver summary`

**Example**:
```
Celestica-DS2000# show interface transceiver summary
Interface      Vendor Name         Part Number         Qualified
------------------------------------------------------------------
Ethernet4      Amphenol            NDCCDA-0003         Yes
Ethernet6      Amphenol            NDCCDA-0003         Yes
Ethernet46     FINISAR CORP.       FTLX8574D3BCL       Yes
Ethernet47     FINISAR CORP.       FTLX8574D3BCL       Yes
Celestica-DS2000#
```

###Breakout
####config interface breakout
Configure breakout modes of an interface

**Syntax**: `interface breakout Ethernet <if-id> <breakout_mode>`

**Parameters**:
- `if-id` - interface identification number
- `breakout_mode` - breakout mode to be configured

**Command mode**: CONFIG

**Usage**: 
- `no interface breakout <if-id>` to return interface to default breakout mode

**Supported Releases**: 1.1.0 or later

**Click command**: 
- `config interface breakout Ethernet<if-id> <breakout_mode>`

**Example**:
```
sonic(config)# interface breakout Ethernet 16 
  <1x400G/2x100G/2x40G/4x100G/1x100G(4)/1x40G(4)/4x25G(4)/4x10G(4)>  Breakout mode
sonic(config)# interface breakout Ethernet 16 4x100G
Do you want to Breakout the port, continue? [y/N]: y
{}
Above Config cannot be verified, It may cause harm to system, continue? [y/N]: y
sonic(config)#


sonic(config)# interface breakout Ethernet 8
1x100G(4) 1x400G    1x40G(4)  2x100G    2x40G     4x100G    4x10G(4)  4x25G(4)
sonic(config)# interface breakout Ethernet 8 4x100G
Do you want to Breakout the port, continue? [y/N]: y
{}
Above Config cannot be verified, It may cause harm to system, continue? [y/N]: y
%Error: Dependencies Exist. No further action will be taken:
["/sonic-interface:sonic-interface/INTERFACE/INTERFACE_LIST[name='Ethernet8']/name", "/sonic-interface:sonic-interface/INTERFACE/INTERFACE_IPPREFIX_LIST[name='Ethernet8'][ip-prefix='1.2.3.4/24']/name"]
sonic(config)#

```

####show interface breakout
Display breakout information of one or all interafaces

**Syntax**: `show interface breakout [Ethernet <if-id>]`

**Parameters**:
- `if-id` - interface identification number

**Command mode**: EXEC

**Usage**: 
- `show interface breakout` displays breakout information of all interfaces

**Supported Releases**: 1.1.0 or later

**Click command**: 
- `show interface breakout`

**Example**:
```
sonic# show interface breakout Ethernet 8
Ethernet8:
        Breakout modes:
            1x100G(4): ['Eth2/1']
            1x400G: ['Eth2/1']
            1x40G(4): ['Eth2/1']
            2x100G: ['Eth2/1', 'Eth2/5']
            2x40G: ['Eth2/1', 'Eth2/5']
            4x100G: ['Eth2/1', 'Eth2/3', 'Eth2/5', 'Eth2/7']
            4x10G(4): ['Eth2/1', 'Eth2/2', 'Eth2/3', 'Eth2/4']
            4x25G(4): ['Eth2/1', 'Eth2/2', 'Eth2/3', 'Eth2/4']
        Child ports: Ethernet8
        Child port speed: 400G
        Current breakout mode: 1x400G
        Default breakout mode: 1x400G
        Autoneg: off
        Fec: rs
        Lanes: 41,42,43,44,45,46,47,48
        Index: 2,2,2,2,2,2,2,2

```

### Ethernet Interface commands
#### shutdown
Disable the administrative status of the interface

**Syntax** : `shutdown`

**Parameters** : none

**Command mode** : Ethernet interface mode, portchannel interface mode, vlan interface mode

**Usage**       : Use `no shutdown` to enable the administrative status of the interface

**Supported Releases** :  1.0.0 or later

**Click command** : 
- config interface shutdown <interface_name>
- config interface startup <interface_name>

**Example**
```
sonic(config)# interface Ethernet 0
sonic(conf-if-Ethernet0)# shutdown
sonic(conf-if-Ethernet0)#
sonic(conf-if-Ethernet0)# no shutdown
sonic(conf-if-Ethernet0)#
```
#### mtu
Configure mtu for an interface

**Syntax** : `mtu <mtu-bytes>`

**Parameters** :
- `mtu-bytes` - maximum transmit unit in bytes, excluding Ethernet header and FCS length, default = 9100

**Command mode** : Ethernet interface mode, portchannel interface mode

**Usage**       : Use `no mtu` to reset the interface MTU to default value

**Supported Releases** :  1.0.0 or later

**Click command** : config interface mtu <interface_name> <interface_mtu>

**Example**
```
sonic(config)# interface Ethernet 4
sonic(conf-if-Ethernet4)# mtu 6000
sonic(conf-if-Ethernet4)#
sonic(conf-if-Ethernet4)# no mtu
sonic(conf-if-Ethernet4)#

```
#### tpid
Configure tpid for the interface

**Syntax** : `tpid <tpid-val>`

**Parameters** :
- `tpid-val` - one of the tpid value <0x8100/0x88a8/0x9100/0x9200>, default = 0x8100 

**Command mode** : Ethernet interface mode

**Usage**       : Use `no tpid` to reset the interface tpid to default value

**Supported Releases** :  1.0.0 or later

**Click command** : config interface tpid <interface_name> <interface_tpid>

**Example**
```
sonic(config)# interface Ethernet 8
sonic(conf-if-Ethernet8)# tpid 0x9100
sonic(conf-if-Ethernet8)#
sonic(conf-if-Ethernet8)# no tpid
sonic(conf-if-Ethernet8)#

```
#### channel-group
Configure an interface as a portchannel member

**Syntax** : `channel-group <po-id>`

**Parameters** :
- `po-id` - Portchannel identifier to which this interface needs to be bundled, range 1-256

**Command mode** : Ethernet interface mode

**Usage**       : Use `no channel-group` to remove the interface as a portchannel member

**Supported Releases** :  1.0.0 or later

**Click command** : config portchannel member add  <portchannel_name> <port_name>

**Example**
```
sonic(config)# interface Ethernet 0
sonic(conf-if-Ethernet0)# channel-group 201
sonic(conf-if-Ethernet0)# no channel-group
sonic(conf-if-Ethernet0)#

```

#### wred queue
Applies a WRED profile to interface queues.

**Syntax** : `wred queue <queue-index> profile <profile-name>`

**Parameters** :
- `queue-index` - Individual queue index. valid value: <0-7>
- `profile-name` - Alphanumeric string including - and _ (Max: 32 characters)

**Command mode** : Physical interface

**Usage**       :
- Use `no wred queue <queue-index> profile` to remove a WRED drop profile from interface queues.
- By default, no WRED drop profile is applied to an interface queue.

**Supported Releases** :  1.0.0 or later

**Click command** : None

**Example**
```
sonic(conf-if-Ethernet1)# wred queue 1 profile test1
sonic(conf-if-Ethernet1)# wred queue 3 profile 12

sonic(conf-if-Ethernet1)# no wred queue 1 profile
sonic(conf-if-Ethernet1)# no wred queue 3 profile
```
#### advertise speeds
Configure advertised speeds on a interface.

**Syntax** : advertise-speed <speed-value>

**Parameters** :
- `speed-value` - A supported advertise speed value for the interface


**Command mode** : Physical interface

**Usage**       : Use `no advertise-speed` to remove the all the configured advertise speeds or use `no advertise-speed <speed-val>' to remove a particular configured advertised speed value from the interface

**Supported Releases** :  1.0.0 or later

**Click command** : config interface advertised-speeds <Interface_name> <speed_value>

**Example**
```
sonic(conf-if-Ethernet36)# advertise-speed 10
sonic(conf-if-Ethernet36)# advertise-speed 100
sonic(conf-if-Ethernet36)# no advertise-speed 10
sonic(conf-if-Ethernet36)# no advertise-speed
```
#### advertise type
Configure advertised type on a interface.

**Syntax** : advertise-type <type-value>

**Parameters** :
- `type-value` - A type value from XLAUI,SR2,SFI,XFI,XAUI,XGMII,LR,CR4,CAUI4,SR4,KR2,LR4,CAUI,KR,CR2,GMII,CR,SR,KR4 options.


**Command mode** : Physical interface

**Usage**       : Use `no advertise-type` to remove the all the configured advertise types or use `no advertise-type <type-val>' to remove a particular configured advertised type value from the interface

**Supported Releases** :  1.0.0 or later

**Click command** : config interface advertised-type <Interface_name> <type_value>

**Example**
```
sonic(conf-if-Ethernet36)# advertise-type CR
sonic(conf-if-Ethernet36)# advertise-type KR
sonic(conf-if-Ethernet36)# no advertise-type CR
sonic(conf-if-Ethernet36)# no advertise-type
```

#### type
Configure type on a interface.

**Syntax** : type <type-value>

**Parameters** :
- `type-value` - A type value from XLAUI,SR2,SFI,XFI,XAUI,XGMII,LR,CR4,CAUI4,SR4,KR2,LR4,CAUI,KR,CR2,GMII,CR,SR,KR4 options.


**Command mode** : Physical interface

**Usage**       : Use `no  type` to remove the the configured type on the interface

**Supported Releases** :  1.0.0 or later

**Click command** : config interface type <Interface_name> <type_value>

**Example**
```
sonic(conf-if-Ethernet36)# type CR
sonic(conf-if-Ethernet36)# no type
```
```

#### fec
Configure fec on a interface.

**Syntax** : fec <fec-value>

**Parameters** :
- `fec-value` - A fec value from FC,RS,none options.


**Command mode** : Physical interface

**Usage**       : Use `no fec` to remove the the configured fec on the interface

**Supported Releases** :  4.0.0 or later

**Click command** : config interface fec <Interface_name> <fec_value>

**Example**
```
Celestica-DS1000(conf-if-Ethernet1)# fec FC
Celestica-DS1000(conf-if-Ethernet1)# no fec

```
```

#### link-training
Configure link-training on a interface.

**Syntax** : link-training <link-training-value>

**Parameters** :
- `link-training-value` - A link-training value from on,off options.


**Command mode** : Physical interface

**Usage**       : Use `no link-training` to remove the the configured link-training on the interface

**Supported Releases** :  4.0.0 or later

**Click command** : config interface link-training <Interface_name> <link-training_value>

**Example**
```
Celestica-DS1000(conf-if-Ethernet1)# link-training on
Celestica-DS1000(conf-if-Ethernet1)# no link-training

```


### PortChannel Interface commands

TBD
### Tunnel Interface commands
GRE tunnel interface commands
### Tunnel source-ip
Configure source ip address of a tunnel interface

**Syntax** : `source-ip <tnl-sip>`

**Parameters** :
- `tnl-sip` - IPv4 address that needs to used as a tunnel source

**Command mode** : Tunnel interface mode

**Usage**       : Use `no source-ip` to remove the tunnel source ip configuraiton

**Supported Releases** :  2.0.0 or later

**Click command** : config tunnel add <tunnel_name> <tunnel_src_ip> <tunnel_dst_ip>

**Example**
```
sonic(conf-if-Tunnel100)# source-ip 1.1.1.1
sonic(conf-if-Tunnel100)# no source-ip
sonic(conf-if-Tunnel100)#


```
### Tunnel destinaiton-ip
Configure destination ip address of a tunnel interface

**Syntax** : `destination-ip <tnl-dip>`

**Parameters** :
- `tnl-dip` - IPv4 address that needs to used as a tunnel destination

**Command mode** : Tunnel interface mode

**Usage**       : Use `no destination-ip` to remove the tunnel destination ip configuraiton

**Supported Releases** :  2.0.0 or later

**Click command** : config tunnel add <tunnel_name> <tunnel_src_ip> <tunnel_dst_ip>

**Example**
```
sonic(conf-if-Tunnel100)# destination-ip 2.2.2.2
sonic(conf-if-Tunnel100)# no destination-ip
sonic(conf-if-Tunnel100)#

```
### Tunnel ip
Configure ip address for a tunnel interface

**Syntax** : `ip address  <tnl-ip-mask>`

**Parameters** :
- `tnl-ip-mask` - Tunnel ip address and network mask in format A.B.C.D/mask  

**Command mode** : Tunnel interface mode

**Usage**       : Use `no ip address <tnl-ip-mask>` to remove the tunnel ip configuraiton

**Supported Releases** :  2.0.0 or later

**Click command** : config interface ip add <tunnel_name> <tnl-ip-mask>

**Example**
```
sonic(conf-if-Tunnel100)# ip address 3.3.3.3/24
sonic(conf-if-Tunnel100)# no ip address 3.3.3.3/24
sonic(conf-if-Tunnel100)#

```
### VLAN Interface commands
TBD

### Loopback Interface commands
TBD

## Layer 2
### VLAN
#### switchport access vlan
Configure the untagged vlan membership for the port, vlan

**Syntax** : `switchport access vlan <vlan-id>`

**Parameters** :
- `vlan-id` - vlan identifier range 1-4094

**Command mode** : Ethernet and Portchannel interface mode

**Usage**       : Use `no switchport access vlan` to remove the access vlan configuration.

**Supported Releases** :  1.0.0 or later

**Click command** : config vlan member add --u <vid> port

**Example**
```
sonic(conf-if-Ethernet0)# switchport access vlan 40
sonic(conf-if-Ethernet0)#
sonic(conf-if-Ethernet0)# no switchport access vlan
sonic(conf-if-Ethernet0)#
```

#### switchport trunk allowed vlan add
Configure the tagged vlan membership for the port, vlan 

**Syntax** : `switchport trunk allowed vlan add <vlan-id>`

**Parameters** :
- `vlan-id` - vlan identifier range 1-4094

**Command mode** : Ethernet and Portchannel interface mode

**Usage**       : Use ` no switchport trunk allowed vlan <vlan-id>` to remove the tagged vlan membership configuration.

**Supported Releases** :  1.0.0 or later

**Click command** : config vlan member add  <vid> port

**Example**
```
sonic(conf-if-Ethernet0)# switchport trunk allowed vlan add 40
sonic(conf-if-Ethernet0)#
sonic(conf-if-Ethernet0)# no switchport trunk allowed vlan 40
sonic(conf-if-Ethernet0)#
```



### Show commands

#### show vlan
Displays the configured vlan information

**Syntax**: `show vlan [vlan-id]`

**Parameters**  :
- `vlan-id' - vlan identifier.

**Command mode** : Exec mode

**Usage**       : If optional vlan identifier is not given all configured vlan information will be displayed.

**Click command** : show vlan brief

**Example**
```
sonic# show vlan
------------------------------------------------------------
Name       Id         Members              Mode
------------------------------------------------------------
Vlan100    100        Ethernet0            tagged
------------------------------------------------------------
Vlan200    200
------------------------------------------------------------
sonic# show vlan 100
------------------------------------------------------------
Name       Id         Members              Mode
------------------------------------------------------------
Vlan100    100        Ethernet0            tagged
------------------------------------------------------------
sonic#

```
### PORTCHANNEL
### Show commands
#### show portchannel summary
Displays the configured portchannel information

**Syntax**: `show portchannel summary [po-id]`

**Parameters**  :
- `po-id' - port-channel identifier.

**Command mode** : Exec mode

**Usage**       : If optional port-channel identifier is not given all configured port-channel information will be displayed.

**Click command** : show interfaces portchannel

**Example**
```
sonic# show portchannel summary
--------------------------------------------------------------------------------
Name                 Group     State     Protocol  Members        Lag-Status
--------------------------------------------------------------------------------
PortChannel100       100       DOWN      lacp      Ethernet4      Deselected
--------------------------------------------------------------------------------
PortChannel200       200       DOWN      lacp
--------------------------------------------------------------------------------
sonic# show portchannel summary 100
--------------------------------------------------------------------------------
Name                 Group     State     Protocol  Members        Lag-Status
--------------------------------------------------------------------------------
PortChannel100       100       DOWN      lacp      Ethernet4      Deselected
--------------------------------------------------------------------------------
sonic#

```

### LLDP

#### lldp enable
Configure to enable globally. LLDP is enabled globally by default.


**Syntax** : `lldp enable`

**Parameters** : `none`

**Command mode** : CONFIG

**Usage**       : Use `no lldp enable` to disable the LLDP globally

**Supported Releases** :  1.0.0 or later

**Click command** : none

**Example**

```

sonic(config)# lldp enable
sonic(config)#
sonic(config)# no lldp enable
sonic(config)#
sonic(config)#


```
#### lldp timer
Configures the interval at which the LLDP hello packets are sent to peers

**Syntax**: `lldp timer <seconds>`

**Parameters**  :
- `seconds` - Enter the interval in seconds from 5 to 254, default = 30

**Command mode** : CONFIG

**Usage**       : Use `no lldp timer` to configure the default value.

**Supported Releases** :  1.0.0 or later

**Click command** : `none`

**Example**
```
sonic(config)# lldp timer 20
sonic(config)# no lldp timer
sonic(config)#
```

#### lldp system-description
Configures the system-description of the 'system-description' TLV in the LLDP transmit packets

**Syntax**: `lldp system-description <string>`

**Parameters**  :
- `string` - LLDP system description string

**Command mode** : CONFIG

**Usage**       : Use `no lldp system-description` to configure the default value.

**Supported Releases** :  1.0.0 or later

**Click command** : `none`

**Example**
```
sonic(config)# lldp system-description TOR-Device-North-10
sonic(config)#

sonic(config)# no lldp system-description
sonic(config)#

```

#### lldp tlv-select
Configures to enable TLVs  in the LLDP transmit packets

**Syntax**: `lldp tlv-select {management-address | system-capabilities}`

**Parameters**  :
- `management-address/system-capabilities` - TLVs to be enabled

**Command mode** : CONFIG

**Usage**       : Use `no lldp tlv-select {management-address/system-capabilities}` to disable the TLV

**Supported Releases** :  1.0.0 or later

**Click command** : `none`

**Example**
```
sonic(config)# lldp tlv-select management-address
sonic(config)#
sonic(config)# lldp tlv-select system-capabilities
sonic(config)#
sonic(config)# no lldp tlv-select management-address
sonic(config)#
sonic(config)# no lldp tlv-select system-capabilities
sonic(config)#

```

#### interface lldp enable 
Configure to enable LLDP on an interface. LLDP is enabled on all interfaces by default.


**Syntax** : `lldp enable`

**Parameters** : `none`

**Command mode** : Ethernet interface mode

**Usage**       : Use `no lldp enable` to disable the LLDP on an interface

**Supported Releases** :  1.0.0 or later

**Click command** : none

**Example**

```

sonic(conf-if-Ethernet0)# lldp enable
sonic(conf-if-Ethernet0)#
sonic(conf-if-Ethernet0)# no lldp enable
sonic(conf-if-Ethernet0)#

```

#### LLDP MED
Configure to enable LLDP MED capabilities on an interface.

**Syntax** : ` lldp med network-policy application <app-type> [dscp <dscp-val>] [priority <dot1p-val>] [vlan-id <vlan-val>] [tagged]`

**Parameters** :
- `app-type`                      -  LLDP MED application type. Valid application types are `voice`,`voice-signaling`,`guest-voice`,`guest-voice-signaling`,`softphone-voice`,`video-conferencing`,`streaming-video`,`video-signaling`
- `dscp-val`                      -  dscp value for the application type (valid range 0-63)
- `dot1p-val`                     -  dot1p value for the application type (valid range 0-7)
- `vlan-val`                      -  vlan value for the application type (valid range 1-4094)
- `tagged`                        -  tagged vlan flag for the application type

**Command mode** : Ethernet interface mode

**Usage**       : Use `no lldp med network-policy` to disable the LLDP MED network policy on an interface

**Supported Releases** :  2.0.0 or later

**Click command** : ```config lldp med network-policy application modify <interface_name> <application_type> [--dscp INTEGER] [--priority INTEGER] [--tagged {true|false}] [--vlan_id INTEGER]```

**Example**

```
Celestica-DS1000(conf-if-Ethernet0)# lldp med network-policy application voice dscp 3 priority 2 vlan-id 100 tagged
Celestica-DS1000(conf-if-Ethernet0)#
Celestica-DS1000(conf-if-Ethernet0)# no lldp med network-policy
Celestica-DS1000(conf-if-Ethernet0)#

```

### Show commands
#### show lldp table
Displays the discovered LLDP neighbor information in tabular format

**Syntax**: `show lldp table`

**Parameters**  : `none`

**Command mode** : Exec mode

**Usage**       : `show lldp table`

**Click command** : `show lldp table`

**Example**
```
sonic# show lldp table
------------------------------------------------------------------------------------------------------
LocalPort           RemoteDevice        RemotePortID        Capability           RemotePortDescr
-------------------------------------------------------------------------------------------------------
Ethernet0           sonic               Ethernet0           BR                  Ethernet1/0/1
Ethernet1           sonic               Ethernet1           BR                  Ethernet1/0/2
Ethernet2           sonic               Ethernet2           BR                  Ethernet1/0/3
Ethernet3           sonic               Ethernet3           BR                  Ethernet1/0/4
Ethernet4           sonic               Ethernet4           BR                  Ethernet1/0/5
Ethernet5           sonic               Ethernet5           BR                  Ethernet1/0/6
Ethernet6           sonic               Ethernet6           BR                  Ethernet1/0/7
Ethernet7           sonic               Ethernet7           BR                  Ethernet1/0/8
eth0                ToR-A05-A06         Ethernet4           BR                  Eth1/5

```
#### show lldp neighbor
Displays the LLDP MED configuration

**Syntax**: `show lldp neighbor [interface_name]`

**Parameters**  :
- `interface_name' - Enter the interface name for which the discovered LLDP information is needed.

**Command mode** : Exec mode

**Usage**       : If interface keyword is not given all discovered LLDP neighbor information will be displayed.

**Click command** : show lldp  neighbors

**Example**
```
sonic# show lldp neighbor
-----------------------------------------------------------
LLDP Neighbors
-----------------------------------------------------------
Interface:   Ethernet0,via: LLDP
  Chassis:
    ChassisID:    34:ad:61:f1:a3:a4
    SysName:      sonic
    SysDescr:     SONiC Software Version: SONiC.prime_master.0-afbfa02b9 - HwSku: CELESTICA-BELGITE - Distribution: Debian 11.6 - Kernel: 5.10.0-8-2-amd64
    Capability:   MAC_BRIDGE, ON
    Capability:   ROUTER, ON
  Port
    PortID:       Ethernet0
    PortDescr:    Ethernet1/0/1
-----------------------------------------------------------
Interface:   Ethernet1,via: LLDP
  Chassis:
    ChassisID:    34:ad:61:f1:a3:a4
    SysName:      sonic
    SysDescr:     SONiC Software Version: SONiC.prime_master.0-afbfa02b9 - HwSku: CELESTICA-BELGITE - Distribution: Debian 11.6 - Kernel: 5.10.0-8-2-amd64
    Capability:   MAC_BRIDGE, ON
    Capability:   ROUTER, ON
  Port
    PortID:       Ethernet1
    PortDescr:    Ethernet1/0/2


sonic# show lldp neighbor Ethernet7
-----------------------------------------------------------
LLDP Neighbors
-----------------------------------------------------------
Interface:   Ethernet7,via: LLDP
  Chassis:
    ChassisID:    0c:48:c6:e1:e0:b5
    SysName:      sonic
    SysDescr:     SONiC Software Version: SONiC.prime_master.0-e2773f7b9 - HwSku: CELESTICA-BELGITE - Distribution: Debian 11.6 - Kernel: 5.10.0-8-2-amd64
    Capability:   MAC_BRIDGE, ON
    Capability:   ROUTER, ON
  Port
    PortID:       Ethernet7
    PortDescr:    Ethernet1/0/8
-----------------------------------------------------------

```
#### show lldp med
Displays the configured LLDP MED information in tabular format

**Syntax**: `show lldp med [interface_name]`

**Parameters**  :
- `interface_name' - Enter the interface name for which the discovered LLDP MED information is needed.

**Command mode** : Exec mode

**Usage**       : If interface keyword is not given all configured LLDP MED information will be displayed.

**Click command** : `show lldp med`

**Example**
```
Celestica-DS1000# show lldp med
------------------------------------------------------------------------------
Port        MED-Application          VlanId    DSCP      Dot1p     Tagged
------------------------------------------------------------------------------
Ethernet0   voice                    3094      15        7         false
------------------------------------------------------------------------------
Celestica-DS1000#


```


### MCLAG

#### mclag domain
Configure mclag domain.

**Syntax** : `mclag domain <mlag-id>`

**Parameters** : 
 - `mlag-id` - mclag domain identifier

**Command mode** : CONFIG

**Usage**       : Use `no mclag domain <mlag-id>` to delete the mclag domain

**Supported Releases** :  1.0.0 or later

**Click command** : none

**Example**

```
sonic(config)# mclag domain 1
sonic(config-mclag-domain-1)#
sonic(config-mclag-domain-1)# no mclag domain 1
sonic(config)#

```

#### source-ip
Configure mclag domain source-ip address

**Syntax** : `source-ip <mlag-sip>`

**Parameters** : 
 - `mlag-sip` - source ip for the mclag domain

**Command mode** : MCLAG domain mode

**Usage**       : Use `no source-ip` to delete the configured source-ip 

**Supported Releases** :  1.0.0 or later

**Click command** : config mclag add <domain_id> <source_ip_addr> <peer_ip_addr> <peer_ifname>

**Example**

```
sonic(config-mclag-domain-1)# source-ip 10.208.140.125
sonic(config-mclag-domain-1)#
sonic(config-mclag-domain-1)# no source-ip
sonic(config-mclag-domain-1)#
sonic(config-mclag-domain-1)#

```

#### peer-ip
Configure mclag domain peer-ip address

**Syntax** : `peer-ip <mlag-peer-ip>`

**Parameters** : 
 - `mlag-peer-ip` - peer ip for the mclag domain

**Command mode** : MCLAG domain mode

**Usage**       : Use `no peer-ip` to delete the configured source-ip 

**Supported Releases** :  1.0.0 or later

**Click command** : config mclag add <domain_id> <source_ip_addr> <peer_ip_addr> <peer_ifname>

**Example**

```
sonic(config-mclag-domain-1)# peer-ip 10.208.140.126
sonic(config-mclag-domain-1)#
sonic(config-mclag-domain-1)# no peer-ip
sonic(config-mclag-domain-1)#

```

#### keepalive
Configure mclag domain keepalive time interval

**Syntax** : `keepalive <ka-sec>`

**Parameters** : 
 - `ka-sec` - keep alive time interval of the MCLAG domain in sec, range 1-60, default = 1 sec

**Command mode** : MCLAG domain mode

**Usage**       : Use `no keepalive` to set the keepalive timer interval to default value

**Supported Releases** :  1.0.0 or later

**Click command** : config mclag keepalive-interval <domain_id> <time_in_secs>

**Example**
```
sonic(config-mclag-domain-1)# keepalive 3
sonic(config-mclag-domain-1)#
sonic(config-mclag-domain-1)# no keepalive
sonic(config-mclag-domain-1)#

```

#### session-timeout
Configure mclag domain session timeout period

**Syntax** : `session-timeout <st-sec>`

**Parameters** : 
 - `st-sec` - session timeout period of the MCLAG domain in sec, range 3-3600, default = 15 sec

**Command mode** : MCLAG domain mode

**Usage**       : Use `no session-timeout` to set the session timeout period to default value

**Supported Releases** :  1.0.0 or later

**Click command** : config mclag session-timeout <domain_id> <time_in_secs>

**Example**

```
sonic(config-mclag-domain-1)# session-timeout 40
sonic(config-mclag-domain-1)#
sonic(config-mclag-domain-1)# no session-timeout
sonic(config-mclag-domain-1)#

```

#### peer-link
Configure mclag domain peer-link interface

**Syntax** : `peer-link {Ethernet <eth-if-id> | PortChannel <po-if-id>}`

**Parameters** : 
- `eth-if-id` - Ethernet interface identifier 
- `po-if-id` - PortChannel identifier within the range of 1 - 256

**Command mode** : MCLAG domain mode

**Usage**       : Use `no peer-link` to delete the configured peer-link interface 

**Supported Releases** :  1.0.0 or later

**Click command** : config mclag add <domain_id> <source_ip_addr> <peer_ip_addr> <peer_ifname>

**Example**

```
sonic(config-mclag-domain-1)# peer-link PortChannel 100
sonic(config-mclag-domain-1)#
sonic(config-mclag-domain-1)# no peer-link
sonic(config-mclag-domain-1)#
sonic(config-mclag-domain-1)# peer-link Ethernet 0
sonic(config-mclag-domain-1)#
sonic(config-mclag-domain-1)# no peer-link
sonic(config-mclag-domain-1)#
```

#### system-mac
Configure mclag domain system-mac address

**Syntax** : `system-mac <mac_address>'

**Parameters** : 
- `mac-address` - MCLAG system mac address to be used for the MCLAG interfaces 


**Command mode** : MCLAG domain mode

**Usage**       : Use `no system-mac` to delete the configured system-mac interface 

**Supported Releases** :  2.0.0 or later

**Click command** : config mclag add <domain_id> <source_ip_addr> <peer_ip_addr> <peer_ifname> <system_mac>

**Example**

```
sonic(config-mclag-domain-1)#
sonic(config-mclag-domain-1)# system-mac 00:00:00:00:44:55
sonic(config-mclag-domain-1)#

```
#### session-vrf
Configure mclag session vrf name 
**Syntax** : `session-vrf <vrf_name>'

**Parameters** : 
- `vrf_name` - VRF to be used for the MCLAG session formation


**Command mode** : MCLAG domain mode

**Usage**       : Use `no session-vrf` to delete the configured session-vrf association

**Supported Releases** :  4.0.0 or later

**Example**

```
sonic(config-mclag-domain-1)#
sonic(config-mclag-domain-1)# session-vrf Vrf01
sonic(config-mclag-domain-1)#

```

#### mclag interface
configure the mclag member interface for the domain

**Syntax** : `mclag <mlag-id>`

**Parameters** : 
 - `mlag-id` - mclag domain identifier

**Command mode** : portchannel interface mode

**Usage**       : Use `no mclag` to delete the configured mclag member interface

**Supported Releases** :  1.0.0 or later

**Click command** : config mclag member add <domain_id> <portchannel_names>

**Example**

```
sonic(conf-if-PortChannel200)# mclag 1
sonic(conf-if-PortChannel200)#
sonic(conf-if-PortChannel200)# no mclag
sonic(conf-if-PortChannel200)#
```


#### unique-ip
configure to enable unique ip address for the vlan interface

**Syntax** : `unique-ip enable'

**Parameters** : None



**Command mode** : interface vlan mode

**Usage**       : Use `no unique-ip enable` to disable unique ip configuration for the vlan interface

**Supported Releases** :  2.0.0 or later

**Click command** : config mclag vlan interface add <vlan_name>

**Example**

```
sonic(conf-if-Vlan100)# unique-ip enable
sonic(conf-if-Vlan100)#
sonic(conf-if-Vlan100)# no unique-ip enable
sonic(conf-if-Vlan100)#

```

### Show commands
#### show mclag brief
Displays the mclag domain information

**Syntax**: `show mclag brief`

**Parameters**  : `none`

**Command mode** : Exec mode

**Usage**       : 

**Click command** : `show mclag state 1`

**Example**
```
sonic# show mclag brief

-----------------------------------------------------------
Domain ID            : 1
Role                 : active
Session Status       : up
Mclag System Mac     :
Source Address       : 10.208.140.125
Peer Address         : 10.208.140.126
Peer Link            : PortChannel100
Keepalive Interval   : 1 secs
Session Timeout      : 15 secs
System Mac           : 34:ad:61:f1:a6:17

Number of MCLAG Interfaces:1
-----------------------------------------------------------
MCLAG Interface      Local/Remote Status
-----------------------------------------------------------
PortChannel200           up/up
sonic#
```
#### FDB
#### clear mac address-table dynamic
Displays the static and dynamic mac address information in the device

**Syntax**: `clear mac address-table dynamic [{vlan <vlan-id> | interface Ethernet <eth-if-id> | interface PortChannel <po-if-id>}]`

**Parameters**  :
- `vlan-id` - vlan identifier 
- `eth-if-id` - Ethernet interface identifier 
- `po-if-id` - PortChannel identifier within the range of 1 - 256

**Command mode** : EXEC mode

**Usage**       : if the optional vlan or interface keywords are not present, all dynamic mac addresses will be cleared

**Click command** :  sonic-clear fdb

**Example**
```
sonic# clear mac address-table dynamic
Success
sonic# clear mac address-table dynamic vlan 100
Success
sonic# clear mac address-table dynamic interface PortChannel 150
Success
sonic# clear mac address-table dynamic vlan 200 interface Ethernet 44
Success

```
### Show commands
#### show mac address-table
Displays the static and dynamic mac address information in the device

**Syntax**: `show mac address-table [{vlan <vlan-id> | interface Ethernet <eth-if-id> | interface PortChannel <po-if-id>}]`

**Parameters**  :
- `vlan-id` - vlan identifier 
- `eth-if-id` - Ethernet interface identifier 
- `po-if-id` - PortChannel identifier within the range of 1 - 256

**Command mode** : Exec mode

**Usage**       : if the optional vlan or interface keywords are not present, entire mac address table info is displayed

**Click command** :  show mac

**Example**
```
sonic# show mac address-table
------------------------------------------------------------------------------
MAC                 Vlan      Port                Type
------------------------------------------------------------------------------
00:00:00:00:00:0a   200       Ethernet45          dynamic
00:00:00:00:00:0c   200       Ethernet45          dynamic
00:00:00:00:00:0d   200       Ethernet45          dynamic
00:00:00:00:00:44   100       Ethernet44          static
00:00:00:00:00:45   100       PortChannel100      static
00:00:00:00:00:64   100       Ethernet44          static
00:00:00:00:0c:00   100       PortChannel100      static
------------------------------------------------------------------------------
Number of Macs displayed :7
------------------------------------------------------------------------------
sonic# show mac address-table Vlan 200
------------------------------------------------------------------------------
MAC                 Vlan      Port                Type
------------------------------------------------------------------------------
00:00:00:00:00:0a   200       Ethernet45          dynamic
00:00:00:00:00:0c   200       Ethernet45          dynamic
00:00:00:00:00:0d   200       Ethernet45          dynamic
------------------------------------------------------------------------------
Number of Macs displayed :3
------------------------------------------------------------------------------
sonic#


sonic# show mac address-table interface Ethernet 44
------------------------------------------------------------------------------
MAC                 Vlan      Port                Type
------------------------------------------------------------------------------
00:00:00:00:00:44   100       Ethernet44          static
00:00:00:00:00:64   100       Ethernet44          static
------------------------------------------------------------------------------
Number of Macs displayed :2
------------------------------------------------------------------------------
sonic#
sonic# show mac address-table interface PortChannel 100
------------------------------------------------------------------------------
MAC                 Vlan      Port                Type
------------------------------------------------------------------------------
00:00:00:00:00:45   100       PortChannel100      static
00:00:00:00:00:46   100       PortChannel100      static
------------------------------------------------------------------------------
Number of Macs displayed :2
------------------------------------------------------------------------------

```

## Mirroring
### Mirror Config commands
#### Mirror-session create and delete
Create a new mirror session(if not present). Enters into "config-mirror-<sessionname>" mode.

**Syntax** :
`mirror-session <session-name>`

**Parameters** :
- `session-name` - Name of the mirror session(Max size 32)

**Command mode** : CONFIG

**Usage**       : Use `no mirror-session <session-name>` to remove the mirror-session.
                  Use `no mirror-session all` to remove all mirror-sessions.

**Supported Releases** :  1.0.0 or later

**Click commands** : None

**Example**
```
sonic(config)# mirror-session m1
sonic(config-mirror-m1)#

sonic(config)# no mirror-session m1
sonic(config)# no mirror-session all
```

#### SPAN session config
Add, delete mirror destination port, source port(s) and its direction into the SPAN session. To add multiple source interfaces into the session, source port alone should be different and other paramters should be as same as the first source interface configuration.

**Syntax** :
`span destination Ethernet <interface-number> source {Ethernet <interface-number> | PortChannel <lag-id>} direction <direction-value>`

**Parameters** :
- `interface-number` - Mirror destination ethernet interface number
- `interface-number` - Mirror source ethernet interface number
- `lag-id` - Mirror source port-channel number. Range:1..256
- `direction-value` - Direction of the source-interface's traffic to be mirrored. Valid values are rx|tx|both

**Command mode** : Mirror session mode 

**Usage**       : Use `no source {Ethernet <interface-number> | PortChannel <lag-id>}` to remove the source interface alone from the mirror session.

**Supported Releases** :  1.0.0 or later

**Click commands** : `config mirror_session span add <session_name> <dst_port> [src_port] [direction] [queue]`

**Example**
```
sonic(config)# mirror-session m1
sonic(config-mirror-m1)# span destination Ethernet 0 source Ethernet 1 direction rx
sonic(config-mirror-m1)# span destination Ethernet 0 source Ethernet 2 direction rx
sonic(config-mirror-m1)# span destination Ethernet 0 source PortChannel 100 direction rx
sonic(config-mirror-m1)# no source Ethernet 2
```

#### Everflow SPAN session config
Add destination port alone to make the mirror session as an everflow mirror session. ACL rules are used to match source port(s). Upon removal, ACL rules must be removed before the deletion of mirror session.

**Syntax** :
`span destination Ethernet <interface-number>`

**Parameters** :
`interface-number` - Mirror destination ethernet interface number

**Command mode** : Mirror session mode

**Usage**       : Use `no mirror-session <session-name>` to delete flow-based mirror session.

**Click commands** : `config mirror_session span add <session_name> <dst_port>`

**Example**
```
sonic(config)# mirror-session m1
sonic(config-mirror-m1)# span destination Ethernet 2
sonic(config)# no mirror-session m1
```

#### ERSPAN session config
Add mirror session source interface(s) along with GRE tunnel mirror encap fields such as destination ip, source ip, dscp, gre, ttl fields value.

**Syntax** :
`erspan dst-ip <destination-ip-address> src-ip <source-ip-address> dscp <dscp-value> gre <gre-value> ttl <ttl-value> source {Ethernet <interface-number> | PortChannel <lag-id>} direction <direction-value>`

**Parameters** :
- `destination-ip-address` - GRE tunnel header's Destination IPv4 host address. Mirror destination port is resolved based on this IP address. Format: A.B.C.D
- `source-ip-address` - GRE tunnel header's source IPv4 address. Format: A.B.C.D
- `dscp-value` - GRE tunnel header's dscp value. Range:0-63
- `gre-value` - GRE tunnel protocol value. It should be given as 2-byte hex value with 0x prefix
- `ttl-value` - GRE tunnel header's ttl value. Range:0..63
- `interface-number` - Mirror source ethernet interface number
- `lag-id` - Mirror source port-channel number. Range:1..256
- `direction-value` - Direction of the source-interface's traffic to be mirrored. Valid values are rx/tx/both.

**Command mode** : Mirror session mode

**Usage**       : Use `no source {Ethernet <interface-number> | PortChannel <lag-id>}` to remove the source interface alone from the mirror session.

**Click commands** :
- `config mirror_session erspan add <session_name> <src_ip> <dst_ip> <dscp> <ttl> [gre_type] [queue] [src_port] [direction]`

**Example**
```
sonic(config)# mirror-session m1
sonic(config-mirror-m1)# erspan dst-ip 1.1.1.1 src-ip 2.2.2.2 dscp 0 gre 0x1234 ttl 63 source Ethernet 0 direction rx
sonic(config-mirror-m1)# erspan dst-ip 1.1.1.1 src-ip 2.2.2.2 dscp 0 gre 0x1234 ttl 63 source Ethernet 1 direction rx
sonic(config-mirror-m1)# no source Ethernet 0
```

#### Everflow ERSPAN session config
Except mirror session source interface, GRE tunnel mirror encap fields such as destination ip, source ip, dscp, gre, ttl fields value has to be given to make the mirror session as an everflow mirror session. ACL rules are used to match source port(s). Upon removal, ACL rules must be removed before the deletion of mirror session.

**Syntax** :
`destination Ethernet <interface-number>`

**Parameters** :
- `interface-number` - Mirror source ethernet interface number

**Command mode** : Mirror session mode

**Usage**       : Use `no mirror-session <session-name>` to delete the flow-based mirror session.

**Click command** : `config mirror_session [erspan] add <session_name> <src_ip> <dst_ip> <dscp> <ttl> [gre_type] [queue]`

**Example**
```
sonic(config)# mirror-session m1
sonic(config-mirror-m1)# erspan dst-ip 1.1.1.1 src-ip 2.2.2.2 dscp 0 gre 0x1234 ttl 63
sonic(config)# no mirror-session m1
```

### Mirror Show commands
Displays both SPAN and ERSPAN mirror sessions' configurations and its status.

**Syntax**: `show mirror-session [session-name]`

**Parameters**  :
`session-name` - Name of the mirror session(Max size 32)

**Command mode** : Exec mode

**Usage**       : If session-name is not given all configured mirror-sessions will be displayed.

**Click command** : `show mirror_session [SESSION_NAME]`

**Example**
```
sonic# show mirror-session
ERSPAN Sessions
---------------------------------------------------------------------------------------------------------------------------------------------------------
Name             Status     SRC-IP           DST-IP           GRE    DSCP   TTL    Queue    Policer    Monitor Port     Direction  SRC-Port
---------------------------------------------------------------------------------------------------------------------------------------------------------
m1               active     1.1.1.1          2.2.2.2          0x4d2  0      63                         Ethernet1
SPAN Sessions
-------------------------------------------------------------------------------------------------------------
Name             Status     DST-Port         Direction  Queue    Policer    SRC-Port
-------------------------------------------------------------------------------------------------------------
m2               active     Ethernet2        BOTH                           ['Ethernet3']
m3               active     Ethernet5        RX                             ['PortChannel100']
sonic# show mirror-session m2
SPAN Sessions
-------------------------------------------------------------------------------------------------------------
Name             Status     DST-Port         Direction  Queue    Policer    SRC-Port
-------------------------------------------------------------------------------------------------------------
m2               active     Ethernet2        BOTH                           ['Ethernet3']
sonic# show mirror-session m1
ERSPAN Sessions
---------------------------------------------------------------------------------------------------------------------------------------------------------
Name             Status     SRC-IP           DST-IP           GRE    DSCP   TTL    Queue    Policer    Monitor Port     Direction  SRC-Port
---------------------------------------------------------------------------------------------------------------------------------------------------------
m1               active     1.1.1.1          2.2.2.2          0x4d2  0      63                         Ethernet1
sonic#
```

## SFLOW
### SFLOW Config commands
Sflow feature has to be enabled by using 'config feature state sflow enabled' CLICK command before configuring sflow related global and interface level commands. This command is used to instantiate Sflow container.

#### SFLOW global config commands
##### SFLOW enable
Configure to enable globally.

**Syntax** : `sflow enable`

**Parameters** : None

**Command mode** : CONFIG

**Usage**       : Use `no sflow enable` to disable sflow feature globally.

**Click command** : `config sflow enable`

**Example**
```
sonic(config)# sflow enable
```

##### SFLOW polling-interval
Configure polling-interval for all interfaces. Based on this value counter samples will be collected from all of the interfaces. Default value is 20 seconds.

**Syntax** : `sflow polling-interval <pol-interval-value>`

**Parameters** :
- `pol-interval-value` - Polling interval value in secs. Range: 0..300

**Command mode** : CONFIG

**Usage**       : Use `sflow polling-interval 0` to disable polling-interval on all interfaces and counter samples collection will be stopped.
                  Use `no sflow polling-interval` to change polling-interval to default value.

**Click command** : `config sflow polling-interval <polling_interval>`

**Example**
```
sonic(config)# sflow polling-interval 100
```

##### SFLOW agent-id
Configure the interface name whose IPv4 or IPv6 address will be used as the agent-id in sFlow datagrams. Upon removal default agent-id will be elected based on the election process.

**Syntax** : `sflow agent-id {Ethernet <intf-num> | Loopback <lo-intf-num> | Vlan <vlan-id>}`

**Parameters** :
- `intf-num` - Ethernet interface number
- `lo-intf-num` - Loopback interface number. Range: 0..16383
- `vlan-id` - Vlan Id. Range: 1..4094

**Command mode** : CONFIG

**Usage**       : Use `no sflow agent-id` to remove agent-id config.

**Click command** : `config sflow agent-id add <interface_name>`

**Example**
```
sonic(config)# sflow agent-id Ethernet 7
```

##### SFLOW collector
Configure the sflow collector ip and port. Maximum 2 collectors are allowed to configure.

**Syntax** : `sflow collector <collector-ip> [collector-port] [collector-vrf]`

**Parameters** :
- `collector-ip` - Collector IP address. Format: A.B.C.D or A:B:C:D:E:F:G:H
- `collector-port` - Collector port number. Range: 0..65535(default: 6343)
- `collector-vrf` - Collector VRF name(mgmt)

**Command mode** : CONFIG

**Usage**       : Use `no sflow collector <collector-ip> [collector-port] [collector-vrf]` to remove collector config.

**Click command** : `config sflow collector add <collector_name> <IPv4|IPv6_address>`

**Example**
```
sonic(config)# sflow collector 1.1.1.1 65535
sonic(config)# sflow collector 1.1.1.2 65536 mgmt
```

##### SFLOW interface disable
Enable/Disable sflow on all interfaces globally. By default, sflow is enabled on all interfaces at the interface level.

**Syntax** : `sflow interface disable all`

**Parameters** : None

**Command mode** : CONFIG

**Usage**       : Use `no sflow interface disable all` to enable sflow on all interfaces.

**Click command** : `config sflow interface disable all`

**Example**
```
sonic(config)# sflow interface disable all
```

#### SFLOW interface level config commands
##### SFLOW interface enable
Enable/disable sflow at an interface level. By default, sflow is enabled on all interfaces at the interface level. Use this command to explicitly disable sFlow for a specific interface. An interface is sampled if sflow is enabled globally as well as at the interface level. Note that this configuration deals only with sFlow flow samples and not counter samples.

**Syntax**: `sflow enable`

**Parameters** : None

**Command mode** : Ethernet interface mode

**Usage**       : Use `no sflow enable` to disable sFlow on this interface.

**Click command** : `config sflow interface enable <interface_name>`

**Example**
```
sonic(config)#interface Ethernet 1
sonic(conf-if-Ethernet1)#sflow enable
sonic(conf-if-Ethernet1)# exit
sonic(config)#
```

##### SFLOW interface sampling-rate
Configure the sample-rate for a specific interface. The default sample rate based on interface speed is
1-in-1000 for a 1G link
1-in-10,000 for a 10G link
1-in-40,000 for a 40G link
1-in-100,000 for a 100G link
It is recommended not to change the defaults. This CLI is to be used only in case of exceptions (to set the sample-rate to the nearest power-of-2 if there are hardware restrictions in using the defaults)

**Syntax**: `sflow sampling-rate <sample-rate-value>`

**Parameters** :
- `sample-rate-value` - Sampling rate. Range: 256..8388608

**Command mode** : Ethernet interface mode

**Usage**       : Use `no sflow sampling-rate` to change it to default value.

**Click command** : `config sflow interface sample-rate <interface_name> <sample_rate>`

**Example**
```
sonic(config)#interface Ethernet 1
sonic(conf-if-Ethernet1)# sflow sampling-rate 300
sonic(conf-if-Ethernet1)# exit
sonic(config)#
```

#### SFLOW Show commands
##### SFLOW show
Displays the global sFlow configuration that includes the admin state, collectors, the Agent ID and counter polling interval.

**Syntax**: `show sflow`

**Parameters**  : None

**Command mode** : Exec mode

**Usage**       : None

**Click command** : `show sflow`

**Example**
```
sonic# show sflow
---------------------------------------------------------
Global sFlow Information
---------------------------------------------------------
     admin state:            up
     polling-interval:       100
     agent-id:               Ethernet7
     configured collectors:  2
      1.1.1.1             65535        default
      1.1.1.2             65536        mgmt
sonic#
```

##### SFLOW show interfaces
Displays the per-interface sflow admin status and the sampling rate.

**Syntax**: `show sflow interface`

**Parameters**  : None

**Command mode** : Exec mode

**Usage**       : None

**Click command** : `show sflow interface`

**Example**
```
sonic# show sflow interface
-----------------------------------------------------------
sFlow interface configurations
Interface              Admin State             Sampling Rate
       Ethernet0             up                     1000
       Ethernet1             up                     300
sonic#configure terminal
sonic(config)# no sflow interface disable all
sonic(config)# exit
sonic# show sflow interface
-----------------------------------------------------------
sFlow interface configurations
Interface              Admin State             Sampling Rate
       Ethernet0             up                     1000
       Ethernet1             up                     300
       Ethernet2             up                     1000
       Ethernet3             up                     1000
       Ethernet4             up                     1000
       Ethernet5             up                     1000
       Ethernet6             up                     1000
       Ethernet7             up                     1000
       Ethernet8             up                     1000
       Ethernet9             up                     1000
       Ethernet10            up                     1000
       Ethernet11            up                     1000
       Ethernet12            up                     1000
       Ethernet13            up                     1000
       Ethernet14            up                     1000
       Ethernet15            up                     1000
       Ethernet16            up                     1000
       Ethernet17            up                     1000
       Ethernet18            up                     1000
       Ethernet19            up                     1000
       Ethernet20            up                     1000
       Ethernet21            up                     1000
       Ethernet22            up                     1000
       Ethernet23            up                     1000
       Ethernet24            up                     1000
       Ethernet25            up                     1000
       Ethernet26            up                     1000
       Ethernet27            up                     1000
       Ethernet28            up                     1000
       Ethernet29            up                     1000
       Ethernet30            up                     1000
       Ethernet31            up                     1000
       Ethernet32            up                     1000
       Ethernet33            up                     1000
       Ethernet34            up                     1000
       Ethernet35            up                     1000
       Ethernet36            up                     1000
       Ethernet37            up                     1000
       Ethernet38            up                     1000
       Ethernet39            up                     1000
       Ethernet40            up                     1000
       Ethernet41            up                     1000
       Ethernet42            up                     1000
       Ethernet43            up                     1000
       Ethernet44            up                     1000
       Ethernet45            up                     1000
       Ethernet46            up                     1000
       Ethernet47            up                     1000
       Ethernet48            up                     10000
       Ethernet49            up                     10000
       Ethernet50            up                     10000
       Ethernet51            up                     10000
       Ethernet52            up                     10000
       Ethernet53            up                     10000
       Ethernet54            up                     10000
       Ethernet55            up                     10000
sonic#
```

## Port security
### BUM Storm Control

### Config commands
Configures the storm-control rate for BUM traffic

**Syntax**: `storm-control type <broadcast|unknown-unicast|unknown-multicast> rate <0-100000000>`

**Parameters**  :
- `broadcast|unknown-unicast|unknown-multicast` - Type of traffic on which storm-control to be applied
- `0-100000000` - Rate of traffic in kbps(kilo bits per second) to be admitted into the system. Traffic that exceeds the configured rate will be dropped.

**Command mode** : Ethernet interface mode

**Usage**       : Use `no storm-control type <broadcast|unknown-unicast|unknown-multicast>` to disable.

**Click command** : `config interface storm-control add <Ethernet-Interface-name> <broadcast|unknown-unicast|unknown-multicast> <0-100000000>`

**Example**
```
sonic(conf-if-Ethernet0)# storm-control type broadcast rate 3000
sonic(conf-if-Ethernet0)# no storm-control type broadcast
sonic(conf-if-Ethernet0)#
```

### Show commands
Displays the storm-control setting on the interface

**Syntax**: `show storm-control [interface <interface_name>]`

**Parameters**  :
- `interface_name' - Enter the interface name on which storm-control settings to be shown.

**Command mode** : Exec mode

**Usage**       : If interface keyword is not given all interfaces' storm-control settings will be displayed.

**Click command** : `show storm-control [interface <interface_name>]`

**Example**
```
sonic# show storm-control
-----------------------------------------------------
Interface Name      Storm-type          Rate (kbps)
-----------------------------------------------------
Ethernet0           broadcast           10000
Ethernet0           unknown-unicast     11000
Ethernet0           unknown-multicast   12000
Ethernet60          broadcast           60000
sonic#

sonic# show storm-control interface Ethernet 0
-----------------------------------------------------
Interface Name      Storm-type          Rate (kbps)
-----------------------------------------------------
Ethernet0           broadcast           10000
Ethernet0           unknown-unicast     11000
Ethernet0           unknown-multicast   12000
sonic#
```
##AAA
###Show aaa
Display the active configuration of aaa

**Syntax**: `show aaa`

**Command mode**: EXEC

**Supported Releases** :  1.0.0 or later

**Click command**: `show aaa`

**Example**:
```

sonic# show aaa
AAA authentication login local,radius
AAA authentication failthrough True
AAA authorization tacacs+
AAA accounting local

```

###AAA Authentication login
Confiure authentication login method

**Syntax**: `aaa authentication login <method>`

**Parameters**:
- `method` - Authentication login method accepts Maximum 2 arguments and Minimum 1 argument.
The combinations allowed are <local | local tacacs+ | local radius | radius | tacacs+ | radius local | tacacs+ local>

**Command mode**: CONFIG

**Usage**:
- Use `no aaa authentication login` to reset login method of authentication to default
- Default login method is <local>

**Click command**:
- config aaa authentication login <login_method>

**Example**:
```

sonic(config)# aaa authentication
failthrough login
sonic(config)# aaa authentication login
local   radius  tacacs+
sonic(config)# aaa authentication login local radius

```

###AAA Authentication failthrough
Confiure authentication failthrough status

**Syntax**: `aaa authentication failthrough <status>`

**Parameters**:
- `status` - Status of failthrough. Select between <enable | disable>

**Command mode**: CONFIG

**Usage**:
- Use `no aaa authentication failthrough` to reset failthrough Status to default
- Default failthrough Status is <disabled>

**Click command**:
- config aaa authentication failthrough <status>

**Example**:
```

sonic(config)# aaa authentication failthrough
disable enable
sonic(config)# aaa authentication failthrough enable

```

###AAA Authorization
Configure authorization method of system

**Syntax**: `aaa authorization <method>`

**Parameters**:
- `method` is the authorization method. Accepts Max one input
Select between <local | tacacs+>

**Command mode**: CONFIG

**Usage**:
- `no aaa authorization` resets the authorization method to default
- Deafult authorization method is <local>

**Click command**:
- config aaa authorization <method>

**Example**:
```

sonic(config)# aaa authorization
local   tacacs+
sonic(config)# aaa authorization tacacs+

```

###AAA Accounting
Configure accounting method of system

**Syntax**: `aaa accounting <method>`

**Parameters**:
- `method` is the accounting method. Accepts Max one input
Select between <local | tacacs+>

**Command mode**: CONFIG

**Usage**:
- `no aaa accounting` removes the AAA Accounting configuration

**Click command**:
- config aaa accounting <method>

**Example**:
```

sonic(config)# aaa accounting
local   tacacs+
sonic(config)# aaa accounting local


```
##Static Anycast Gateway
Static Anycast Gateway (SAG) commands
###sag mac
Configure static anycast gateway mac address

**Syntax** : `sag  mac <sag-mac>`

**Parameters** : 
 - `sag-mac` - anycast gateway mac address

**Command mode** : CONFIG

**Usage**       : Use `no sag mac <sag-mac>` to delete the anycast gateway mac address configuration

**Supported Releases** :  2.0.0 or later

**Click command** : config sag mac add <sag-mac>

**Example**

```
sonic(config)#
sonic(config)# sag mac 00:00:00:00:00:44

```
###sag ip
configure the static anycast gateway ip address

**Syntax** : `sag-ip <ip-address>`

**Parameters** : 
 - `ip-address` - v4 or v6 ip address

**Command mode** : vlan interface mode

**Usage**       : Use `no sag-ip` to delete the configured sag ip address

**Supported Releases** :  2.0.0 or later

**Click command** : config sag interface add <vlan_name> <sag_ip>

**Example**

```
sonic(conf-if-Vlan100)#
sonic(conf-if-Vlan100)# sag-ip 1000::1
sonic(conf-if-Vlan200)#
sonic(conf-if-Vlan200)# sag-ip 2.2.2.2
```

###show sag mac
Displays the configured static anycast gateway mac address

**Syntax**: `show sag mac

**Parameters**  : None

**Command mode** : Exec mode

**Supported Releases** :  2.0.0 or later

**Click command** : show sag mac

**Example**
```
sonic# show sag mac
---------------------
SAG MAC
---------------------
00:00:00:00:00:44
---------------------


```
###show sag interface
Displays the configured static anycast gateway interface ip address

**Syntax**: `show sag interface

**Parameters**  : None

**Command mode** : Exec mode

**Supported Releases** :  2.0.0 or later

**Click command** : show sag interface

**Example**
```
sonic# show sag interface
------------------------------------------------------------------------------
Vlan                IP address
------------------------------------------------------------------------------
Vlan100             1000::1
Vlan200             2.2.2.2
------------------------------------------------------------------------------
```
### Dynamic Load-balancing

#### dlb-hash idle-time
Configure dynamic load balancing idle time(in microseconds) period,
to detect flow inactivity.


**Syntax** : `dlb-hash idle-time <idle_time>`

**Parameters**  :
 - `idle_time` - Enter the time period in microseconds from 16 to 16383, default = 256

**Command mode** : CONFIG

**Usage**       : Use `no dlb-hash idle-time` to reset to default value.

**Supported Releases** :  3.0.0 or later

**Click command** : 'config switch-hash global ecmp-dlb-hash FLOWLET-QUALITY --idle-time 300'

**Example**
```
sonic(config)# dlb-hash idle-time 300
sonic(config)# no dlb-hash idle-time
sonic(config)#

```

#### dlb-hash load-current-enable
configure current load as a consideration for path eligibility criteria


**Syntax** : `dlb-hash load-current-enable <lc_enable>`

**Parameters**  :
 - `lc_enable` - true/false, default:true

**Command mode** : CONFIG

**Usage**       : Use `no dlb-hash load-current-enable` to reset to default value.

**Supported Releases** :  3.0.0 or later

**Click command** : 'config switch-hash global ecmp-dlb-hash FLOWLET-QUALITY --load-current-enable true'

**Example**
```
sonic(config)# dlb-hash load-current-enable true
sonic(config)# no dlb-hash load-current-enable
sonic(config)#

```


#### dlb-hash load-past-enable
configure past load as a consideration for path eligibility criteria


**Syntax** : `dlb-hash load-past-enable <lp_enable>`

**Parameters**  :
 - `lp_enable` - true/false, default:true

**Command mode** : CONFIG

**Usage**       : Use `no dlb-hash load-past-enable` to reset to default value.

**Supported Releases** :  3.0.0 or later

**Click command** : 'config switch-hash global ecmp-dlb-hash FLOWLET-QUALITY --load-past-enable true'

**Example**
```
sonic(config)# dlb-hash load-past-enable true
sonic(config)# no dlb-hash load-past-enable
sonic(config)#

```

#### dlb-hash load-future-enable
configure future load as a consideration for path eligibility criteria


**Syntax** : `dlb-hash load-future-enable <lf_enable>`

**Parameters**  :
 - `lf_enable` - true/false, default:true

**Command mode** : CONFIG

**Usage**       : Use `no dlb-hash load-future-enable` to reset to default value.

**Supported Releases** :  3.0.0 or later

**Click command** : 'config switch-hash global ecmp-dlb-hash FLOWLET-QUALITY --load-future-enable true'

**Example**
```
sonic(config)# dlb-hash load-future-enable true
sonic(config)# no dlb-hash load-future-enable
sonic(config)#

```

#### dlb-hash load-current-weight
configure current load weightage for determining the eligibility of a path for DLB selection.


**Syntax** : `dlb-hash load-current-weight <lc_weight>`

**Parameters**  :
 - `lc_weight` - range 0-15, default:2

**Command mode** : CONFIG

**Usage**       : Use `no dlb-hash load-current-weight` to reset to default value.

**Supported Releases** :  3.0.0 or later

**Click command** : 'config switch-hash global ecmp-dlb-hash FLOWLET-QUALITY --load-current-exponent 10'

**Example**
```
sonic(config)# dlb-hash load-current-weight 10
sonic(config)# no dlb-hash load-current-weight
sonic(config)#

```


#### dlb-hash load-past-weight
configure past load weightage for determining the eligibility of a path for DLB selection.


**Syntax** : `dlb-hash load-past-weight <lp_weight>`

**Parameters**  :
 - `lp_weight` - range 0-15, default:15

**Command mode** : CONFIG

**Usage**       : Use `no dlb-hash load-past-weight` to reset to default value.

**Supported Releases** :  3.0.0 or later

**Click command** : 'config switch-hash global ecmp-dlb-hash FLOWLET-QUALITY --load-past-weight 10'

**Example**
```
sonic(config)# dlb-hash load-past-weight 10
sonic(config)# no dlb-hash load-past-weight
sonic(config)#

```

#### dlb-hash load-future-weight
configure future load weightage for determining the eligibility of a path for DLB selection.


**Syntax** : `dlb-hash load-future-weight <lf_weight>`

**Parameters**  :
 - `lf_weight` - range 0-15, default:15

**Command mode** : CONFIG

**Usage**       : Use `no dlb-hash load-future-weight` to reset to default value.

**Supported Releases** :  3.0.0 or later

**Click command** : 'config switch-hash global ecmp-dlb-hash FLOWLET-QUALITY --load-future-weight 10'

**Example**
```
sonic(config)# dlb-hash load-future-weight 10
sonic(config)# no dlb-hash load-future-weight
sonic(config)#

```
#### dlb-hash max-flows
Configure maximum number of flows reserved for per DLB group.


**Syntax** : `dlb-hash max-flows <max_flows>`

**Parameters**  :
 - `max_flows` - Enter the number of flows within range 256-23768, default:512

**Command mode** : CONFIG

**Usage**       : Use `no dlb-hash max-flows` to reset to default value.

**Supported Releases** :  3.0.0 or later

**Click command** : 'config switch-hash global ecmp-dlb-hash FLOWLET-QUALITY --max-flows 1024'

**Example**
```
sonic(config)# dlb-hash max-flows 1024
sonic(config)# no dlb-hash max-flows
sonic(config)#

```
#### dlb-hash random-seed
configure the DLB hash random seed value.

**Syntax** : `dlb-hash random-seed <random_seed>`

**Parameters**  :
 - `random_seed` - range 1-16777215 default:53694

**Command mode** : CONFIG

**Usage**       : Use `no dlb-hash random-seed` to reset to default value.

**Supported Releases** :  3.0.0 or later

**Click command** : 'config switch-hash global ecmp-dlb-hash FLOWLET-QUALITY --random-seed 10000'

**Example**
```
sonic(config)# dlb-hash random-seed 10000
sonic(config)# no dlb-hash random-seed
sonic(config)#

```

#### dlb-hash sampling-interval
Configure DLB hash sampling interval in microseconds

**Syntax** : `dlb-hash sampling-interval <smpl_intvl>`

**Parameters**  :
 - `smpl_intvl` - interval range 1-255 microseconds, default:16

**Command mode** : CONFIG

**Usage**       : Use `no dlb-hash sampling-interval` to reset to default value.

**Supported Releases** :  3.0.0 or later

**Click command** : 'config switch-hash global ecmp-dlb-hash FLOWLET-QUALITY --sampling-interval 100'

**Example**
```
sonic(config)# dlb-hash sampling-interval 100
sonic(config)# no dlb-hash sampling-interval
sonic(config)#
```

#### dlb-hash quant-band-min
Configure DLB hash quantization band minimum value.

**Syntax** : `dlb-hash quant-band-min <quant_band_min>`

**Parameters**  :
 - `quant_band_min` - minimum bandwidth value, default:1000

**Command mode** : CONFIG

**Usage**       : Use `no dlb-hash quant-band-min` to reset to default value.

**Supported Releases** :  3.0.0 or later

**Click command** : 'config switch-hash global ecmp-dlb-hash FLOWLET-QUALITY --quantization-band-min 2000'

**Example**
```
sonic(config)# dlb-hash quant-band-min 2000
sonic(config)# no dlb-hash quant-band-min

```

#### dlb-hash quant-band-max
Configure DLB hash quantization band maximum value.

**Syntax** : `dlb-hash quant-band-max <quant_band_max>`

**Parameters**  :
 - `quant_band_max` - maximum bandwidth value, default:10000

**Command mode** : CONFIG

**Usage**       : Use `no dlb-hash quant-band-max` to reset to default value.

**Supported Releases** :  3.0.0 or later

**Click command** : 'config switch-hash global ecmp-dlb-hash FLOWLET-QUALITY --quantization-band-max 20000'

**Example**
```
sonic(config)# dlb-hash quant-band-max 20000
sonic(config)# no dlb-hash quant-band-max

```
#### dlb-hash reassign-probability
Configure DLB hash path reassignment probability value.

**Syntax** : `dlb-hash reassign-probability <reassign_probability>`

**Parameters**  :
 - `reassign_probability` - reassign probability value, default:0

**Command mode** : CONFIG

**Usage**       : Use `no dlb-hash reassign-probability` to reset to default value.

**Supported Releases** :  3.0.0 or later

**Click command** : 'config switch-hash global ecmp-dlb-hash FLOWLET-QUALITY --reassign-probability 10'

**Example**
```
sonic(config)# dlb-hash reassign-probability 50
sonic(config)# no dlb-hash reassign-probability

```
#### dlb-hash reassign-quality-delta
Configure DLB hash path reassignment quality band delta value.

**Syntax** : `dlb-hash reassign-quality-delta <reassign_qual_delta>`

**Parameters**  :
 - `reassign_qual_delta` - reassign quality band delta value, default:0

**Command mode** : CONFIG

**Usage**       : Use `no dlb-hash reassign-quality-delta` to reset to default value.

**Supported Releases** :  3.0.0 or later

**Click command** : 'config switch-hash global ecmp-dlb-hash FLOWLET-QUALITY --reassign-quality-delta 3'

**Example**
```
sonic(config)# dlb-hash reassign-quality-delta 3
sonic(config)# no dlb-hash reassign-quality-delta

```
#### dlb-hash mode
Configure DLB hash mode.

In FLOWLET-QUALITY mode, a new optimal path will be selected when inactivity duration is detected for the flow.
In PACKET-QUALITY mode, a new optimal path will be selected for every packet, this is also called spray-mode.
In Fixed mode, DLB mode will be in disabled state. always the selected path will be used.

**Syntax** : `dlb-hash mode <dlb_mode>`

**Parameters**  :
 - `dlb_mode` - FLOWLET_QUALITY/PACKET_QUALITY/FIXED, default: FLOWLET_QUALITY

**Command mode** : CONFIG

**Usage**       : Use `no dlb-hash mode` to reset to default value.

**Supported Releases** :  3.0.0 or later

**Click command** : 'config switch-hash global ecmp-dlb-hash FLOWLET-QUALITY'

**Example**
```
sonic(config)# dlb-hash mode FLOWLET_QUALITY
sonic(config)# no dlb-hash mode
sonic(config)#

```

#### show dlb-hash brief
Display the DLB attributes detail applied on the switch.

**Syntax**: `show dlb-hash brief`

**Parameters**  : `none`

**Command mode** : Exec mode

**Usage**       : `show dlb-hash brief`

**Click command** : `show switch-hash dlb`

**Example**
```
sonic#
sonic# show dlb-hash brief
-----------------------------------------------------------
DLB Mode                  : FLOWLET_QUALITY
Max FLows                 : 512
Idle time                 : 256
Sampling interval         : 16
Random seed               : 53694
Quantization band Min     : 1000
Quantization band Max     : 10000
Load past enable          : True
Load current enable       : True
Load future enable        : True
Load past weight          : 2
Load current weight       : 15
Load future weight        : 15
-----------------------------------------------------------
```


##Tunnel
###Show tunnel summary
Displays the configured tunnel information

**Syntax**: `show tunnel summary [tunnel-id]`

**Parameters**  :
- `tunnel-id' - Tunnel identifier.

**Command mode** : Exec mode

**Usage**       : If optional Tunnel identifier is not given all configured tunnel information will be displayed.

**Supported Releases** :  2.0.0 or later

**Click command** : show tunnel

**Example**
```
sonic# show tunnel summary
--------------------------------------------------------------------------------
Tunnel Name         Tunnel Source IP     Tunnel Destination IP 
--------------------------------------------------------------------------------
Tunnel100            1.1.1.1              2.2.2.2
--------------------------------------------------------------------------------
Tunnel50             2.1.1.1              3.2.2.2
--------------------------------------------------------------------------------
sonic# show tunnel summary 100
--------------------------------------------------------------------------------
Tunnel Name         Tunnel source IP     Tunnel Destination IP 
--------------------------------------------------------------------------------
Tunnel100            1.1.1.1              2.2.2.2
--------------------------------------------------------------------------------
sonic#

```

##SNMP
###SNMP Contact 
Configure SNMP contact information

**Syntax**: `snmp-server contact <contact_detail>`

**Command mode**: CONFIG

**Usage**       : Use `no snmp-server contact` to remove the SNMP contact information

**Parameters**  :
- `contact_detail` -  SNMP Contact detail(Max 255 characters)

**Supported Releases** :  1.0.0 or later

**Click command**: `config snmp contact add [OPTIONS] <contact_name> <contact_email>`

**Example**:
```

sonic(config)# snmp-server contact Celestica
sonic(config)# no snmp-server contact

```

###SNMP Location
Configure SNMP location information

**Syntax**: `snmp-server location <location>`

**Command mode**: CONFIG

**Usage**       : Use `no snmp-server location` to remove the SNMP location information

**Parameters**  :
- `location` -  SNMP Location detail(Max 255 characters)

**Supported Releases** :  1.0.0 or later

**Click command**: `config snmp location add [OPTIONS] <location>`

**Example**:
```

sonic(config)# snmp-server location CLS_US
sonic(config)# no snmp-server location

```

###SNMP Community
Configure SNMP community

**Syntax**: `snmp-server community <name> <RO/RW>`

**Command mode**: CONFIG

**Usage**       : Use `no snmp-server community <string>` to remove the SNMP community

**Parameters**  :
- `name`        -  SNMP community name(4-32 chars: no space, comma, @ allowed)
- <RO | RW>     -  Read-only or Read-write permission 

**Supported Releases** :  1.0.0 or later

**Click command**: `config snmp community add [OPTIONS] <snmp_community> <RO|RW>`

**Example**:
```

sonic(config)# snmp-server community private RW
sonic(config)# no snmp-server community private

```

###SNMP User
Configure SNMP User

**Syntax**: `snmp-server user <username> <noAuthNoPriv|AuthNoPriv|Priv> <MD5|SHA|HMAC-SHA-2> {auth-password <auth_password> | encrypted-auth-password <encrypted_auth_password>} <DES|AES> {encrypt-password <encrypt_password> | encrypted-auth-password <encrypted_auth_password>} <RO/RW>`

**Command mode**: CONFIG

**Usage**       : Use `no snmp-server user <username>` to remove the SNMP user

**Parameters**  :
- `username`                      -  SNMP username(Max: 32 characters)
- <noAuthNoPriv|AuthNoPriv|Priv>  -  User type
- <MD5|SHA|HMAC-SHA-2>            -  Authentication method
- `auth_password`                 -  Authentication password(Min len:8 Max len:64, '@' , ':' not allowed)
- `encrypted_auth_password`       -  Authentication password string encrypted
- <DES|AES>                       -  Encryption method
- `encrypt_password`              -  Encryption password(Min len:8 Max len:64, '@' , ':' not allowed)
- `encrypted_encrypt_password`    -  Encryption password string encrypted
- <RO|RW>                         -  Read-only or Read-write permission

**Supported Releases** :  1.0.0 or later

**Click command**: `config snmp user add [OPTIONS] <snmp_user>
                            <noAuthNoPriv|AuthNoPriv|Priv> <RO|RW>
                            <MD5|SHA|HMAC-SHA-2> <auth_password> <DES|AES>
                            <encrypt_password>`

**Example**:
```

sonic(config)# snmp-server user testuser1 noAuthNoPriv RO
sonic(config)# snmp-server user testuser2 AuthNoPriv MD5 auth-password testpassword RW
sonic(config)# snmp-server user testuser3 Priv MD5 auth-password testpassword DES encrypt-password testpassword RW
sonic(config)# no snmp-server user testuser1
sonic(config)# snmp-server user test3 Priv MD5 encrypted-auth-password U2FsdGVkX1+sd7irRVoxtsl5jCscDv1nbF0KdWIve1U= DES encrypted-encrypt-password U2FsdGVkX1+sd7irRVoxtsl5jCscDv1nbF0KdWIve1U= RW
Celestica-DS3000(config)# snmp-server user user2 Priv MD5 auth-password admin12345 DES encrypted-encrypt-password YourPaSsWoRd RO
Celestica-DS3000(config)# snmp-server user user3 Priv MD5 encrypted-auth-password  U2FsdGVkX1+sd7irRVoxtsl5jCscDv1nbF0KdWIve1U= DES encrypt-password YourPaSsWoRd RO
```

###SNMP Host
Configure SNMP Host to send Trap messages

**Syntax**: `snmp-server host <host_address> version <1/2/3> [community <community_name>] [port <port_num>] [vrf <vrf_name>]`

**Command mode**: CONFIG

**Usage**       : Use `no snmp-server host <host_address> version <1/2/3>` to remove the SNMP Host

**Parameters**  :
- `host_address`   -  Host IP address to receive Trap messages, One host IP address is allowed per SNMP version.
- <1 | 2 | 3>      -  SNMP version
- `community_name` -  Community name(4-32 chars: no space, comma, @ allowed), default value is "public".
- `port_num`       -  UDP port number(range 1024..65535 , default 162)
- `vrf_name`       -  VRF name, default value is "None".

**Supported Releases** :  1.0.0 or later

**Click command**: `config snmptrap modify [OPTIONS] <SNMP Version> <SNMP TRAP SERVER IP Address>`

**Example**:
```

sonic(config)# snmp-server host 1.1.1.1 version 2 community private
sonic(config)# no snmp-server host 1.1.1.1 version 2

```
###SNMP Agentaddress
Configure SNMP Agentaddress

**Syntax**: `snmp-server agent-address <ip_address> [port <port_num>] [vrf <vrf_name>]`

**Command mode**: CONFIG

**Usage**       : Use `no snmp-server agent-address <ip_address>` to remove the SNMP Agentaddress

**Parameters**  :
- `port_num`       -  UDP port number(range 1024..65535 , default 162)
- `vrf_name`       -  VRF name

**Supported Releases** :  1.0.0 or later

**Click command**: `config snmpagentaddress add [OPTIONS] <SNMP AGENT LISTENING IP Address>`

**Example**:
```

sonic(config)# snmp-server agent-address 1.1.1.1
sonic(config)# no snmp-server agent-address 1.1.1.1

```

###Show SNMP contact and location
Display SNMP contact and location details

**Syntax**: `show snmp-server`

**Command mode** : EXEC

**Supported Releases** :  1.0.0 or later

**Click command** : None

**Example**:
```

sonic# show snmp-server
               SNMP Global Configurations
------------------------------------------------------------
SNMP Contact            : Celestica
SNMP Location           : CLS_India

```

###Show SNMP community
Display SNMP community details

**Syntax**: `show snmp-server community`

**Command mode** : EXEC

**Supported Releases** :  1.0.0 or later

**Click command** : None

**Example**:
```

sonic# show snmp-server community
-------------------------------------------------------------------
Community Name                           Community Type
-------------------------------------------------------------------
    private                                  RW
    test_comm                                RO

```

###Show SNMP user
Display SNMP user details

**Syntax**: `show snmp-server user`

**Command mode** : EXEC

**Supported Releases** :  1.0.0 or later

**Click command** : None

**Example**:
```

sonic# show snmp-server user
---------------------------------------------------------------------------------------------
User Name                           User Type            Auth       Privacy    Permission
---------------------------------------------------------------------------------------------
testuser                            no-auth-no-priv      None       None       RO
testuser2                           auth-no-priv         MD5        None       RW
testuser3                           auth-priv            MD5        DES        RW
sonic#

```

###Show SNMP host
Display SNMP host details

**Syntax**: `show snmp-server host`

**Command mode** : EXEC

**Supported Releases** :  1.0.0 or later

**Click command** : `show snmptrap`

**Example**:
```

sonic# show snmp-server host
-----------------------------------------------------------------------------------------------
Target Address                 Version     UDP Port  Community                           VRF
-----------------------------------------------------------------------------------------------
1.1.1.1                        V2C         162        public                             None


```

###Show SNMP agentaddress
Display SNMP agent-address details

**Syntax**: `show snmp-server agent-address`

**Command mode** : EXEC

**Supported Releases** :  1.0.0 or later

**Click command** : `show snmpagentaddress`

**Example**:
```

sonic(config)# do show snmp-server agent-address
-----------------------------------------------------------------------------------------------
Agent Address                  UDP Port   VRF
-----------------------------------------------------------------------------------------------
172.23.126.113                 None       default

```

##DHCP Relay
###DHCPv4 Relay Configuration
Configure DHCPv4 Relay address in vlan

**Syntax**: `ip helper-address <relay_address> [<relay_address>] [<relay_address>] [<relay_address>]`

**Command mode**: Interface mode (VLAN)

**Usage**       : Use `no ip helper-address <relay_address>` to remove the DHCPv4 Relay information

**Parameters**  :
- `relay_address`    -  DHCPv4 Relay address (Max 4)

**Supported Releases** :  1.0.0 or later

**Click command**: `config vlan dhcp_relay add [OPTIONS] <vid> DHCP_RELAY_DESTINATION_IPS...`

**Example**:
```

sonic(conf-if-Vlan100)# ip helper-address 1.1.1.1
sonic(conf-if-Vlan100)# no ip helper-address 1.1.1.1


```
###Show DHCPv4 relay address
Display DHCPv4 relay address details

**Syntax**: `show ip dhcp-relay brief [vlan <id>]`

**Command mode** : EXEC

**Parameters**  :
- `id`    -  Vlan ID (1-4094)

**Supported Releases** :  1.0.0 or later

**Click command** : `show vlan brief`

**Example**:
```

sonic# show ip dhcp-relay brief Vlan 200
------------------------------------------------
Interface Name    DHCP Helper Address
------------------------------------------------
Vlan200           21.1.1.1
                  21.1.1.3
                  21.1.1.4

```

###DHCPv6 Relay Configuration
Configure DHCPv6 Relay address in vlan

**Syntax**: `ipv6 helper-address <relay_address> [<relay_address>] [<relay_address>] [<relay_address>]`

**Command mode**: Interface mode (VLAN)

**Usage**       : Use `no ipv6 helper-address <relay_address>` to remove the DHCPv6 Relay information

**Parameters**  :
- `relay_address`    -  DHCPv6 Relay address (Max 4)

**Supported Releases** :  1.0.0 or later

**Click command**: `config vlan dhcp_relay add [OPTIONS] <vid> DHCP_RELAY_DESTINATION_IPS...`

**Example**:
```

sonic(conf-if-Vlan100)# ipv6 helper-address 1::1
sonic(conf-if-Vlan100)# no ipv6 helper-address 1::1


```

###Show DHCPv6 relay address
Display DHCPv6 relay address details

**Syntax**: `show ipv6 dhcp-relay brief [vlan <id>]`

**Command mode** : EXEC

**Parameters**  :
- `id`    -  Vlan ID (1-4094)

**Supported Releases** :  1.0.0 or later

**Click command** : `show dhcprelay_helper ipv6`

**Example**:
```

sonic# show ipv6 dhcp-relay brief
------------------------------------------------
Interface Name    DHCPv6 Helper Address
------------------------------------------------
Vlan100           21::1
                  21::5
                  21::4
Vlan200           21::9
                  43::2

```

###Show DHCPv6 relay counters
Display DHCPv6 relay counter details

**Syntax**: `show ipv6 helper-address counters [vlan <id>]`

**Command mode** : EXEC

**Parameters**  :
- `id`    -  Vlan ID (1-4094)

**Supported Releases** :  1.0.0 or later

**Click command** : `show dhcp6relay_counters counts`

**Example**: 
```
sonic# show ipv6 dhcp-relay counters
------------------------------------------------
       Message Type   Vlan100
------------------------------------------------
            Unknown   0
            Solicit   24
          Advertise   0
            Request   0
            Confirm   0
              Renew   0
             Rebind   0
              Reply   0
            Release   0
            Decline   0
        Reconfigure   0
Information-Request   0
      Relay-Forward   72
        Relay-Reply   0
          Malformed   0
```

###Clear DHCPv6 relay counters
Clear DHCPv6 relay counters

**Syntax**: `clear ipv6 dhcp-relay counters [vlan <id>]`

**Command mode** : EXEC

**Parameters**  :
- `id`    -  Vlan ID (1-4094)

**Supported Releases** :  1.0.0 or later

**Click command** : `sonic-clear dhcp6relay_counters`

**Example**: 
```
sonic# clear ipv6 dhcp-relay counters Vlan 100
sonic#

```
##CRM
###CRM polling interval
Configure CRM polling interval

**syntax**: `crm polling-interval <value>`

**Command mode**: CONFIG

**Usage**: Use `no crm polling-interval` to reset the polling inteval value to 300sec.

**Parameters** :
- `value` - Polling interval value(in seconds), Default value is 300 secounds.

**Supported Releases** : 1.0.0 or later

**Click command**: `crm config polling interval [OPTIONS] INTERVAL`

**Example**:
```
sonic(config)# crm polling-interval 600
sonic(config)#
```
```
sonic(config)# no crm polling-interval
sonic(config)#
```

###CRM threshold resource
Configure threshold values for CRM resources.

**syntax**: `crm threshold resource <resource_name> high-threshold <high-threshold-value> low-threshold <low-threshold-value> threshold-type <threshold-type-value>`

**Command mode**: CONFIG

**Usage**: Use `no crm threshold resource <resource_name>` reset the configured threshold values to default values.

**Parameters** :
- `resource_name` - Choose the required resource from the list, for which threshold value need to be configured,
                    below is the list of available resources,
                       acl_group_counter     
                       acl_group_entry     
                       acl_group_table
                       fdb                  
                       ipv4_neighbor        
                       ipv4_nexthop         
                       ipv4_route        
                       ipv6_neighbor        
                       ipv6_nexthop         
                       ipv6_route  
                       nexthop_group_object
                       nexthop_group_member

- `high-threshold-value` - Configure higher threshold value for the resource, default value is 85%.
- `low-threshold-value`  - Configure higher threshold value for the resource, default value is 70%.
- `threshold-type` - Configure threshold type from <percentage/used/free> options, percentage is the default config.

**Supported Releases** : 1.0.0 or later

**Click command**: 
- `crm config thresholds acl group counter high <value>`
- `crm config thresholds acl group counter low <value>`
- `crm config thresholds acl group counter type <option>`

**Example**:
```
sonic(config)# `crm threshold resource acl_group_counter high-threshold 90 low-threshold 60 threshold-type used`
sonic(config)# `no crm threshold resource acl_group_counter'
```

###Show crm summary
Displays the polling interval configured values.

**Syntax**: `show crm summary`

**Parameters**: NA

**Command mode**: EXEC

**Usage**: NA

**Click command**:
- `crm show summary`

**Example**:
```
sonic# show crm summary
Polling Interval:300 second(s)
sonic#
```

###Show crm threshold
Displays the configured and default threshold values of the CRM resources.

**Syntax**: `show crm threshold [<resource_name> | all ]

**Parameter**:
- `resource_name` - Choose the required resource from the list, for which threshold value need to be displayed,
                    below is the list of available resources,
                       `acl_group_counter`
                       `acl_group_entry`
                       `acl_group_table`
                       `fdb`
                       `ipv4_neighbor`
                       `ipv4_nexthop`
                       `ipv4_route`
                       `ipv6_neighbor`
                       `ipv6_nexthop`
                       `ipv6_route`
                       `nexthop_group_object`
                       `nexthop_group_member`

- `all` - Displays threshold values of all the resources.

**Command mode**: EXEC

**Usage**: NA

**Click command**:
- `crm show threshold [<resource_name> | all]`

**Example**:
```
sonic# show crm threshold all
Resource Name             Threshold type  Low-threshold High-threshold
-------------------------------------------------------------------------------------------------
acl_group                 percentage      70              85
acl_group_counter         used            60              90
acl_group_entry           percentage      70              85
acl_group_table           percentage      70              85
fdb                       percentage      70              85
ipv4_neighbor             percentage      70              85
ipv4_nexthop              percentage      70              85
ipv4_route                percentage      70              85
ipv6_neighbor             percentage      70              85
ipv6_nexthop              percentage      70              85
ipv6_route                percentage      70              85
nexthop_group_member      percentage      70              85
nexthop_group_object      percentage      70              85
```

###Show crm resource
Displays the used and available count of the CRM resources.

**Syntax**: `show crm resource [<resource_name> | all ]

**Parameter**:
- `resource_name` - Choose the required resource from the list, for which used and available values need to be displayed,
                    below is the list of available resources,
                       `acl_group_counter`
                       `acl_group_entry`
                       `acl_group_table`
                       `fdb`
                       `ipv4_neighbor`
                       `ipv4_nexthop`
                       `ipv4_route`
                       `ipv6_neighbor`
                       `ipv6_nexthop`
                       `ipv6_route`
                       `nexthop_group_object`
                       `nexthop_group_member`

- `all` - Displays used and available values of all the resources.

**Command mode**: EXEC

**Usage**: NA

**Click command**:
- `crm show resources [<resource_name> | all]`

**Example**:
```
sonic# show crm resource all

Resource Name           Used Count    Available Count
--------------------  ------------  -----------------
ipv4_route                       1               6139
ipv6_route                       3               1536
ipv4_nexthop                     0              32766
ipv6_nexthop                     0              32766
ipv4_neighbor                    0              32765
ipv6_neighbor                    0              16383
nexthop_group_member             0              32768
nexthop_group                    0                512
fdb_entry                        0              65535
ipmc_entry                       0              16384
snat_entry                       0                  0
dnat_entry                       0                  0


Stage    Bind Point    Resource Name      Used Count    Available Count
-------  ------------  ---------------  ------------  -----------------
INGRESS  PORT          acl_group                   0                256
INGRESS  PORT          acl_table                   0                  5
INGRESS  LAG           acl_group                   0                256
INGRESS  LAG           acl_table                   0                  5
INGRESS  VLAN          acl_group                   0                256
INGRESS  VLAN          acl_table                   0                 16
INGRESS  RIF           acl_group                   0                256
INGRESS  RIF           acl_table                   0                 16
INGRESS  SWITCH        acl_group                   0                256
INGRESS  SWITCH        acl_table                   0                 16
EGRESS   PORT          acl_group                   0                256
EGRESS   PORT          acl_table                   0                  2
EGRESS   LAG           acl_group                   0                256
EGRESS   LAG           acl_table                   0                  2
EGRESS   VLAN          acl_group                   0                256
EGRESS   VLAN          acl_table                   0                  2
EGRESS   RIF           acl_group                   0                256
EGRESS   RIF           acl_table                   0                  2
EGRESS   SWITCH        acl_group                   0                256
EGRESS   SWITCH        acl_table                   0                  2

```

##Feature
####Show Feature
Display the status, owner, fallback and auto-restart information of system features

**Syntax**: `show feature status [feature_name]`

**Parameters**:
- `feature_name` - Name of the feature For which the information needs to be fetched.
accepts String of Maximum 32 Characters

**Command mode**: EXEC

**Usage**:
- <feature_name> is optional
- If <feature_name> is not given, all the feature information is retrieved

**Click command**:
- `show feature <status | autorestart | config>`

**Example**:
```

sonic# show feature status
----------------------------------------------------------------------------------
NAME                 STATE                AUTORESTART          OWNER
----------------------------------------------------------------------------------
bgp                  enabled              enabled              local
database             always_enabled       always_enabled       local
dhcp_relay           disabled             enabled              local
gbsyncd              enabled              enabled              local
iccpd                disabled             enabled              local
lldp                 enabled              enabled              local
macsec               disabled             enabled              local
mgmt-framework       enabled              enabled              local
mux                  always_disabled      enabled              local
nat                  disabled             enabled              local
pmon                 enabled              enabled              local
radv                 enabled              enabled              local
sflow                disabled             enabled              local
snmp                 enabled              enabled              local
swss                 enabled              enabled              local
syncd                enabled              enabled              local
teamd                enabled              enabled              local
gnmi                 enabled              enabled              local


sonic# show feature status mgmt-framework
----------------------------------------------------------------------------------
NAME                 STATE                AUTORESTART          OWNER
----------------------------------------------------------------------------------
mgmt-framework       enabled              enabled              local


```

####Config Feature
Configure state, auto-restart, fallback and owner of system features

**Syntax**: `feature <feature_name> state <state> auto-restart <autorestart_state> owner <owner> fallback <fallback>`

**Parameters**:
- `feature_name` - name of the feature to configure. accepts String of Max 32 Characters
- `state` - state of the feature. select between <enabled | disabled>
- `autorestart_state` - state of autorestart of the feature. select between <enabled | disabled>
- `owner` -  Owner of the Feature. select between <local | kube>
- `fallback` - Fallback of Feature. select Between <off | on>

**Command mode**: CONFIG

**Usage**:
- Use this command to enable/disable the feature, auto-start, owner and fallback 
- Configuring bgpd, ospfd, ospf6d and staticd daemon state erases the unsaved frr config. 

**Click command**:
- `config feature state <Enable|disable>
- `config feature autorestart <Enable|disable>
- `config feature fallback <off|on>
- `config feature owner <kube|local>

**Example**:
```

sonic(config)# feature snmp fallback on state enabled auto-restart disabled owner local
sonic(config)#

```

## System management

### Image management

#### Image install
Install new SONiC image.

**Syntax** : `image install <image-path> [skip-package-migration] [skip-migration]`

**Command mode** : EXEC

**Parameters** :
- `image-path` : Local file (local://) or Remote file (http:// or https://)
- `skip-package-migration` : Option to skip package migration while installing image
- `skip-migration` : Option to skip migration while installing image
- `skip-platform-check` : Option to skip platform check  while installing image
- `skip-secure-check` : Option to skip secure check while installing image
- `skip-setup-swap` : Option to skip setup swap while installing image
- `swap-mem-size` : Option to swap mem size while installing image
- `secure-boot-key-update` : Option to install secure boot image signed with different key
- `total-mem-threshold` : Option to total mem threshold while installing image
- `available-mem-threshold` : Option to available mem threshold while installing image
**Usage** :
Use this command to install new image. New image will be set as next boot image after successful installation.<br>Use `show image status` to retrieve image installation status.<br>

**Supported Releases** :  1.0.0 or later

**Click command** : `sonic-installer install <image-path> [--skip-package-migration] [--skip_migration] [ --skip-platform-check] [ --skip-secure-check] [ --skip-setup-swap] [ --swap-mem-size] [--secure-boot-key-update] [total-mem-threshold] [ --available-mem-threshold]`

**Example**
```
sonic# image install local:///tmp/sonic-broadcom.bin
%Info: Use 'show image status' for image install progress.
sonic#

sonic# image install http://10.208.29.3:8080/sonic-broadcom.bin
%Info: Use 'show image status' for image install progress.
sonic#

sonic# image install local:///tmp/sonic-broadcom.bin skip-package-migration skip-migration
%Info: Use 'show image status' for image install progress.
sonic#
sonic# image install local:///cls-sonic-broadcom-k179.bin skip-platform-check skip-secure-check
New image will be installed, continue? [y/N]: y
sonic# image install local:///tmp/sonic-broadcom.bin skip-setup-swap
New image will be installed, continue? [y/N]: y
%Info: Use 'show image status' for image install progress.
sonic# image install local:///cls-sonic-broadcom-k179.bin swap-mem-size 10 available-mem-threshold 20
New image will be installed, continue? [y/N]: y
%Info: Use 'show image status' for image install progress.
sonic# image install local:///cls-sonic-broadcom-k179.bin swap-mem-size 10 available-mem-threshold 20 total-mem-threshold 15
New image will be installed, continue? [y/N]: y
%Info: Use 'show image status' for image install progress.
sonic#

```
#### Verify next image
Verify next boot Image.

**Syntax** : `image verify-next-image`

**Command mode** : EXEC

**Usage** : Use this command to verify next image for reboot.

**Supported Releases** :  1.0.0 or later

**Click command** :
- `sonic-installer verify-next-image
- 
**Example**
```
sonic# image verify-next-image
sonic#
```

#### Image remove
Remove installed image.

**Syntax** : `image remove {all | <image-name>}`

**Command mode** : EXEC

**Parameters** :
- `image-name` : Name of installed image

**Usage** : Use this command to remove installed image, `all` option removes all images which are not current or next.

**Supported Releases** :  1.0.0 or later

**Click command** :
- `sonic-installer remove <image-name>`
- `sonic-installer cleanup`

**Example**
```
sonic# image remove SONiC-OS-staging_202205.0-dirty-20230124.120342
Success
sonic#
```

#### Set next boot
Set the image for next boot

**Syntax** : `image set-next-boot <image-name>`

**Command mode** : EXEC

**Parameters** :
- `image-name` : Name of installed image

**Usage** : Use this command to set the image for next boot.

**Supported Releases** :  1.0.0 or later

**Click command** : `sonic-installer set-next-boot <image-name>`

**Example**
```
sonic# show image list
Current: SONiC-OS-AF_CLS_SONiC_master_1-0-0_20
Next: SONiC-OS-AF_CLS_SONiC_master_1-0-0_20
Available:
SONiC-OS-AF_CLS_SONiC_master_1-0-0_19
SONiC-OS-AF_CLS_SONiC_master_1-0-0_20
sonic# image set-next-boot SONiC-OS-AF_CLS_SONiC_master_1-0-0_19
sonic# show image list
Current: SONiC-OS-AF_CLS_SONiC_master_1-0-0_20
Next: SONiC-OS-AF_CLS_SONiC_master_1-0-0_19
Available:
SONiC-OS-AF_CLS_SONiC_master_1-0-0_19
SONiC-OS-AF_CLS_SONiC_master_1-0-0_20

```

#### Set default image
Set the default image that gets activated on all reloads.

**Syntax** : `image set-default <image-name>`

**Command mode** : EXEC

**Parameters** :
- `image-name` : Name of installed image

**Usage** : Use this command to select the image that gets activated on all reloads.

**Supported Releases** :  1.0.0 or later

**Click command** : `sonic-installer set-default <image-name>`

**Example**
```
sonic# image set-default SONiC-OS-prime_master.0-dirty-20230224.135957
Success
sonic#
```

#### Display image install status
Displays the status of recent image install operation.

**Syntax** : `show image status`

**Command mode** : EXEC

**Usage** : Use this command to retrieve the status of recent image install operation.

**Supported Releases** :  1.0.0 or later

**Click command** : None

**Example**
```
sonic# show image status
-----------------------------------------------------------
Global operation status  : install
-----------------------------------------------------------
File operation status    : success
File size(bytes)         : 0
Transfer start time      : 2023-03-13 15:11:40
Transfer end time        : 2023-03-13 15:11:40
-----------------------------------------------------------
Install operation status : success
Install start time       : 2023-03-13 15:11:41
Install end time         : 2023-03-13 15:12:25
sonic#
```

#### Display image list
Displays the list of installed images and their boot setting.

**Syntax** : `show image list`

**Command mode** : EXEC

**Usage** : Use this command to retrieve the list of installed images.

**Supported Releases** :  1.0.0 or later

**Click command** : None

**Example**
```
sonic# show image list
Current: SONiC-OS-prime_master.0-dirty-20230224.135957
Next: SONiC-OS-staging_202205.0-dirty-20230124.120342
Available:
SONiC-OS-staging_202205.0-dirty-20230124.120342
SONiC-OS-prime_master.0-dirty-20230224.135957
sonic#
```

### Process and Memory statistics

#### Display memory statistics
Displays the current memory usage statistics.

**Syntax** : `show system memory`

**Command mode** : EXEC

**Usage** : None

**Supported Releases** :  1.0.0 or later

**Click command** : `show system-memory`

**Example**
```
sonic# show system memory
-----------------------------------------------------------
Attribute            Value/State
-----------------------------------------------------------
Total               :7893
Used                :2122
sonic#
```

#### Display process statistics
Displays the statistics of current processes in the system.

**Syntax** : `show system processes [pid <pid-value>]`

**Command mode** : EXEC

**Parameters** :
- `pid-value` : Process identifier

**Usage** : If the <pid-value> is not passed, CPU utilization of all processes will be displayed

**Supported Releases** :  1.0.0 or later

**Click command** : `show processes {cpu | memory | summary}`

**Example**
```
sonic# show system processes
--------------------------------------------------------------------------
PID       %CPU      %MEMORY   MEM-USAGE(Bytes)      NAME
--------------------------------------------------------------------------
0          0           0          0
1          0           0          0           /sbin/init
10         0           0          0           [rcu_tasks_rude_]
1096       0           0          0           /usr/bin/containerd-shim-runc-v2
11         0           0          0           [rcu_tasks_trace]
110        0           0          0           [hv_vmbus_con]
111        0           0          0           [ata_sff]
112        0           0          0           [hv_pri_chan]
11233      0           0          0           /usr/bin/python3
1128       0           0          0           /usr/bin/python3
113        0           0          0           [scsi_eh_0]
114        0           0          0           [hv_sub_chan]
1167       0           0          0           /bin/bash
1168       0           0          0           python3
117        0           0          0           [scsi_tmf_0]
119        0           0          0           [scsi_eh_1]
12         0           0          0           [ksoftirqd/0]
120        0           0          0           [scsi_tmf_1]
1212       0           0          0           /usr/bin/containerd-shim-runc-v2
1231       0           0          0           /usr/bin/python3
12389      0           0          0           /usr/bin/containerd-shim-runc-v2
--more--

sonic# show system processes pid 10
-----------------------------------------------------------
Attribute            Value/State
-----------------------------------------------------------
Pid                 :10
Name                :[rcu_tasks_rude_]
Args                :None
Start Time          :0
Uptime              :0
Cpu Usage User      :0
Cpu Usage System    :0
Cpu Utilization     :0
Memory Usage        :0
Memory Utilization  :0
sonic#
```

## Bootloader Management

Configure bootloader credential and authentication to update boot configuration and boot image.

### Set Bootloader Credential
Set Bootloader's superuser username and password.

**Syntax** : `bootloader credential set [user <username>] password [hashed] <passtext>`

**Command mode** : EXEC

**Parameters** :
- `username` : Name of the bootloader superuser, defaults to `bootadmin`
- `passtext` : Plaintext or grub-pbkdf2-sha512 hashed password string

**Usage** :
Use this command to set the superuser and its password thereby protecting bootloader<br>against updating the menu entries in the runtime.

**Supported Releases** : 4.1.0 or later

**Click command** :
- `sonic-installer bootloader set-credential [--user=<username>] <--password=<plaintext> | --passhash=<hashed>>`

**Example**
```
sonic# bootloader credential set user root password hashed ggrub.pbkdf2.sha512.25000.69EDFD1F03A0144288D19A338630C6D8BB77EEBDD7DAFB9F93D2BAD7BA17C2F8BF37C698F35E8BF11E8370CE19A39492B2B696B2F6DE3B47688D518AD1FA9F13.523A81638901B2619B2784C2BADF1A815A53C340DE13D89E941199D0B7FB1113D88A1002EF47B5E2436F13B5FD016B544C7EEFAD861BD47DF7129515DE60CB37
%Info: Bootloader configuration success.

sonic# bootloader credential set password TmpPaSs123
%Info: Bootloader configuration success.
```
NOTE: For generating GRUB compatible hashed password (pbkdf2-sha512), either <br>`grub-mkpasswd-pbkdf2` utility or Python's `hash() @ passlib.hash.grub_pbkdf2_sha512`<br>can be used.

### Clear Bootloader Credential
Clear Bootloader's superuser username and password.

**Syntax** : `bootloader credential clear [factory-defaults]`

**Command mode** : EXEC

**Supported Releases** : 4.1.0 or later

**Click command** :
- `sonic-installer bootloader clear-credential [--factory-defaults]`

**Example**
```
sonic# bootloader credential clear
%Info: Bootloader configuration success.

sonic# bootloader credential clear factory-defaults
%Info: Bootloader configuration success.
```

### Boot Authentication
Set boot authentication for SONiC/ONIE menu entry.

**Syntax** : `bootloader authenticate <none | image [sonic] [onie]>`

**Command mode** : EXEC

**Usage** :
Use this command to enable/disable boot authentication for the SONiC/ONIE menu entry.<br>For unattended boot, the defaults are kept to authenticaation disabled.<br>For more secured boot, the ONIE boot entry could be boot authentication enabled,<br>thus allowing only authorized user to boot to ONIE.

**Supported Releases** : 4.1.0 or later

**Click command** :
- `sonic-installer bootloader authenticate [--sonic/--no-sonic] [--onie/--no-onie]`

**Example**
```
sonic# bootloader authenticate none
%Info: Bootloader configuration success.

sonic# bootloader authenticate image onie
%Info: Bootloader configuration success.
```

### Show Bootloader Status
Diplays the status of bootloader credential and boot authentication.

**Syntax** : `show bootloader status`

**Command mode** : EXEC

**Usage** :
This command displays the credential status which is one of `None`, `Default` or `Custom`.<br>The username/password credentials set are not displayed.

**Supported Releases** : 4.1.0 or later

**Click command** :
- `sonic-installer bootloader status`

**Example**
```
sonic# show bootloader status
Bootloader Credential     : Custom
SONiC Boot Authentication : Disabled
ONIE Boot Authentication  : Disabled
```


## ZTP
### ZTP Enable
Enable ZTP feature

**Syntax**: `ztp enable`

**Command mode**: EXEC

**Usage**       : Use `ztp enable` to enable the ZTP feature

**Supported Releases** :  1.1.0 or later

**Click command**: `config ztp enable`

**Example**:
```
sonic# ztp enable
sonic#
```

### ZTP Disable
Disable ZTP feature

**Syntax**: `ztp disable`

**Command mode**: EXEC

**Usage**       : Use `ztp disable` to disable/stop the ZTP feature

**Supported Releases** :  1.1.0 or later

**Click command**: `config ztp disable`

**Example**:
```
sonic# ztp disable
sonic#
```

### ZTP Run
Start ZTP process

**Syntax**: `ztp run`

**Command mode**: EXEC

**Supported Releases** :  1.1.0 or later

**Click command**: `config ztp run`

**Example**:
```
sonic# ztp run
sonic#
```

### Show ZTP status
Display status of ZTP process

**Syntax**: `show ztp status`

**Command mode**: EXEC

**Supported Releases** :  1.1.0 or later

**Click command**: `show ztp status`

**Example**:
```
sonic# show ztp status
ZTP Admin Mode : True
ZTP Service    : Inactive
ZTP Status     : FAILED
ZTP Source     : local-fs (/host/ztp/ztp_data_local.json)
Runtime        : 04m 49s
Timestamp      : 2023-03-02 06:51:50 UTC
ZTP Service is not running
04-download: FAILED
06-snmp: SUCCESS
sonic#
```

### Show ZTP status detail
Display detailed status of ZTP process

**Syntax**: `show ztp status detail`

**Command mode**: EXEC

**Supported Releases** :  1.1.0 or later

**Click command**: `show ztp status --verbose`

**Example**:
```
sonic# show ztp status detail
========================================
                ZTP
========================================
ZTP Admin Mode      : True
ZTP Service         : Processing
ZTP Status          : IN-PROGRESS
ZTP Source          : local-fs (/host/ztp/ztp_data_local.json)
ZTP Runtime         : 02m 50s
ZTP Timestamp       : 2023-04-11 12:55:26 UTC
ZTP JSON Version    : 1.0
(01m 20s) Downloading plugin 'tftp://188.188.36.36/chg_mac.sh' for configuration section 05-provisioning-script
---------------------------------------------
03-connectivity-check
---------------------------------------------
Status              : SUCCESS
Runtime             : 05s
Timestamp           : 2023-04-11 12:56:53 UTC
Ignore Result       : False
---------------------------------------------
05-provisioning-script
---------------------------------------------
Status              : IN-PROGRESS
Runtime             :
Timestamp           : 2023-04-11 12:56:56 UTC
Ignore Result       : False
---------------------------------------------
06-snmp
---------------------------------------------
Status              : Not Started
Runtime             :
Timestamp           : 2023-04-11 12:55:26 UTC
Ignore Result       : False
```

##ARP and NDP commands
####show arp
Displays the IPv4 ARP neighbor Cache. If the L3 Interface that the ARP entry is learnt is on a Vlan, 
It also displays the Egress L2 Port through which the Neighbour MAC is reachable if not a "-". 
If Neighbour is not Reachable or Invalid the MAC is displayed as "-" 

**Syntax**: `show arp [ vrf <vrfname>] [ <interfacename> | <ipv4address> ]`

**Parameters**:
- `vrfname` - Name of the VRF.
              accepts String of Maximum 32 Characters
- `interfacename` - Name of the L3 Interface like Ethernet0, PortChannel10, Loopback2, Vlan100 or Management0
- `ipv4address` - IPv4 Neighbour Address 

**Command mode**: EXEC

**Usage**:
- <vrfname> is optional
  If <vrfname> is not given, all the VRFs Neighbour Cache is retrieved
- <interfacename> is optional
  If <interfacename> is not given all Neighbour Cache entries learnt on L3 Interfaces is retrieved
- <ipv4address> is optional, by default all Neighbours are retrieved if not specified

**Click command**:
- `show arp -if <interface> [<ipv4address>]`

**Example**:
```

sonic# show arp vrf Vrf-101
Address         MacAddress         Iface      Vlan  Status
--------------  -----------------  -------  ------  --------
101.101.101.8   00:00:23:88:87:33  -           101  STALE
101.101.101.11  00:00:23:88:87:36  -           101  STALE
101.101.101.10  00:00:23:88:87:35  -           101  STALE
101.101.101.12  00:00:23:88:87:37  -           101  STALE
101.101.101.3   00:00:23:88:87:2e  -           101  STALE
101.101.101.2   00:00:00:0f:d5:29  -           101  STALE
101.101.101.5   00:00:23:88:87:30  -           101  STALE
101.101.101.4   00:00:23:88:87:2f  -           101  STALE
101.101.101.7   00:00:23:88:87:32  -           101  STALE
101.101.101.6   00:00:23:88:87:31  -           101  STALE
101.101.101.9   00:00:23:88:87:34  -           101  STALE
Total number of entries 11

sonic# show arp
Address         MacAddress         Iface        Vlan    Status
--------------  -----------------  -----------  ------  ---------
101.101.101.8   00:00:23:88:87:33  -            101     STALE
101.101.101.11  00:00:23:88:87:36  -            101     STALE
101.101.101.10  00:00:23:88:87:35  -            101     STALE
10.208.81.253   74:86:e2:51:b4:27  Management0  -       STALE
10.208.81.254   74:86:e2:51:2c:27  Management0  -       STALE
101.101.101.12  00:00:23:88:87:37  -            101     STALE
10.208.81.1     00:00:5e:00:01:02  Management0  -       REACHABLE
101.101.101.3   00:00:23:88:87:2e  -            101     STALE
101.101.101.2   00:00:00:0f:d5:29  -            101     STALE
3.1.1.1         -                  Ethernet5    -       FAILED
101.101.101.5   00:00:23:88:87:30  -            101     STALE
101.101.101.4   00:00:23:88:87:2f  -            101     STALE
101.101.101.7   00:00:23:88:87:32  -            101     STALE
101.101.101.6   00:00:23:88:87:31  -            101     STALE
101.101.101.9   00:00:23:88:87:34  -            101     STALE
Total number of entries 15
sonic#
sonic# show arp Management0
Address        MacAddress         Iface        Vlan    Status
-------------  -----------------  -----------  ------  ---------
10.208.81.253  74:86:e2:51:b4:27  Management0  -       STALE
10.208.81.254  74:86:e2:51:2c:27  Management0  -       STALE
10.208.81.1    00:00:5e:00:01:02  Management0  -       REACHABLE
Total number of entries 3
sonic#
sonic# show arp 3.1.1.1
Address    MacAddress    Iface      Vlan    Status
---------  ------------  ---------  ------  --------
3.1.1.1    -             Ethernet5  -       FAILED
Total number of entries 1

```

####show ndp
Displays the IPv6 neighbor Cache. If the L3 Interface that the Neighbour entry is learnt is on a Vlan, 
It also displays the Egress L2 Port through which the Neighbour MAC is reachable if not a "-". 
If Neighbour is not Reachable or Invalid the MAC is displayed as "-" 

**Syntax**: `show ndp [ vrf <vrfname>] [ <interfacename> | <ipv6address> ]`

**Parameters**:
- `vrfname` - Name of the VRF.
              accepts String of Maximum 32 Characters
- `interfacename` - Name of the L3 Interface like Ethernet0, PortChannel10, Loopback2, Vlan100 or Management0
- `ipv6address` - IPv6 Neighbour Address 

**Command mode**: EXEC

**Usage**:
- <vrfname> is optional
  If <vrfname> is not given, all the VRFs Neighbour Cache is retrieved
- <interfacename> is optional
  If <interfacename> is not given all Neighbour Cache entries learnt on L3 Interfaces is retrieved
- <ipv6address> is optional, by default all Neighbours are retrieved if not specified

**Click command**:
- `show ndp -if <interface> [<ipv6address>]`

**Example**:
```

sonic# show ndp vrf Vrf-101
Address                   MacAddress         Iface      Vlan  Status
------------------------  -----------------  -------  ------  --------
2023::b:2                 -                  -           101  FAILED
2023::6:2                 00:00:23:88:87:47  -           101  STALE
2023::1:2                 00:00:23:88:87:42  -           101  STALE
2023::8:2                 00:00:23:88:87:49  -           101  STALE
fe80::200:23ff:fe88:8738  00:00:23:88:87:38  -           101  STALE
2023::3:2                 00:00:23:88:87:44  -           101  STALE
2023::a:2                 00:00:23:88:87:4b  -           101  STALE
2023::5:2                 00:00:23:88:87:46  -           101  STALE
2023::7:2                 00:00:23:88:87:48  -           101  STALE
2023::2:2                 00:00:23:88:87:43  -           101  STALE
2023::9:2                 00:00:23:88:87:4a  -           101  STALE
2023::4:2                 00:00:23:88:87:45  -           101  STALE
Total number of entries 12

sonic# show ndp
Address                    MacAddress         Iface        Vlan    Status
-------------------------  -----------------  -----------  ------  ---------
fe80::e48:c6ff:fe85:ef5a   0c:48:c6:85:ef:5a  Management0  -       STALE
2023::b:2                  -                  -            101     FAILED
2023::6:2                  00:00:23:88:87:47  -            101     STALE
fe80::eab5:d0ff:fe82:894   e8:b5:d0:82:08:94  Management0  -       STALE
2023::1:2                  00:00:23:88:87:42  -            101     STALE
fe80::36ad:61ff:fef1:a4fa  34:ad:61:f1:a4:fa  Management0  -       STALE
2023::8:2                  00:00:23:88:87:49  -            101     STALE
fe80::200:23ff:fe88:8738   00:00:23:88:87:38  -            101     STALE
2023::3:2                  00:00:23:88:87:44  -            101     STALE
fe80::eab5:d0ff:fe81:ec94  e8:b5:d0:81:ec:94  Management0  -       REACHABLE
2010::2                    -                  Ethernet5    -       FAILED
fe80::eab5:d0ff:fe81:b694  e8:b5:d0:81:b6:94  Management0  -       REACHABLE
2023::a:2                  00:00:23:88:87:4b  -            101     STALE
2023::5:2                  00:00:23:88:87:46  -            101     STALE
2023::7:2                  00:00:23:88:87:48  -            101     STALE
2023::2:2                  00:00:23:88:87:43  -            101     STALE
2023::9:2                  00:00:23:88:87:4a  -            101     STALE
fe80::36ad:61ff:fef1:a56c  34:ad:61:f1:a5:6c  Ethernet5    -       STALE
2023::4:2                  00:00:23:88:87:45  -            101     STALE
fe80::eab5:d0ff:fe81:f794  e8:b5:d0:81:f7:94  Management0  -       STALE
Total number of entries 20
sonic#
sonic# show ndp Management0
Address                    MacAddress         Iface        Vlan    Status
-------------------------  -----------------  -----------  ------  ---------
fe80::e48:c6ff:fe85:ef5a   0c:48:c6:85:ef:5a  Management0  -       STALE
fe80::eab5:d0ff:fe82:894   e8:b5:d0:82:08:94  Management0  -       STALE
fe80::36ad:61ff:fef1:a4fa  34:ad:61:f1:a4:fa  Management0  -       STALE
fe80::eab5:d0ff:fe81:ec94  e8:b5:d0:81:ec:94  Management0  -       REACHABLE
fe80::eab5:d0ff:fe81:b694  e8:b5:d0:81:b6:94  Management0  -       REACHABLE
fe80::eab5:d0ff:fe81:f794  e8:b5:d0:81:f7:94  Management0  -       STALE
Total number of entries 6
sonic#
sonic# show ndp 2023::a:2
Address    MacAddress         Iface      Vlan  Status
---------  -----------------  -------  ------  --------
2023::a:2  00:00:23:88:87:4b  -           101  STALE
Total number of entries 1

```
####clear arp
Clears the IPv4 ARP neighbor Cache by Neighbour IPv4 Address or L3 Interface or VRF .  

**Syntax**: `clear arp [ vrf <vrfname>] [ <interfacename> | <ipv4address> ]`

**Parameters**:
- `vrfname` - Name of the VRF.
              accepts String of Maximum 32 Characters
- `interfacename` - Name of the L3 Interface like Ethernet0, PortChannel10, Loopback2, Vlan100 or Management0
- `ipv4address` - IPv4 Neighbour Address 

**Command mode**: EXEC

**Usage**:
- <vrfname> is optional
  If <vrfname> is not given, all the VRFs Neighbour Cache is retrieved
- <interfacename> is optional
  If <interfacename> is not given all Neighbour Cache entries learnt on L3 Interfaces is retrieved
- <ipv4address> is optional, by default all Neighbours are retrieved if not specified

**Click command**:
- `sonic-clear arp [<ipv4address>]`

**Example**:
```

sonic# show arp vrf Vrf-101
Address         MacAddress         Iface      Vlan  Status
--------------  -----------------  -------  ------  --------
101.101.101.8   00:00:23:88:87:33  -           101  STALE
101.101.101.11  00:00:23:88:87:36  -           101  STALE
101.101.101.10  00:00:23:88:87:35  -           101  STALE
101.101.101.12  00:00:23:88:87:37  -           101  STALE
101.101.101.3   00:00:23:88:87:2e  -           101  STALE
101.101.101.2   00:00:00:0f:d5:29  -           101  STALE
101.101.101.5   00:00:23:88:87:30  -           101  STALE
101.101.101.4   00:00:23:88:87:2f  -           101  STALE
101.101.101.7   00:00:23:88:87:32  -           101  STALE
101.101.101.6   00:00:23:88:87:31  -           101  STALE
101.101.101.9   00:00:23:88:87:34  -           101  STALE
Total number of entries 11
sonic# clear arp vrf Vrf-101
sonic# show arp vrf Vrf-101
Address    MacAddress    Iface    Vlan    Status
---------  ------------  -------  ------  --------
Total number of entries 0
sonic#

```

####clear ndp
Clears the IPv6 ND neighbor Cache by Neighbour IPv6 Address or L3 Interface or VRF .  

**Syntax**: `clear ndp [ vrf <vrfname>] [ <interfacename> | <ipv6address> ]`

**Parameters**:
- `vrfname` - Name of the VRF.
              accepts String of Maximum 32 Characters
- `interfacename` - Name of the L3 Interface like Ethernet0, PortChannel10, Loopback2, Vlan100 or Management0
- `ipv6address` - IPv6 Neighbour Address 

**Command mode**: EXEC

**Usage**:
- <vrfname> is optional
  If <vrfname> is not given, all the VRFs Neighbour Cache is retrieved
- <interfacename> is optional
  If <interfacename> is not given all Neighbour Cache entries learnt on L3 Interfaces is retrieved
- <ipv6address> is optional, by default all Neighbours are retrieved if not specified

**Click command**:
- `sonic-clear ndp [<ipv6address>]`

**Example**:
```

sonic# show ndp vrf Vrf-101
Address                   MacAddress         Iface      Vlan  Status
------------------------  -----------------  -------  ------  --------
2023::b:2                 -                  -           101  FAILED
2023::6:2                 00:00:23:88:87:47  -           101  STALE
2023::1:2                 00:00:23:88:87:42  -           101  STALE
2023::8:2                 00:00:23:88:87:49  -           101  STALE
fe80::200:23ff:fe88:8738  00:00:23:88:87:38  -           101  STALE
2023::3:2                 00:00:23:88:87:44  -           101  STALE
2023::a:2                 00:00:23:88:87:4b  -           101  STALE
2023::5:2                 00:00:23:88:87:46  -           101  STALE
2023::7:2                 00:00:23:88:87:48  -           101  STALE
2023::2:2                 00:00:23:88:87:43  -           101  STALE
2023::9:2                 00:00:23:88:87:4a  -           101  STALE
2023::4:2                 00:00:23:88:87:45  -           101  STALE
Total number of entries 12
sonic# clear ndp vrf Vrf-101
sonic# show ndp vrf Vrf-101
Address    MacAddress    Iface    Vlan    Status
---------  ------------  -------  ------  --------
Total number of entries 0
sonic#

```

##Miscellaneous Show commands
####show vrf
Display the list of configured VRFs and the bound L3 Interfaces in that VRF

**Syntax**: `show vrf [<vrfname>]`

**Parameters**:
- `vrfname` - Name of the VRF which needs to be fetched.
accepts String of Maximum 32 Characters

**Command mode**: EXEC

**Usage**:
- <vrfname> is optional
- If <vrfname> is not given, all the VRFs are retrieved

**Click command**:
- `show vrf [<vrfname>]`

**Example**:
```

sonic# show vrf
VRF      Interfaces
-------  ------------
Vrf-1    Ethernet0
Vrf-101  Vlan101
Vrf-2    Ethernet1

sonic# show vrf Vrf-1
VRF    Interfaces
-----  ------------
Vrf-1  Ethernet0

```

####show management_interface address
Displays the IPv4/IPv6 Address configured on the Management Interface 

**Syntax**: `show managment_interface address`

**Parameters**:
- None

**Command mode**: EXEC

**Usage**:
None

**Click command**:
- `show management_interface address`

**Example**:
```

sonic# show management_interface address
Management IP address = 10.208.81.122/24
Management Network Default Gateway = 10.208.81.1

```

####show mgmt-vrf 
Displays the Management VRF bound interfaces and its routes 

**Syntax**: `show mgmt-vrf [routes]`

**Parameters**:
- None

**Command mode**: EXEC

**Usage**:
None

**Click command**:
- `show mgmt-vrf [routes]`

**Example**:
```

sonic# show mgmt-vrf

ManagementVRF : Enabled

Management VRF interfaces in Linux:
170: mgmt: <NOARP,MASTER,UP,LOWER_UP> mtu 65575 qdisc noqueue state UP mode DEFAULT group default qlen 1000
    link/ether 4a:b0:a0:33:c8:66 brd ff:ff:ff:ff:ff:ff promiscuity 0 minmtu 1280 maxmtu 65575
    vrf table 5000 addrgenmode eui64 numtxqueues 1 numrxqueues 1 gso_max_size 65536 gso_max_segs 65535

2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq master mgmt state UP mode DEFAULT group default qlen 1000
    link/ether 34:ad:61:f1:a2:87 brd ff:ff:ff:ff:ff:ff
171: lo-m: <BROADCAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc noqueue master mgmt state UNKNOWN mode DEFAULT group default qlen 1000
    link/ether 76:f1:c4:b7:9e:52 brd ff:ff:ff:ff:ff:ff

sonic# show mgmt-vrf routes

Routes in Management VRF Routing Table:
default via 10.208.81.1 dev eth0 metric 201
unreachable default metric 4278198272
broadcast 10.208.81.0 dev eth0 proto kernel scope link src 10.208.81.122
10.208.81.0/24 dev eth0 proto kernel scope link src 10.208.81.122
local 10.208.81.122 dev eth0 proto kernel scope host src 10.208.81.122
broadcast 10.208.81.255 dev eth0 proto kernel scope link src 10.208.81.122
broadcast 127.0.0.0 dev lo-m proto kernel scope link src 127.0.0.1
127.0.0.0/16 dev lo-m proto kernel scope link src 127.0.0.1
local 127.0.0.1 dev lo-m proto kernel scope host src 127.0.0.1
broadcast 127.0.255.255 dev lo-m proto kernel scope link src 127.0.0.1


```

####show ip interfaces 
Displays the IPv4 Address configured on an L3 Interface and its bound VRF (if any configured)

**Syntax**: `show ip interfaces [<intrfacename>]`

**Parameters**:
- <interfacename> - The L3 Interface name like Ethernet0, PortChannel1, Vlan100, Loopback10 or Management0

**Command mode**: EXEC

**Usage**:
 To find the IPv4 Addresses configured on an L3 Interface, also the VRF to which it is bound to (if any)

**Click command**:
- `show ip interfaces`

**Example**:
```

sonic# show ip interfaces
Interface     Master    Address           Admin/Oper
------------  --------  ----------------  ------------
Ethernet1     Vrf-2     4.4.4.1/24        UP/UP
Ethernet5               3.1.1.2/24        UP/UP
Loopback0               111.11.1.1/32     UP/UP
PortChannel1            5.5.5.1/24        UP/DOWN
Vlan101       Vrf-101   101.101.101.1/24  UP/UP
Management0   mgmt      10.208.81.122/24  UP/UP

sonic# show ip interfaces Management0
Interface    Master    Address           Admin/Oper
-----------  --------  ----------------  ------------
Management0  mgmt      10.208.81.122/24  UP/UP
sonic#
sonic# show ip interfaces Vlan101
Interface    Master    Address           Admin/Oper
-----------  --------  ----------------  ------------
Vlan101      Vrf-101   101.101.101.1/24  UP/UP

```

####show ipv6 interfaces 
Displays the IPv6 Address configured on an L3 Interface and its bound VRF (if any configured).
It also displays the auto-configured Link-local IPv6, by the Kernel

**Syntax**: `show ipv6 interfaces [<intrfacename>]`

**Parameters**:
- <interfacename> - The L3 Interface name like Ethernet0, PortChannel1, Vlan100, Loopback10 or Management0

**Command mode**: EXEC

**Usage**:
 To find the IPv6 Addresses configured on an L3 Interface, also the VRF to which it is bound to (if any)

**Click command**:
- `show ipv6 interfaces`

**Example**:
```

sonic# show ipv6 interfaces
Interface       Master    Address                       Admin/Oper
--------------  --------  ----------------------------  ------------
Ethernet0       Vrf-1     fe80::36ad:61ff:fef1:a287/64  UP/UP
Ethernet1       Vrf-2     fe80::36ad:61ff:fef1:a287/64  UP/UP
Ethernet2                 fe80::36ad:61ff:fef1:a287/64  UP/UP
Ethernet3                 fe80::36ad:61ff:fef1:a287/64  UP/UP
Ethernet4                 fe80::36ad:61ff:fef1:a287/64  UP/UP
Ethernet5                 2010::1/64                    UP/UP
                          fe80::36ad:61ff:fef1:a287/64
Ethernet6                 fe80::36ad:61ff:fef1:a287/64  UP/UP
Ethernet7                 fe80::36ad:61ff:fef1:a287/64  UP/UP
Ethernet47                fe80::36ad:61ff:fef1:a287/64  UP/DOWN
Loopback0                 fe80::70ba:7dff:fe90:792b/64  UP/UP
Loopback1                 fe80::14cb:54ff:fe95:32c7/64  UP/UP
PortChannel256            2011::1/64                    UP/DOWN
Vlan101         Vrf-101   2023::1:1/64                  UP/UP
                          fe80::36ad:61ff:fef1:a287/64
Management0     mgmt      fe80::36ad:61ff:fef1:a287/64  UP/UP

sonic# show ipv6 interfaces Management0
Interface    Master    Address                       Admin/Oper
-----------  --------  ----------------------------  ------------
Management0  mgmt      fe80::36ad:61ff:fef1:a287/64  UP/UP
sonic#
sonic# show ipv6 interfaces PortChannel256
Interface       Master    Address     Admin/Oper
--------------  --------  ----------  ------------
PortChannel256            2011::1/64  UP/DOWN
sonic#
sonic# show ipv6 interfaces Ethernet5
Interface    Master    Address                       Admin/Oper
-----------  --------  ----------------------------  ------------
Ethernet5              2010::1/64                    UP/UP
                       fe80::36ad:61ff:fef1:a287/64
sonic#

```

## Quality of Service (QoS)
QoS manages network resources and prioritizes traffic to balance system resources.
### Congestion avoidance (Weighted Early Random Detection)
#### qos wred-profile
Configure a WRED profile

**Syntax** : `qos wred-profile <name>`

**Parameters** :
- `name` - Alphanumeric string including - and _ (Max: 32 characters)

**Command mode** : CONFIG

**Usage**       :
- Use `no qos wred-profile <name>` to remove a WRED profile

**Supported Releases** :  1.0.0 or later

**Click command** : None

**Example**
```
sonic(config)# qos wred-profile test1
sonic(config-wred-test1)#

sonic(config)# no qos wred-profile test1
```

#### random-detect color
Configure WRED threshold parameters for different colors in WRED CONFIGURATION mode

**Syntax** : `random-detect color <color-name> min-threshold <min-th-value> max-threshold <max-th-value> drop-probability <drop-rate>`

**Parameters** :
- `color-name` - Enter the color of drop precedence for the WRED profile. The available options are
green, yellow, and red
- `min-th-value` - Enter the minimum threshold value for the specified color, from 1 to 67108608
- `max-th-value` - Enter the maximum threshold value for the specified color, from 1 to 67108608
- `drop-rate` - Enter the rate of drop precedence in percentage, from 0 to 100

**Command mode** : WRED CONFIGURATION

**Usage**       :
- Use `no random-detect color <color-name>` to restores the default settings of a WRED drop profile
- By default, the parameters are not configured.

**Supported Releases** :  1.0.0 or later

**Click command** : None

**Example**
```
sonic(config-wred-test1)# random-detect color green min-threshold 100 max-threshold 300 drop-probability 100
sonic(config-wred-test1)# random-detect color yellow min-threshold 256 max-threshold 2560 drop-probability 50
sonic(config-wred-test1)#

sonic(config-wred-test1)# no random-detect color green
sonic(config-wred-test1)# no random-detect color yellow
```


#### random-detect ecn
Enables explicit congestion notification (ECN) for different colors of a WRED profile

**Syntax** : `random-detect ecn <value>`

**Parameters** :
- `value` - The available options are :
    - `green` Enable ECN marking for green color. Yellow and red are disabled
    - `yellow`  Enable ECN marking for yellow color. Green and red are disabled
    - `red` Enable ECN marking for red color. Green and yellow are disabled
    - `green_yellow` Enable ECN marking for green and yellow colors. Red is disabled
    - `green_red` Enable ECN marking for green and red colors. Yellow is disabled
    - `yellow_red`  Enable ECN marking for yellow and red colors. Green is disabled
    - `all` Enable ECN marking for all colors

**Command mode** : WRED CONFIGURATION

**Usage**       :
- Use `no random-detect ecn` to restores the default settings `none` for ECN
- By default, Disable ECN marking for all colors

**Supported Releases** :  1.0.0 or later

**Click command** : None

**Example**
```
sonic(config-wred-test1)# random-detect ecn green
sonic(config-wred-test1)# random-detect ecn red

sonic(config-wred-test1)# random-detect ecn yellow_red

sonic(config-wred-test1)# no random-detect ecn
```


#### show qos wred-profile
Displays the details of WRED profile configuration

**Syntax** : `show qos wred-profile [<wred-profile-name>]`

**Parameters** :
- `wred-profile-name` - (Optional) Alphanumeric string including - and _ (Max: 32 characters)

**Command mode** : EXEC

**Usage**       : If `wred-profile-name` is not given all WRED profile settings will be dispalyed.

**Supported Releases** :  1.0.0 or later

**Click command** : None

**Example**
```
sonic# show qos wred-profile
                  |               Green           |               Yellow          |               Red             |            |
Profile Name      |-------------------------------|-------------------------------|-------------------------------|            |
                  |       MIN        MAX DROP-RATE|       MIN        MAX DROP-RATE|       MIN        MAX DROP-RATE|         ECN|
                  |     Bytes      Bytes         %|     Bytes      Bytes         %|     Bytes      Bytes         %|            |
------------------|-------------------------------|-------------------------------|-------------------------------|------------|
12                |                               |       256       2560        50|                               |        none|
------------------|-------------------------------|-------------------------------|-------------------------------|------------|
test1             |       100        300       100|       256       2560        50|                               |       green|
------------------|-------------------------------|-------------------------------|-------------------------------|------------|
sonic#

sonic# show qos wred-profile test1
                  |               Green           |               Yellow          |               Red             |            |
Profile Name      |-------------------------------|-------------------------------|-------------------------------|            |
                  |       MIN        MAX DROP-RATE|       MIN        MAX DROP-RATE|       MIN        MAX DROP-RATE|         ECN|
                  |     Bytes      Bytes         %|     Bytes      Bytes         %|     Bytes      Bytes         %|            |
------------------|-------------------------------|-------------------------------|-------------------------------|------------|
test1             |       100        300       100|       256       2560        50|                               |       green|
------------------|-------------------------------|-------------------------------|-------------------------------|------------|
sonic#
```

#### show qos wred interface
Displays the WRED configuration applied to a specific interface queue.

**Syntax** : `show qos wred interface Ethernet {all | <if-id> [queue <qindex-id>]}`

**Parameters** :
- `if-id` - Ethernet interface identifier
- `qindex-id` - Individual queue index. valid value: <0-7>

**Command mode** : EXEC

**Usage**       :
- If selected `all`, displays the WRED configuration applied to all interface queues.
- If `qindex-id` is not given, displays the WRED configuration applied to all queues of an interface.

**Supported Releases** :  1.0.0 or later

**Click command** : None

**Example**
```
sonic# show qos wred interface Ethernet all

Ethernet1
 queue:   1
     wred_profile:  test1
 queue:   3
     wred_profile:  12
 queue:   5
     wred_profile:  12

Ethernet46
 queue:   2
     wred_profile:  test1
 queue:   4
     wred_profile:  test1
sonic#
sonic# show qos wred interface Ethernet 1

Ethernet1
 queue:   1
     wred_profile:  test1
 queue:   3
     wred_profile:  12
 queue:   5
     wred_profile:  12
sonic#
sonic# show qos wred interface Ethernet 1 queue 1

Ethernet1
 queue:   1
     wred_profile:  test1
sonic#
sonic# show qos wred interface Ethernet 1 queue 5

Ethernet1
 queue:   5
     wred_profile:  12
sonic#
```


### QoS Maps
#### Create Dot1p to Traffic Class map
Dot1p-to-tc mapping assigns an 802.1p priority to the internal traffic class on the device. This command creates a mapping with default assignments i.e. dot1p priority 0 to internal traffic class 0, dot1p priority 1 to internal traffic class 0, dot1p priority 2 to internal traffic class 0, and so on.

**Syntax**: `qos map dot1p-tc <qos-map-name>`

**Parameters**  :
- `qos-map-name` - Enter the name of the qos map (Alphanumeric string including - and _ upto 32 characters)

**Command mode** : CONFIG

**Usage**       : Use `no qos map dot1p-tc <qos-map-name>` to unconfigure a qos map.

**Click command** : None

**Example**
```
sonic(config)# qos map dot1p-tc MAP1
sonic(config)# no qos map dot1p-tc MAP1
```
#### Configure Dot1p to Traffic Class map entries
Configures the dot1p priority to traffic class map entries

**Syntax**: `dot1p <dot1p-values> traffic-class <traffic-class>`

**Parameters**  :
- `dot1p-values` - Enter the dot1p values as a range or/and  comma separated list i.e. (-) or (,) separated individual dot1p and range of dot1p. Ex: 0,2-7

**Command mode** : QoS map configuration mode

**Usage**       : Use `no dot1p <dot1p-values>` to unconfigure a qos mapping and reset it to default mapping

**Click command** : None

**Example**
```
sonic(config-dot1p-tc-MAP1)# dot1p 0-2,7 traffic-class 0
sonic(config-dot1p-tc-MAP1)# no dot1p 0-2,7
```
#### Create DSCP to Traffic Class map
Dscp-to-tc mapping assigns a DSCP to the internal traffic class on the device. This command creates a mapping with default assignments i.e. DSCP 0 to internal traffic class 0, DSCP 1 to internal traffic class 0, and so on.

**Syntax**: `qos map dscp-tc <qos-map-name>`

**Parameters**  :
- `qos-map-name` - Enter the name of the qos map (Alphanumeric string including - and _ upto 32 characters)

**Command mode** : CONFIG

**Usage**       : Use `no qos map dscp-tc <qos-map-name>` to unconfigure a qos map.

**Click command** : None

**Example**
```
sonic(config)# qos map dscp-tc MAP1
sonic(config)# no qos map dscp-tc MAP1
```
#### Configure DSCP to Traffic Class map entries
Configures the DSCP to traffic class map entries

**Syntax**: `dscp <dscp-values> traffic-class <traffic-class>`

**Parameters**  :
- `dscp-values` - Enter the dscp values as a range or/and  comma separated list i.e. (-) or (,) separated individual dscp and range of dscp. Ex: 5,18,22-37
- `traffic-class` - Enter the traffic class value to be mapped to the dot1p(s)

**Command mode** : QoS map configuration mode

**Usage**       : Use `no dscp <dscp-values>` to unconfigure a qos mapping and reset it to default mapping

**Click command** : None

**Example**
```
sonic(config-dscp-tc-MAP1)# dscp 10-22,37 traffic-class 0
sonic(config-dscp-tc-MAP1)# no dscp 12
```
#### Create Traffic Class to Dot1p map
Tc-to-dot1p mapping assigns internal traffic class to 802.1p priority for remarking on outgoing packets. This command creates a mapping with default assignments i.e. internal traffic class 0 to dot1p 0, internal traffic class 1 to dot1p 0, and so on.

**Syntax**: `qos map tc-dot1p <qos-map-name>`

**Parameters**  :
- `qos-map-name` - Enter the name of the qos map (Alphanumeric string including - and _ upto 32 characters)

**Command mode** : CONFIG

**Usage**       : Use `no qos map tc-dot1p <qos-map-name>` to unconfigure a qos map.

**Click command** : None

**Example**
```
sonic(config)# qos map tc-dot1p MAP1
sonic(config)# no qos map tc-dot1p MAP1
```
#### Configure Traffic Class to Dot1p map entries
Configures the traffic class to dot1p priority map entries

**Syntax**: `traffic-class <tc-values> dot1p <dot1p>`

**Parameters**  :
- `tc-values` - Enter the traffic class values as a range or/and  comma separated list i.e. (-) or (,) separated individual tc and range of tc. Ex: 0,2-7
- `dot1p` - Enter the dot1p value to be mapped to the traffic class(es)

**Command mode** : QoS map configuration mode

**Usage**       : Use `no traffic-class <tc-values>` to unconfigure a qos mapping and reset it to default mapping

**Click command** : None

**Example**
```
sonic(config-tc-dot1p-MAP1)# traffic-class 2-4 dot1p 3
sonic(config-tc-dot1p-MAP1)# no traffic-class 2-4
```
#### Create Traffic Class to DSCP map
Tc-to-dscp mapping assigns internal traffic class to DSCP for remarking on outgoing packets. This command creates a mapping with default assignments i.e. internal traffic class 0 to dscp 0, internal traffic class 1 to dscp 0, and so on.

**Syntax**: `qos map tc-dscp <qos-map-name>`

**Parameters**  :
- `qos-map-name` - Enter the name of the qos map (Alphanumeric string including - and _ upto 32 characters)

**Command mode** : CONFIG

**Usage**       : Use `no qos map tc-dscp <qos-map-name>` to unconfigure a qos map.

**Click command** : None

**Example**
```
sonic(config)# qos map tc-dscp MAP1
sonic(config)# no qos map tc-dscp MAP1
```
#### Configure Traffic Class to DSCP map entries
Configures the traffic class to dscp map entries

**Syntax**: `traffic-class <tc-values> dscp <dscp>`

**Parameters**  :
- `tc-values` - Enter the traffic class values as a range or/and  comma separated list i.e. (-) or (,) separated individual tc and range of tc. Ex: 0,2-7
- `dscp` - Enter the dscp value to be mapped to the traffic class(es)

**Command mode** : QoS map configuration mode

**Usage**       : Use `no traffic-class <tc-values>` to unconfigure a qos mapping and reset it to default mapping

**Click command** : None

**Example**
```
sonic(config-tc-dscp-MAP1)# traffic-class 2-4 dscp 3
sonic(config-tc-dscp-MAP1)# no traffic-class 5
```
#### Create Traffic Class to Queue map
Tc-to-queue mapping assigns traffic class to a queue. This command creates a mapping with default assignments i.e. internal traffic class 0 to queue 0, internal traffic class 1 to queue 0, and so on. Note that this has to be applied on the ingress interface.

**Syntax**: `qos map tc-queue <qos-map-name>`

**Parameters**  :
- `qos-map-name` - Enter the name of the qos map (Alphanumeric string including - and _ upto 32 characters)

**Command mode** : CONFIG

**Usage**       : Use `no qos map tc-queue <qos-map-name>` to unconfigure a qos map.

**Click command** : None

**Example**
```
sonic(config)# qos map tc-queue MAP1
sonic(config)# no qos map tc-queue MAP1
```
#### Configure Traffic Class to Queue map entries
Configures the traffic class to queue map entries

**Syntax**: `traffic-class <tc-values> queue <queue>`

**Parameters**  :
- `tc-values` - Enter the traffic class values as a range or/and  comma separated list i.e. (-) or (,) separated individual tc and range of tc. Ex: 0,2-7
- `queue` - Enter the queue value to be mapped to the traffic class(es)

**Command mode** : QoS map configuration mode

**Usage**       : Use `no traffic-class <tc-values>` to unconfigure a qos mapping and reset it to default mapping

**Click command** : None

**Example**
```
sonic(config-tc-queue-MAP1)# traffic-class 2-4 queue 3
sonic(config-tc-queue-MAP1)# no traffic-class 3
```
#### Create Traffic Class to Priority Group map
Tc-to-priority-group mapping assigns traffic class to a priority group. This command creates a mapping with default assignments i.e. internal traffic class 0 to queue 0, internal traffic class 1 to queue 0, and so on. 

**Syntax**: `qos map tc-pg <qos-map-name>`

**Parameters**  :
- `qos-map-name` - Enter the name of the qos map (Alphanumeric string including - and _ upto 32 characters)

**Command mode** : CONFIG

**Usage**       : Use `no qos map tc-pg <qos-map-name>` to unconfigure a qos map.

**Click command** : None

**Example**
```
sonic(config)# qos map tc-pg MAP1
sonic(config)# no qos map tc-pg MAP1
```
#### Configure Traffic Class to Priority Group map entries
Configures the traffic class to priority-group map entries

**Syntax**: `traffic-class <tc-values> priority-group <priority-group>`

**Parameters**  :
- `tc-values` - Enter the traffic class values as a range or/and  comma separated list i.e. (-) or (,) separated individual tc and range of tc. Ex: 0,2-7
- `priority-group` - Enter the priority group value to be mapped to the traffic class(es)

**Command mode** : QoS map configuration mode

**Usage**       : Use `no traffic-class <tc-values>` to unconfigure a qos mapping and reset it to default mapping

**Click command** : None

**Example**
```
sonic(config-tc-pg-MAP1)# traffic-class 2-4 priority-group 3
sonic(config-tc-pg-MAP1)# no traffic-class 3
```
#### Create PFC Priority to Queue map
pfc-to-priority-queue mapping assigns PFC packet priority to a queue. This command creates a mapping with default assignments i.e. pfc 0 to queue 0, pfc 1 to queue 0, and so on. 

**Syntax**: `qos map pfc-priority-queue <qos-map-name>`

**Parameters**  :
- `qos-map-name` - Enter the name of the qos map (Alphanumeric string including - and _ upto 32 characters)

**Command mode** : CONFIG

**Usage**       : Use `no qos map pfc-priority-queue <qos-map-name>` to unconfigure a qos map.

**Click command** : None

**Example**
```
sonic(config)# qos map pfc-priority-queue MAP1
sonic(config)# no qos map pfc-priority-queue MAP1
```
#### Configure PFC Priority to Queue map entries
Configures the pfc priority to queue map entries

**Syntax**: `pfc-priority <pfc-priority> queue <queue-index>`

**Parameters**  :
- `pfc-priority` - Enter the PFC priority values as a range or/and  comma separated list i.e. (-) or (,) separated individual pfc priority and range of pfc priority. Ex: 0,2-7
- `queue-index` - Enter the queue value to be mapped to the pfc priority

**Command mode** : QoS map configuration mode

**Usage**       : Use `no pfc-priority <pfc-priority>` to unconfigure a qos mapping and reset it to default mapping

**Click command** : None

**Example**
```
sonic(config-pfc-priority-queue-MAP1)# pfc-priority 2-4 queue 3
sonic(config-pfc-priority-queue-MAP1)# no pfc-priority 3
```
#### Show QoS Maps
Displays the QoS maps configured by the user

**Syntax**: `show qos maps {dot1p-tc|dscp-tc|pfc-priority-queue|tc-dot1p|tc-dscp|tc-pg|tc-queue} [qos-map-name]`

**Parameters**  :
- `qos-map-name` - Enter the name of the QoS map to be displayed

**Command mode** : Exec mode

**Usage**       : If qos map name is not specified, all QoS maps of the specified type will be displayed.

**Click command** : None

**Example**
```
sonic# show qos map
  dot1p-tc            Display Dot1p to Traffic Class QoS Maps
  dscp-tc             Display DSCP to Traffic Class QoS Maps
  pfc-priority-queue  Display PFC priority to Queue QoS Maps
  tc-dot1p            Display Traffic Class to Dot1p QoS Maps
  tc-dscp             Display Traffic Class to DSCP QoS Maps
  tc-pg               Display Traffic Class to Priority Group QoS Maps
  tc-queue            Display Traffic Class to Queue QoS Maps

sonic# show qos map dot1p-tc
DOT1P-TC-MAP: dot1p-tc01
---------------------------------------------------------
  DOT1P   |    TC
---------------------------------------------------------
    0     |    7
    1     |    6
    2     |    5
    3     |    4
    4     |    3
    5     |    2
    6     |    1
    7     |    0
---------------------------------------------------------
DOT1P-TC-MAP: dot1p-tc02
---------------------------------------------------------
  DOT1P   |    TC
---------------------------------------------------------
    0     |    0
    1     |    1
    2     |    2
    3     |    3
    4     |    4
    5     |    5
    6     |    6
    7     |    7

```
#### Attach qos map to interface
This command binds a configured QoS map to an interface

**Syntax**: `qos-map {dot1p-tc|dscp-tc|pfc-priority-queue|tc-dot1p|tc-dscp|tc-pg|tc-queue} [<qos-map-name>]`

**Parameters**  :
- `qos-map-name` - Enter the name of the QoS map

**Command mode** : Ethernet interface configuration mode

**Usage**       : Use `no qos-map {dot1p-tc|dscp-tc|pfc-priority-queue|tc-dot1p|tc-dscp|tc-pg|tc-queue}` to unbind a qos map from the interface

**Click command** : None

**Example**
```
sonic(conf-if-Ethernet0)# qos-map dot1p-tc MAP1
sonic(conf-if-Ethernet0)# no qos-map dot1p-tc
```
#### Show QoS Maps attached to interface
Displays the QoS maps bound to interface

**Syntax**: `show qos interface {Ethernet <Ethernet-id>|all}`

**Parameters**  :
- `Ethernet-id` - Enter the id of the Ethernet interface

**Command mode** : Exec mode

**Usage**       : Specify keyword `all` to display QoS maps configured on all interfaces

**Click command** : None

**Example**
```
sonic# show qos interface Ethernet 16
Interface : Ethernet16
  pfc-priority-queue-map : pfc-priority-queue02
  tc-priority-group-map  : tc-pg01
  tc-queue-map           : tc-queue01
  pfc-asymmetric :
  pfc-priority   :
  PFC Watchdog
    Action            :
    Detection Time    :
    Restoration Time  :

sonic# show qos interface Ethernet all
            |          |                                                                |               Priority-Flow-Control
            | Scheduler|                          Interface Maps                        |asym               --------- WATCHDOG ------------
Interface   |    Policy| dot1p-tc  dscp-tc  pfc-p2q tc-dot1p  tc-dscp    tc-pg tc-queue |mode      priority     action    detect    restore
------------+----------+--------- -------- -------- -------- -------- -------- ---------+---- ------------- ---------- --------- ----------
Ethernet0   |          | dot1p-tc dscp-tc0 pfc-prio tc-dot1p tc-dscp0  tc-pg01 tc-queue |
Ethernet12  |          | dot1p-tc                            tc-dscp0                   |
Ethernet16  |          |                   pfc-prio                    tc-pg01 tc-queue |
Ethernet4   |          | dot1p-tc dscp-tc0 pfc-prio tc-dot1p tc-dscp0  tc-pg01 tc-queue |
Ethernet8   |          | dot1p-tc dscp-tc0 pfc-prio tc-dot1p tc-dscp0  tc-pg02 tc-queue |
sonic#
```
### Scheduler configuration
#### Enter scheduler configuration mode
This command enters scheduler configuration mode.

**Syntax**: `qos scheduler-policy <scheduler-policy-name>`

**Parameters**  :
- `scheduler-policy-name` - Enter the name of the scheduler policy

**Command mode** : CONFIG

**Usage**       : Use `no qos scheduler-policy <scheduler-policy-name>` to delete a scheduler policy

**Click command** : None

**Example**
```
sonic(config)# qos scheduler-policy POL1
sonic(config)# no qos scheduler-policy POL1
```
#### Configure scheduler policy per queue
This command enter scheduler configuration mode for queue and configures default parameters. By default, Weighted Round Robin (WRR) with weight 1 is configured on the queue.

**Syntax**: `queue <queue-index>`

**Parameters**  :
- `queue-index` - Enter the queue index

**Command mode** : Scheduler configuration mode

**Usage**       : Use `no queue <queue-index>` to delete queue's scheduler policy

**Click command** : None

**Example**
```
sonic(config-scheduler-POL1)# queue 0
sonic(config-scheduler-POL1)# no queue 0
```
#### Configure scheduler algorithm
This command configures scheduler algorithm and weight for the queue.

**Syntax**: `type {wrr|dwrr|strict}`

**Parameters**  : None

**Command mode** : Scheduler queue configuration mode

**Usage**       : Use `no type` to reset the scheduler algorithm

**Click command** : None

**Example**
```
sonic(config-scheduler-S1-queue-0)# type wrr
sonic(config-scheduler-S1-queue-0)# no type
```
#### Configure weight for queue scheduling
This command configures the weight for the queue.

**Syntax**: `weight <weight>`

**Parameters**  : 
- `weight` - Enter the weight of the queue for WRR and DWRR

**Command mode** : Scheduler queue configuration mode

**Usage**       : Use `no weight` to reset the weight of the queue to 1

**Click command** : None

**Example**
```
sonic(config-scheduler-S1-queue-0)# weight 10
sonic(config-scheduler-S1-queue-0)# no weight
```
#### Attach scheduler policy to interface
This command attaches a configured scheduler policy to the interface.

**Syntax**: `scheduler-policy <scheduler-policy-name>`

**Parameters**  : 
- `scheduler-policy-name` - Name of the configured scheduler policy

**Command mode** : Ethernet Interface configuration mode

**Usage**       : Use `no scheduler-policy` to detach scheduler policy from interface

**Click command** : None

**Example**
```
sonic(conf-if-Ethernet8)# scheduler-policy S1
sonic(conf-if-Ethernet8)# no scheduler-policy
```
#### Show scheduler policy
This command displays the specified scheduler's configuration.

**Syntax**: `show qos scheduler-policy [<scheduler-policy-name>]`

**Parameters**  :
- `scheduler-policy-name` - (Optional) Alphanumeric string including - and _ (Max: 32 characters)

**Command mode** : EXEC mode

**Usage**       : 

**Click command** : None

**Example**
```
sonic# show qos scheduler-policy
Scheduler Policy: test1
  queue: 1
         type   : STRICT
         weight : 10
  queue: 2
         type   : WRR
         weight : 20
  queue: 3
         type   : DWRR
         weight : 30

Scheduler Policy: test2
  queue: 2
         type   : DWRR
         weight : 22

sonic# show qos scheduler-policy test2
Scheduler Policy: test2
  queue: 2
         type   : DWRR
         weight : 22

```

#### Show scheduler policy interface
Display the scheduler's configuration on interface.

**Syntax**: `show qos scheduler-policy interface Ethernet {all | <if-id>}`

**Parameters**  :
- `if-id` - Ethernet interface identifier

**Command mode** : EXEC mode

**Usage**       : 
- If selected `all`, displays the scheduler configuration applied to all interface.

**Click command** : None

**Example**
```
sonic# show qos scheduler-policy interface Ethernet all
Interface : Ethernet0
  Scheduler Policy: test4

Interface : Ethernet1
  Scheduler Policy: test1

Interface : Ethernet12
  Scheduler Policy: test3

sonic# show qos scheduler-policy interface Ethernet 1
Interface : Ethernet1
  Scheduler Policy: test1

```

#### Buffer management

#### enable buffer management
Init the buffer management feature

**Syntax**: `qos buffer-mgmt enable`

**Parameters**  : `none`

**Command mode** : CONFIG

**Usage**:
- Use `no qos buffer-mgmt enable` command to disable qos buffer management.

**Example**
```
 sonic(config)# qos buffer-mgmt enable
 sonic(config)# no qos buffer-mgmt enable

```
#### create buffer profile

**Syntax**: `buffer-profile ingress profile-name <buffer-profile-name> buffer-pool-name <buffer-pool> {dynamic-threshold <threshold-value>|static-threshold<threshold-value>} [xon <xon-value> | headroom <hdrm-value> | size <size>]`

**Parameters**  :
- `buffer-profile-name` - Buffer profile name(max 64 chars).
- `buffer-pool-name` - Valid ingress buffer pool name.
- `threshold-value` - Static or Dynamic threshold.
- `xon-value` - Resume threshold.  
- `hdrm-value ` - Maximum headroom value for this buffer profile that can use from global headroom buffer.  
- `size` - dedicated size. 

**Command mode** : CONFIG

**Usage**       : Use `no  buffer-profile profile-name <buffer-profile-name>  ` to remove buffer profile.

**Example**
```
sonic(config)# buffer-profile ingress profile-name  ingress_lossless_profile  buffer-pool-name ingress_lossy_pool dynamic-threshold 3 headroom 2560 xon 25600
sonic(config)# no qos buffer-profile profile-name  ingress_lossless_profile
```
Configuring  the Egress buffer Profile

**Syntax**: `buffer-profile egress profile-name <buffer-profile-name> buffer-pool-name <buffer-pool> {dynamic-threshold <threshold-value>|static-threshold<threshold-value>} [size <size>]`

**Parameters**  :
- `buffer-profile-name` - Buffer profile name (max 64 chars).
- `buffer-pool-name` - Valid egress buffer pool name.
- `threshold-value` - Static or Dynamic threshold.

**Command mode** : CONFIG

**Usage**       : Use `no  buffer-profile profile-name <buffer-profile-name>  ` to remove buffer profile.

**Example**
```
sonic(config)# buffer-profile egress profile-name  egress_lossless_profile  pool-name egress_lossless_pool static-threshold 25600
 
```

#### Attach buffer profile to priority group

**Syntax**: `[no] buffer-pg-profile name <ingress-buffer-prof-name> priority-group <pg-range>`

**Parameters**  :
- `ingress-buffer-prof-name` - IngressBuffer profile name.
- `pg-range` - prirority group range. 


**Command mode** : Ethernet interface

**Example**
```
sonic(conf-if-Ethernet48)# buffer-pg-profile name  ingress_lossless_profile priority-group 2-5
sonic(conf-if-Ethernet48)# no buffer-pg-profile name ingress_lossless_profile priority-group 2
```

#### Attach buffer profile to queue

**Syntax**: `[no] buffer-queue-profile name  <egress-buffer-prof-name> queue-id <qid-range>`

**Parameters**  :
- `egress-buffer-prof-name` - egressBuffer profile name.
- `qid-range` - qid range. 

**Command mode** : Ethernet interface

**Example**
```
sonic(conf-if-Ethernet48)# buffer-queue-profile name  egress_lossless_profile queue-id 2
sonic(conf-if-Ethernet48)# no buffer-queue-profile name  egress_lossless_profile queue-id 2
```

#### Enable PFC

**Syntax**: `priority-flow-control mode enable <pg-id>`

**Parameters**  :
- `pg-id` - priority-group identification number

**Command mode** : Ethernet interface

**Usage**:
- Use `no priority-flow-control mode enable <pg-id>` command to diable priority flow control for that pg on that interface


**Example**
```
sonic(conf-if-Ethernet48)# priority-flow-control mode enable 3
sonic(conf-if-Ethernet48)# no priority-flow-control mode enable 3
``` 

#### show buffer pool
Display the buffer pool configuration

**Syntax**: `show qos buffer-detail`

**Command mode** : Exec mode

**Usage**       : `Display global buffer pool configuration`

**Example**
```

sonic(config)# do show qos buffer-detail
------------------------------------------------------------------------------------------
BufferName                               Type           Mode            Size
------------------------------------------------------------------------------------------
egress_lossless_pool                   Egress         dynamic        15982720
egress_lossy_pool                      Egress         dynamic         9243812
ingress_lossless_pool                 Ingress         dynamic        21881408
ingress_lossy_pool                    Ingress         dynamic           10000


```

#### show buffer profile

**Syntax**: `show qos buffer-profile`

**Command mode** : Exec mode

**Usage**       : `Display global buffer profile configuration`


**Example**
```
sonic(config)# do show qos buffer-profile
BufferProfile : test
BufferPool    : ingress_lossy_pool
Dynamic Threshold : 3
Pause Threshold : 55120
Resume Threshold : 18432
Size : 56368

```

#### show priority-group

**Syntax**: `show priority-group {drop counters | {watermark | persistent-watermark} {headroom | shared}} [Ethernet <if-id>]`

**Parameters**  :
- `if-id` - Ethernet interface identifier.

**Command mode** : Exec mode

**Usage**       : `If interface id is not given, display information for all interfaces.`

**Click command** :
- `show priority-group {drop counters | {watermark | persistent-watermark} {headroom | shared}}`

**Example**
```
sonic# show priority-group watermark headroom Ethernet 11
Ingress headroom per PG:
      Port     PG0     PG1     PG2     PG3     PG4     PG5     PG6     PG7
----------  ------  ------  ------  ------  ------  ------  ------  ------
Ethernet11       0       0       0       0       0       0       0       0
sonic#
sonic# show priority-group watermark shared Ethernet 11
Ingress shared pool occupancy per PG:
      Port     PG0     PG1     PG2     PG3     PG4     PG5     PG6     PG7
----------  ------  ------  ------  ------  ------  ------  ------  ------
Ethernet11     768     512     256     512     512     512     256     256
sonic#
sonic# show priority-group persistent-watermark headroom Ethernet 11
Ingress headroom per PG:
      Port     PG0     PG1     PG2     PG3     PG4     PG5     PG6     PG7
----------  ------  ------  ------  ------  ------  ------  ------  ------
Ethernet11       0       0       0       0       0       0       0       0
sonic#
sonic# show priority-group persistent-watermark shared Ethernet 11
Ingress shared pool occupancy per PG:
      Port     PG0     PG1     PG2     PG3     PG4     PG5     PG6     PG7
----------  ------  ------  ------  ------  ------  ------  ------  ------
Ethernet11     768     512     256     512     512     512     256     256
sonic#
sonic# show priority-group drop counters Ethernet 11
Ingress PG dropped packets:
      Port     PG0     PG1     PG2     PG3     PG4     PG5     PG6     PG7
----------  ------  ------  ------  ------  ------  ------  ------  ------
Ethernet11       0       0       0       0       0       0       0 2424482

```

#### show interface priority group

**Syntax**: `show qos buffer-interface Ethernet {all|<interface-id>} {priority-group|queue}`

**Parameters**  :
- `interface_id` - Enter the interface number on which buffer profile  settings to be shown.

**Command mode** : Exec mode

**Usage**       : If interface id is not given all interfaces'configured buffer profile will be displayed.

**Example**
```
sonic# show qos buffer-interface Ethernet 48 priority-group
------------------------------------------------------------------------------------------
Interface                      Buffer-Profile                Priority-Group
------------------------------------------------------------------------------------------
Ethernet48                           tst                         4

sonic# show qos buffer-interface Ethernet all priority-group
------------------------------------------------------------------------------------------
Interface                      Buffer-Profile                Priority-Group
------------------------------------------------------------------------------------------
Ethernet48                           tst                         4

```

#### show interface queue profile

**Syntax**: `show qos buffer-interface Ethernet {all|<interface-id>} {priority-group|queue}`

**Parameters**  :
- `interface_id` - Enter the interface number on which buffer profile  settings to be shown.

**Command mode** : Exec mode

**Usage**       : If interface id is not given all interfaces'configured buffer profile will be displayed.

**Example**
```
  
sonic# show qos buffer-interface Ethernet all queue
------------------------------------------------------------------------------------------
Interface                      Buffer-Profile                           Queue-Id
------------------------------------------------------------------------------------------
Ethernet48                    egress_lossless_profile                         4
```

#### show PFC interface status
Displays pfc interface status

**Syntax**: `show qos pfc interface Ethernet {all | <if-id>}`

**Parameters**  : 
- `if-id` - Ethernet interface identifier.

**Command mode** : EXEC

**Usage**       : If interface name is not given all interfaces'pfc status will be displayed.

**Click command** :
- `show pfc priority [<interface_name>]`

**Example**
```
sonic# show qos pfc interface Ethernet 2
Interface    Priority
-----------  ----------------
Ethernet1    2


sonic# show qos pfc interface Ethernet all
Interface    Priority
-----------  ----------------
Ethernet1    1
Ethernet2    2

```

#### Queue

#### show queue counters
Displays packet and byte counters for queues

**Syntax**: `show queue counters [Ethernet <if-id>]`

**Parameters**  : 
- `if-id` - (Optional) Ethernet interface identifier.

**Command mode** : EXEC

**Usage**       : If interface name is not given all interfaces'queue counters will be displayed.

**Click command** :
- `show queue counters [<interface_name>]`

**Example**
```
sonic# show queue counters Ethernet 47
      Port    TxQ    Counter/pkts    Counter/bytes    Drop/pkts    Drop/bytes
----------  -----  --------------  ---------------  -----------  ------------
Ethernet47   UC0             174            43542           0             0
Ethernet47   UC1             100            10000           0             0
Ethernet47   UC2             200            20000           0             0
Ethernet47   UC3             300            30000           0             0
Ethernet47   UC4             400            40000           0             0
Ethernet47   UC5             100            10000           0             0
Ethernet47   UC6             600            60000           0             0
Ethernet47   UC7             700            70000           0             0
Ethernet47   MC8             100            10000           0             0
Ethernet47   MC9             200            20000           0             0
Ethernet47  MC10             300            30000           0             0
Ethernet47  MC11           25529          2552900           0             0
Ethernet47  MC12             400            40000           0             0
Ethernet47  MC13             500            50000           0             0
Ethernet47  MC14             600            60000           0             0
Ethernet47  MC15             700            70000           0             0

sonic# show queue counters
      Port    TxQ    Counter/pkts    Counter/bytes    Drop/pkts    Drop/bytes
----------  -----  --------------  ---------------  -----------  ------------
Ethernet0    UC0             223            55451           0             0
Ethernet0    UC1               0                0           0             0
Ethernet0    UC2               0                0           0             0
Ethernet0    UC3               0                0           0             0
Ethernet0    UC4               0                0           0             0
Ethernet0    UC5               0                0           0             0
Ethernet0    UC6               0                0           0             0
Ethernet0    UC7               0                0           0             0
Ethernet0    MC8               0                0           0             0
Ethernet0    MC9               0                0           0             0
Ethernet0   MC10               0                0           0             0
Ethernet0   MC11               0                0           0             0
Ethernet0   MC12               0                0           0             0
Ethernet0   MC13               0                0           0             0
Ethernet0   MC14               0                0           0             0
Ethernet0   MC15               0                0           0             0

Ethernet1    UC0             223            55451           0             0
Ethernet1    UC1               0                0           0             0
Ethernet1    UC2               0                0           0             0
Ethernet1    UC3               0                0           0             0
Ethernet1    UC4               0                0           0             0
Ethernet1    UC5               0                0           0             0
Ethernet1    UC6               0                0           0             0
Ethernet1    UC7               0                0           0             0
Ethernet1    MC8               0                0           0             0
Ethernet1    MC9               0                0           0             0
Ethernet1   MC10               0                0           0             0
Ethernet1   MC11               0                0           0             0
Ethernet1   MC12               0                0           0             0
Ethernet1   MC13               0                0           0             0
Ethernet1   MC14               0                0           0             0
Ethernet1   MC15               0                0           0             0
...

```

#### show queue watermark
Displays queue watermark

**Syntax**: `show queue {watermark | persistent-watermark} {all | unicast | multicast} [Ethernet <if-id>]`

**Parameters**  : 
- `if-id` - (Optional) Ethernet interface identifier.

**Command mode** : EXEC

**Usage**       : 
- If selected `persistent-watermark`, displays the watermark from switch boot or last clear of persistent watermark
- If selected `all`, displays both unicast and multicast queue watermarks.
- If interface name is not given all interfaces'queue watermarks will be displayed.

**Click command** :
- `show queue {watermark | persistent-watermark} {all | unicast | multicast}`

**Example**
```
sonic# show queue watermark unicast Ethernet 10
Egress queue watermark per unicast queue:
      Port      UC0      UC1      UC2      UC3      UC4      UC5      UC6      UC7
---------- -------- -------- -------- -------- -------- -------- -------- --------
Ethernet10      512        0        0        0        0        0        0        0

sonic# show queue watermark multicast Ethernet 10
Egress queue watermark per multicast queue:
      Port      MC8      MC9     MC10     MC11     MC12     MC13     MC14     MC15
---------- -------- -------- -------- -------- -------- -------- -------- --------
Ethernet10      256        0        0        0        0        0        0        0

sonic# show queue watermark all Ethernet 10
Egress queue watermark per all queue:
      Port      UC0      UC1      UC2      UC3      UC4      UC5      UC6      UC7      MC8      MC9     MC10     MC11     MC12     MC13     MC14     MC15
---------- -------- -------- -------- -------- -------- -------- -------- -------- -------- -------- -------- -------- -------- -------- -------- --------
Ethernet10      512        0        0        0        0        0        0        0      256        0        0        0        0        0        0        0



sonic# show queue watermark all
Egress queue watermark per all queue:
      Port      UC0      UC1      UC2      UC3      UC4      UC5      UC6      UC7      MC8      MC9     MC10     MC11     MC12     MC13     MC14     MC15
---------- -------- -------- -------- -------- -------- -------- -------- -------- -------- -------- -------- -------- -------- -------- -------- --------
Ethernet0         0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet1         0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet2         0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet3         0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet4         0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet5         0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet6         0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet7         0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet8         0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet9         0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet10      512        0        0        0        0        0        0        0      256        0        0        0        0        0        0        0
Ethernet11      512        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet12      512        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet13      512        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet14      512        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet15      512        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet16        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet17        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet18        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet19        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet20        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet21        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet22        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet23        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet24        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet25        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet26        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet27        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet28        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet29        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet30        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet31        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet32        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet33        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet34        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet35        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet36        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet37        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet38        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet39        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet40        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet41        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet42        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet43        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet44        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet45        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet46        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet47        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet48        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet49        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet50        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet51        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet52        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet53        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet54        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
Ethernet55        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0        0
```

## Telemetry
### Telemetry mode
Enter into telemetry config mode to access telemetry related configurations.

**syntax** : `telemetry`

**Parametes** : None

**Command mode** : CONFIG

**Usage** : None

**Supported Releases** : 1.1.0 or later

**Click command** : None

**Example**:
```
sonic(config)# telemetry
sonic(conf-telemetry)#
```

### Server port

**Syntax** : `server port <value>`

**Parameters** :
  - `value` : Server port number.

**Commmand mode** : Telemetry config mode

**Usage** :
- GNMI server runs on 8080 port by default
 - Telemetry service will be restarted to apply the confiuration; wait for telemetry container to be up prior applying subsequent configuration
- Use `no server port` for the default port number to be applied.

**Supported Releases** : 1.1.0 or later

**Click command** : None

**Example**:
```
sonic(conf-telemetry)# server port 9090
sonic(conf-telemetry)# no server port
sonic(conf-telemetry)#
```

### Server certificate
Configure absolute path of server certificate and key files.

**Syntax** : `server certificate file <cert-path> <key-path>`

**Parameters** :
 - `cert-file` - Specify the absolute path of server certificate file.
 - `key-file` - Specify the absolute path of key file.

**Commmand mode** : Telemetry config mode

**Usage** :
 - Trannsfer or copy the certificate and key files into telemtry container prior executing this command
 - Telemetry service will be restarted to apply the confiuration; wait for telemetry container to be up prior applying subsequent configuration
 - Use `no server certificate` to remove server certificate cofiguration.

**Supported Releases** : 1.1.0 or later

**Click command** : none

**Example**:
```
sonic(conf-telemetry)# server certificate file /etc/certs/server.cer /etc/certs/server.key
sonic(conf-telemetry)# no server certificate
sonic(conf-telemetry)#
```

### Authentication type
Configure the server side authentication type of to be used.

**syntax** : `authentication {password | jwt | certificate}`

**Parameters** : None

**Commmand mode** : Telemetry config mode

**Usage** :
 - Telemetry service will be restarted to apply the confiuration; wait for telemetry container to be up prior applying subsequent configuration
 - Multiple authentication modes are allowed to be configured
 - Use `no authentication [password | jwt | certificate]` to remove specific authentication mode or all modes

**Supported Releases** : 1.1.0 or later

**Click command** : None

**Example**:
```
sonic(conf-telemetry)# authentication password
sonic(conf-telemetry)# authentication jwt
sonic(conf-telemetry)# authentication certificate
sonic(conf-telemetry)# no authentication jwt
sonic(conf-telemetry)# no authentication
sonic(conf-telemetry)#
```

### CA certificate
Configure absolute path of CA certificate file for the certificate authentication mode.

**syntax** : `ca-certificate file <path>`

**Parameteris** :
 - `path` - Specify the absolute path of certificate file location in the telemetry container.

**Commmand mode** : Telemetry config mode

**Usage** :
 - Trannsfer or copy the certificate file into telemtry container prior executing this command
 - Telemetry service will be restarted to apply the confiuration; wait for telemetry container to be up prior applying subsequent configuration
 - Use `no ca-certificate` to remove client certificate cofiguration.

**Supported Releases** : 1.1.0 or later

**Click command** : None

**Example**:
```
sonic(conf-telemetry)# ca-certificate file /etc/certs/ca-certificate.cer
sonic(conf-telemetry)# no ca-certificate
sonic(conf-telemetry)#
```

### Retry interval
Configure retry interval in seconds.

**Syntax** : `retry-interval <value>`

**Parameters** :
 - `value` - Specify the retry interval value.

**Commmand mode** : Telemetry config mode

**Usage** : Use `no retry-interval` to remove the configuration.

**Supported Releases** : 1.1.0 or later

**Click command** : None

**Example**:
```
sonic (conf-telemetry)#retry-interval
  <0..65535>  Value in seconds
sonic (conf-telemetry)#no retry-interval
```

### Destination group
Configures telemetry destination group and enters into destination group config mode

**Syntax** : `destination-group <name>`

**Parameters** :
 - `name` - Specify the destination group name

**Commmand mode** : Telemetry config mode

**Usage** : Use `no destination group <name>` to remove the destination group.

**Supported Releases** : 1.1.0 or later

**Click command** : None

**Example**:
```
sonic(conf-telemetry)# destination-group test
sonic(conf-telemetry-dst-group-test)# exit
sonic(conf-telemetry)# no destination-group test
sonic(conf-telemetry)#
```

#### Destination address
Create or delete destination address and port number for the destination group.

**Syntax** : `destination <ip_address> <port_num>`

**Parameters** :
 - `ip_address` - IPv4 address.
 - `port_num`  - Port number.

**Commmand mode** : Telemetry destination group config mode

**Usage** :
- Use `no destination` to remove the destination configuration.

**Supported Releases** : 1.1.0 or later

**Click command** : None

**Example**:
```
sonic(conf-telemetry-dst-group-test)# destination 1.1.1.1 1
sonic(conf-telemetry-dst-group-test)# destination 2.2.2.2 2
sonic(conf-telemetry-dst-group-test)# no destination 2.2.2.2 2
sonic(conf-telemetry-dst-group-test)# no destination 1.1.1.1 1
sonic(conf-telemetry-dst-group-test)#
```

### Subscription group
Configure subscription group and enters into subscription group config mode.

**Syntax** : `subscription-group <name>`

**Parameters** :
 - `name` - Specify subscription group name

**Commmand mode** : Telemetry config mode

**Usage** : Use `no subscription-group <name>` to remove the subscription group.

**Supported Releases** : 1.1.0 or later

**Click command** : None

**Example**:
```
sonic(conf-telemetry)# subscription-group HS_RDMA
sonic(conf-telemetry-sub-group-HS_RDMA)# exit
sonic(conf-telemetry)# no subscription-group HS_RDMA
sonic(conf-telemetry)#
```

#### Target DB
Configure the target DB from which the data path to be fetched.

**Syntax** : `target <target-val>`

**Parameters** :
 - `target-val` -Specify target DB name

**Commmand mode** : Subscription group config mode

**Usage** :

**Supported Releases** : 1.1.0 or later

**Click command** : none

**Example**:
```
sonic(conf-telemetry-sub-group-test)# target CONFIG_DB
sonic(conf-telemetry-sub-group-test)# target COUNTERS_DB
sonic(conf-telemetry-sub-group-test)# target STATE_DB
sonic(conf-telemetry-sub-group-test)#
```

#### Collection paths
Configure data path to fetch information.

**Syntax** : `path <path-val>`

**Parameters** :
 - `path-val` - Specify the data path

**Commmand mode** : Subscription group config mode

**Usage** : Use `no path [<path-val>]` to remove the configuration

**Supported Releases** : 1.1.0 or later

**Click command** : None

**Example**:
```
sonic(conf-telemetry-sub-group-test)# path COUNTERS/Ethernet0
sonic(conf-telemetry-sub-group-test)# path COUNTERS_PORT_NAME_MAP
sonic(conf-telemetry-sub-group-test)#
```

#### Report type
Configure reporting type of telemetry data.

**Syntax** : `type {periodic | stream}`

**Parameters** : None

**Commmand mode** : Subscription group config mode

**Usage** : None

**Supported Releases** : 1.1.0 or later

**Click command** : None

**Example**:
```
sonic(conf-telemetry-sub-group-test)# type periodic
sonic(conf-telemetry-sub-group-test)# type stream
sonic(conf-telemetry-sub-group-test)#
```

#### Report interval
Configure report interval value in milliseconds.

**Syntax** : `report-interval <value>`

**Parameters** :
 - `value` - Specify the value in millisecondsi, default is 5000.

**Commmand mode** : Telemetry subscription group config mode

**Usage** : Use `no report-interval` removes the configured value, sets the default value.

**Supported Releases** : 1.1.0 or later

**Click command** : None

**Example**:
```
sonic(conf-telemetry-sub-group-test)# report-interval 2000
sonic(conf-telemetry-sub-group-test)# no report-interval
sonic(conf-telemetry-sub-group-test)#
```

#### Associate destination group
Configure the destinaiton group name to be used by the subscription group

**Syntax** : `destination-group <name>`

**Parameters** :
 - `name` - Destination group name.

**Commmand mode** : Subscription group config mode

**Usage** : Use `no destination-group`  to remove the configuration.

**Supported Releases** : 1.1.0 or later

**Click command** : None

**Example**:
```
sonic(conf-telemetry-sub-group-test)# destination-group d1
sonic(conf-telemetry-sub-group-test)# no destination-group
sonic(conf-telemetry-sub-group-test)#
```

### Show telemetry server
Displays the telemetry global configuration.

**Syntax** : `show telemetry server`

**Parameters** : None

**Commmand mode** : Exec mode

**Usage** : None

**Supported Releases** : 1.1.0 or later

**Click command** : None

**Example**:
```
sonic# show telemetry server
Server port : 9098
Server certificate file : /etc/certs/server.cer
Server key file : /etc/certs/server.key
CA certificate file : /etc/certs/client.cer
Authentication modes : certificate,jwt,password
Retry interval : 20
sonic#
```

### Show destination-group
Display destionation group information.

**Syntax** : `show telemetry destination-group [<name>]`

**Parameters** :
 - `name` - Destination group name

**Commmand mode** : Exec mode

**Usage** : All groups details will be displayed, if the group name is not entered.

**Supported Releases** : 1.1.0 or later

**Click command** : None

**Example**:
```
sonic# show telemetry destination-group
------------------------------------------------------------
Destination Group    Destination address  Destination port
------------------------------------------------------------
d1                   1.1.1.1              1
                     1.1.1.1              2
                     1.1.1.1              3
                     1.1.1.1              4
d2                   2.2.2.2              1
                     2.2.2.2              2
                     2.2.2.2              3
d3                   NA                   NA
sonic# show telemetry destination-group d1
------------------------------------------------------------
Destination Group    Destination address  Destination port
------------------------------------------------------------
d1                   1.1.1.1              1
                     1.1.1.1              2
                     1.1.1.1              3
                     1.1.1.1              4
sonic# 
```

### Show subscription-group
Displays subscription group information.

**Syntax** : `show telemetry subscription-group [<name>]`

**Parameters** :
 - `name` - Subscription group name

**Commmand mode** : Exec mode

**Usage** : All groups details will be displayed, if the group name is not entered.

**Supported Releases** : 1.1.0 or later

**Click command** : None

**Example**:
```
sonic# show telemetry subscription-group
------------------------------------------------------------------------------------------
Subscription Group   Destination Group    Type       Interval   Target          Path(s)
------------------------------------------------------------------------------------------
s1                   d1                   periodic   10         CONFIG_DB       PORT
                                                                                VLAN
                                                                                PORTCHANNEL
                                                                                PORTCHANNEL
s2                   d2                   stream     30         COUNTERS_DB     PORT/Ethernet0
                                                                                VLAN/Vlan10
                                                                                PORTCHANNEL/PortChannel20
                                                                                PORTCHANNEL/PortChannel20
s3                   d3                   NA         NA         NA              NA
sonic# show telemetry subscription-group s1
------------------------------------------------------------------------------------------
Subscription Group   Destination Group    Type       Interval   Target          Path(s)
------------------------------------------------------------------------------------------
s1                   d1                   periodic   10         CONFIG_DB       PORT
                                                                                VLAN
                                                                                PORTCHANNEL
                                                                                PORTCHANNEL
sonic# 
```

## VxLAN
### VxLAN Config commands
#### VxLAN global config commands
##### Vxlan-profile enable
Configure to load VxLAN specific broadcom config variables and init the broadcom NPU based on the variables present in *-vxlan.config.bcm file. Its applicable only for broadcom chipset based platforms. In Vxlan enabled platforms *-vxlan.config.bcm file is loaded by default even if the config is not present. This configuration takes effect only after save and reboot.

**Syntax** : `vxlan-profile enable`

**Parameters** : None

**Command mode** : CONFIG

**Usage**       : Use `no vxlan-profile enable` to load generic *.config.bcm file which gives max vlan scale.

**Supported Releases** :  1.1.0 or later

**Click command** : `config vxlan_profile enable`

**Example**
```
sonic(config)# vxlan-profile enable
```

##### Vxlan interface create and delete
Create a new vxlan interface(if not present) which acts as a virtual tunnel end point(VTEP). Enters into "config-if-vxlan-<vtepname>" mode. Only one VTEP can exist in a switch.

**Syntax** :
`interface vxlan <vtep-name>`

**Parameters** :
- `vtep-name` - Name of the vxlan interface/VTEP (Max 10 chars, prefixed by 'vtep')

**Command mode** : CONFIG

**Usage**       : Use `no vxlan interface <vtep-name>` to remove the VTEP.

**Supported Releases** :  1.1.0 or later

**Click commands** : `config vxlan add/del <vtep-name> <src-ip>`

**Example**
```
sonic(config)# interface vxlan vtep1
sonic(config-if-vxlan-vtep1)#

sonic(config)# no interface vxlan vtep1
```

#### VxLAN interface level config commands
##### Source-vtep-ip
Add or delete source VTEP's IPv4 address which is used to form the tunnel between peer VTEP. The VTEP's source address should be assigned to a loopback interface with /32 mask. EVPN nvo config entry will be added/deleted internally, if the source-ip config addition/deletion is success.

**Syntax** : `source-ip <vtep-sip>`

**Parameters** :
 - `vtep-sip` - source ip for the VTEP in (A.B.C.D) format

**Command mode** : VTEP mode

**Usage**       : Use `no source-ip` to delete the configured source-ip

**Supported Releases** :  1.1.0 or later

**Click command** : config vxlan add/del <vtep-name> <src-ip>

**Example**

```
sonic(config-if-vxlan-vtep1)# source-ip 1.1.1.1
sonic(config-if-vxlan-vtep1)# no source-ip

```

##### Map-vni-vlan
Add or delete vlan vni one-to-one mappings to/from a VTEP. It will throw error if the given vlan interface doesn't exist. Map count can also be given along with this command to configure more than vlan-vni mappings. If the count range is exceeded than 4095, it will throw error.

**Syntax** : `map vni <1..16777215> vlan <1..4094> [count <1..4094>]`

**Parameters** :
 - `1..16777215` - VNI range
 - `1..4094` - vlan id range
 - `1..4094` - map count range and it should not exceed 4094

**Command mode** : VTEP mode

**Usage**       : Use `no map vni <1..16777215> vlan <1..4094> count <1..4094>` to unconfigure the vlan-vni maps fully or partially. It should throw error if the given parameters are invalid

**Supported Releases** :  1.1.0 or later

**Click command** : config vxlan map add <vxlan_name> <vlan_id> <vni>
                    config vxlan map_range <vxlan_name> <vlan_start> <vlan_end> <vni_start>

**Example**

```
sonic(config-if-vxlan-vtep1)# map vni 100010 vlan 10 count 3
sonic(config-if-vxlan-vtep1)# map vni 100015 vlan 15
sonic(config-if-vxlan-vtep1)# no map vni 100010 vlan 10
sonic(config-if-vxlan-vtep1)# no map vni 100011 vlan 11 count 2

```

#### BGP config commands
##### BGP router config
Create a BGP router instance (if not present) in switch. Enters into BGP router "config-router" mode.

**Syntax** :
`router bgp <asn> [vrf <vrf-name>]`

**Parameters** :
- `asn` - An identifier for the autonomous system. The BGP protocol uses the AS number for detecting whether the BGP connection is internal or external.
- `vrf-name` -  The name of the VRF instance is matched against VRFs configured in the kernel(Max 15 chars, prefixed by 'Vrf'). When vrf VRFNAME is not specified, the BGP protocol process belongs to the default VRF. Configuration of additional autonomous systems is possible through VRF instance.

**Command mode** : CONFIG

**Usage** : Use `no router bgp <asn> [vrf <vrf-name>]` to remove the BGP router instance(s).

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
sonic(config)# router bgp 65100
sonic(config-router)#
sonic(config)# no router bgp 65100

sonic(config)# router bgp 65200 vrf Vrf01
sonic(config-router)#
sonic(config)# no router bgp 65200 vrf Vrf01
```

###### Router id
Add or delete router ID to the BGP router instance manually. Mostly loopback interface's IP address is configured as router-id. If the router ID is not set manually, bgpd connects to zebra it gets interface and address information. In that case default router ID value is selected as the largest IP Address of the interfaces.

**Syntax** :
`bgp router-id <router-ip>]`

**Parameters** :
- `router-ip` - An IPv4 address(A.B.C.D) of the BGP router instance.

**Command mode** : Router BGP mode

**Usage** : Use `no bgp router-id <router-ip>` to remove the router ID of BGP router instance.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
sonic(config)# router bgp 65100
sonic(config-router)# bgp router-id 3.3.3.3

sonic(config-router)# no bgp router-id 3.3.3.3
```

###### Log neighbor changes
Log neighbor up/down and reset reason

**Syntax** :
`bgp log-neighbor-changes`

**Command mode** : Router BGP mode

**Usage** : Use `no bgp log-neighbor-changes` to disable neighbor up/down, reset reason logging.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
sonic(config)# router bgp 65100
sonic(config-router)# bgp log-neighbor-changes

sonic(config-router)# no bgp log-neighbor-changes
```

###### Ebgp requires policy
This command requires incoming and outgoing filters to be applied for eBGP sessions as part of RFC-8212 compliance. Without the incoming filter, no routes will be accepted. Without the outgoing filter, no routes will be announced.

**Syntax** :
`bgp ebgp-requires-policy`

**Command mode** : Router BGP mode

**Usage** : Use `no bgp ebgp-requires-policy` to accept all incoming routes and all routes will be announced.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
sonic(config)# router bgp 65100
sonic(config-router)# bgp ebgp-requires-policy

sonic(config-router)# no bgp ebgp-requires-policy
```

###### BGP as-path

Configure graceful restart commands.

**Syntax** :
`bgp as-path access-list <alist_name> permit|deny <AS_path_regex>`

**Parameters** :
- `alist_name` - Access list name.
- `AS_path_regex` - BGP AS Path regular-expression.

**Command mode** : configure-router-bgp-view

**Usage** : Use no bgp as-path access-list <alist_name> permit|deny <AS_path_regex> to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

###### Always-compare-med

Uses MED to compare for routers even when received across ASes

**Syntax** :
`bgp always-compare-med`

**Parameters** : None

**Command mode** : configure-router-bgp-view

**Usage** : Use no bgp always-compare-med to remove the configuration .

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS2000(config)# router bgp 65100
Celestica-DS2000(config-router)# bgp always-compare-med

Celestica-DS2000(config-router)# no bgp always-compare-med
```

###### Bestpath as-path confed
Matches lenght of confederation path set and sequence.

**Syntax** :
`bgp bestpath as-path confed`

**Parameters** : None

**Command mode** : configure-router-bgp-view

**Usage** : Use no bgp bestpath as-path confed to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS2000(config)# router bgp 65100
Celestica-DS2000(config-router)# bgp bestpath as-path confed

Celestica-DS2000(config-router)# no BGP bestpath as-path confed
```

###### Bestpath as-path multipath-relax
This command specifies that BGP decision process should consider paths of equal AS_PATH length candidates for multipath computation during route selection to allow load sharing. Without the knob, the entire AS_PATH must match for multipath computation.

**Syntax** :
`bgp bestpath as-path multipath-relax`

**Command mode** : Router BGP mode

**Usage** : Use `no bgp bestpath as-path multipath-relax` to disable load-sharing across across routes that have different AS paths(but same length).

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
sonic(config)# router bgp 65100
sonic(config-router)# bgp bestpath as-path multipath-relax

sonic(config-router)# no bgp bestpath as-path multipath-relax
```
##### Bestpath bandwidth
Links the bandwidth attribute

**Syntax** :
`bgp bestpath bandwidth default-weight-for-missing | ignore | skip-missing`

**Parameters** : None

**Command mode** : configure-router-bgp-view

**Usage** : Use no bgp bestpath bandwidth default-weight-for-missing | ignore | skip-missing to remove the configuration

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# bgp bestpath bandwidth default-weight-for-missing
Celestica-DS3000(config-router)# no bgp bestpath bandwidth default-weight-for-missing
```

###### Bestpath compare-routerid
Allows Uses router ID as tie-breaker for bestpath selection.

**Syntax** :
`bgp bestpath compare-routerid`

**Parameters** : None

**Command mode** : configure-router-bgp-view

**Usage** : Use no bgp bestpath compare-routerid to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS2000(config-router)# router bgp 65100
Celestica-DS2000(config-router)# bgp bestpath compare-routerid

Celestica-DS2000(config-router)# no bgp bestpath compare-routerid

```

###### Bestpath med
Configures the med attribute.

**Syntax** :
`bgp bestpath med confed [missing-as-worst]`

**Parameters** : None

**Command mode** : configure-router-bgp-view

**Usage** : Use no bgp bestpath med confed [missing-as-worst] to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS2000(config-router)# router bgp 65100
Celestica-DS2000(config-router)# bgp bestpath med confed missing-as-worst

Celestica-DS2000(config-router)# no bgp bestpath med confed missing-as-worst

```

###### Bestpath peer-type multipath-relax
Uses router ID as tie-breaker for bestpath selection.

**Syntax** :
`bgp bestpath peer-type multipath-relax`

**Parameters** : None

**Command mode** : configure-router-bgp-view

**Usage** : Use no bgp bestpath peer-type multipath-relax to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS2000(config)# router bgp 65100
Celestica-DS2000(config-router)# bgp bestpath peer-type multipath-relax

Celestica-DS2000(config-router)# no bgp bestpath peer-type multipath-relax

```

###### bgp community-list

Configure community list.

**Syntax** :
`bgp community-list <clst_sno>|<clst_exno>|{expanded|standard <clst_name>} {seq <seq_no> deny|permit <com_no>}|{deny|permit <com_no>}`

**Parameters** :
- `clst_sno` - Community list number (standard).
- `clst_exno` - Community list number (expanded).
- `clst_name` - Community list name.
- `seq_no` - Sequence number.
- `com_no` – Community number in AA:NN format (where AA and NN are (0-65535)) or local-AS|no-advertise|no-export|internet or additive (comma separated Community list)

**Command mode** : configure-router-bgp-view

**Usage** : Use no bgp community-list <clst_sno>|<clst_exno>|{expanded|standard <clst_name>} {seq<seq_no> deny|permit <com_no>}|{deny|permit <com_no>} to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

###### bgp extcommunity-list

Configures extended community list.

**Syntax** :
`bgp extcommunity-list <clst_sno>|<clst_exno>|{expanded|standard <clst_name>} {seq <seq_no> deny|permit <com_no>}|{deny|permit <com_no>}`

**Parameters** :
- `clst_sno` - Extended Community list number (standard).
- `clst_exno` - Extended Community list number (expanded).
- `clst_name` - Extended Community list name.
- `seq_no` - Sequence number.
- `com_no` – Extended Community number in rt:aa:nn_or_IPaddr:nn or soo:aa:nn_or_IPaddr:nn format.

**Command mode** : configure-router-bgp-view

**Usage** : Use no bgp extcommunity-list <clst_sno>|<clst_exno>|{expanded|standard <clst_name>} {seq<seq_no> deny|permit <com_no>}|{deny|permit <com_no>} to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

###### bgp large-community-list

Configures large community list.

**Syntax** :
`bgp large-community-list <clst_sno>|<clst_exno>|{expanded|standard <clst_name>}{seq <seq_no> deny|permit <AA:BB:CC>}|{deny|permit <AA:BB:CC>}`

**Parameters** :
- `clst_sno` - Extended Community list number (standard).
- `clst_exno` - Extended Community list number (expanded).
- `clst_name` - Extended Community list name.
- `seq_no` - Sequence number.
- `AA:BB:CC` –  Large community attribute in comma separated list.

**Command mode** : configure-router-bgp-view

**Usage** : Use no bgp large-community-list <clst_sno>|<clst_exno>|{expanded|standard <clst_name>}{seq <seq_no> deny|permit <AA:BB:CC>}|{deny|permit <AA:BB:CC>} to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

###### bgp client-to-client reflection
Configures client to client route reflection.

**Syntax** :
`bgp client-to-client reflection`

**Parameters** : None

**Command mode** : configure-router-bgp-view

**Usage** : Use no bgp client-to-client reflection to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS2000(config)# router bgp 65100
Celestica-DS2000(config-router)# bgp client-to-client reflection

Celestica-DS2000(config-router)# no bgp client-to-client reflection

```

######  bgp cluster-id
Configures Route-Reflector Cluster ID.

**Syntax** :
`bgp cluster-id <cluster_id> | <A.B.C.D>`

**Parameters** :
- `cluster_id` - Cluster-id as 32 bit qunatity.
- `A.B.C.D` - Cluster-id in IP address format.

**Command mode** : configure-router-bgp-view

**Usage** : Use no bgp cluster_id <cluster_id | A.B.C.D> to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS2000(config)# router bgp 65100
Celestica-DS2000(config-router)# bgp cluster-id 1.1.1.2

Celestica-DS2000(config-router)# no bgp cluster-id 1.1.1.2

```

###### bgp confederation
Configures AS confederation parameters.

**Syntax** :
`bgp confederation {identifier <conf_ASN> | peers <peer_ASN>}`

**Parameters** :
- `conf_ASN` - Routing domain confederation AS..
- `peer_ASN` - Peer AS’s number in BGP confederation.

**Command mode** : configure-router-bgp-view

**Usage** : Use no bgp confederation {identifier <conf_ASN> | peers <peer_ASN>} to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS2000(config)# router bgp 65100
Celestica-DS3000(config-router)# bgp confederation identifier 65100
Celestica-DS3000(config-router)# no bgp confederation identifier 65100
```
###### bgp dampening
Enables route-flap dampening.

**Syntax** :
`bgp dampening [<HL_time> <reuse_val> <suppress_val> <max_val>]`

**Parameters** :
- `HL_time` - Routing domain confederation AS..
- `reuse_val` - Peer AS’s number in BGP confederation.
- `suppress_val` - Value to start suppressing a route
- `max_val` - Maximum duration to suppress a stable route.

**Command mode** :
- configure-router-bgp-view
- configure-router-bgp-af4-view
- configure-router-bgp-af6-view

**Usage** : Use no bgp dampening [<HL_time> <reuse_val> <suppress_val> <max_val>] to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config-router)# bgp dampening 10 5 100 1
Celestica-DS3000(config-router)# no bgp dampening 10 5 100 1
```

###### BGP default
BGP default setting for its config parameters.

**Syntax** :
`bgp default {ipv4-unicast | local_preference <value> | show-hostname | show-nexthop-hostname | shutdown`

**Parameters** : `value` - Local preference value.

**Command mode** : configure-router-bgp-view

**Usage** : Use no bgp default {ipv4-unicast | local_preference <value> | show-hostname | show-nexthop-hostname | shutdown} to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65300
Celestica-DS3000(config-router)# bgp default ipv4-unicast
Celestica-DS3000(config-router)# no bgp default ipv4-unicast
Celestica-DS3000(config-router)# bgp default local-preference 100
Celestica-DS3000(config-router)# no bgp default local-preference
Celestica-DS3000(config-router)# no bgp default local-preference 100
Celestica-DS3000(config-router)# bgp default show-hostname
Celestica-DS3000(config-router)# no bgp default show-hostname
Celestica-DS3000(config-router)# bgp default show-nexthop-hostname
Celestica-DS3000(config-router)# no bgp default show-nexthop-hostname
Celestica-DS3000(config-router)# bgp default shutdown
Celestica-DS3000(config-router)# no bgp shutdown
```

###### BGP  deterministic-med
Deterministic Route selection with MED.

**Syntax** :
`bgp deterministic-med`

**Parameters** : None

**Command mode** : configure-router-bgp-view

**Usage** : Use no bgp deterministic-med to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS2000(config)# router bgp 65100
Celestica-DS2000(config-router)# bgp deterministic-med
Celestica-DS2000(config-router)# no bgp deterministic-med

```
###### BGP disable-ebgp-connected-route-check
Disables connection verification process for EBGP peers.

**Syntax** :
`bgp disable-ebgp-connected-route-check`

**Parameters** : None

**Command mode** : configure-router-bgp-view

**Usage** : Use no bgp disable-ebgp-connected-route-check to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS2000(config)# router bgp 65100
Celestica-DS2000(config-router)# bgp disable-ebgp-connected-route-check
Celestica-DS2000(config-router)# no bgp disable-ebgp-connected-route-check

```

###### BGP fast-external-failover
Resets session immediately if a link to a directly connected external peer goes down.

**Syntax** :
`bgp fast-external-failover`

**Parameters** : None

**Command mode** : configure-router-bgp-view

**Usage** : Use no bgp fast-external-failover to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS2000(config)# router bgp 65100
Celestica-DS2000(config-router)# bgp fast-external-failover
Celestica-DS2000(config-router)# no bgp fast-external-failover

```

###### BGP graceful-restart
Configures graceful restart commands.

**Syntax** :
`bgp graceful-restart [disable-eor | preserve-fw-state | restart-time <rt_val> | rib-stale-time <rst_val> | select-defer-time <sdt_val> | stalepath-time <st_val>]`

**Parameters** :
- `rt_val` - Restart time(0-4095).
- `rst_val` - Rib stale time(1-3600).
- `sdt_val` - Select defer time(0-3600).
- `st_val` - Stalepath(1-4095).

**Command mode** : configure-router-bgp-view

**Usage** : Use no bgp graceful-restart [disable-eor | preserve-fw-state | restart-time <rt_val> | rib-stale-time <rst_val> | select-defer-time <sdt_val> | stalepath-time <st_val>] to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS2000(config)# router bgp 65100
Celestica-DS3000(config-router)# bgp graceful-restart disable-eor
Celestica-DS3000(config-router)# no bgp graceful-restart disable-eor
Celestica-DS3000(config-router)# bgp graceful-restart preserve-fw-state
Celestica-DS3000(config-router)# no bgp graceful-restart preserve-fw-state
Celestica-DS3000(config-router)# bgp graceful-restart restart-time 1300
Celestica-DS3000(config-router)# no bgp graceful-restart restart-time 1300
Celestica-DS3000(config-router)# bgp graceful-restart rib-stale-time 1300
Celestica-DS3000(config-router)# no bgp graceful-restart rib-stale-time 1300
Celestica-DS3000(config-router)# bgp graceful-restart select-defer-time 2000
Celestica-DS3000(config-router)# no bgp graceful-restart select-defer-time 2000
Celestica-DS3000(config-router)# bgp graceful-restart stalepath-time 2500
Celestica-DS3000(config-router)# no bgp graceful-restart stalepath-time 2500
```

###### BGP graceful-restart-disable
Undo Global Graceful Restart.

**Syntax** :
`bgp graceful-restart-disable`

**Parameters** : None

**Command mode** : configure-router-bgp-view

**Usage** : Use no bgp graceful-restart-disable to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None


**Example**
```
Celestica-DS2000(config)# router bgp 65100
Celestica-DS2000(config-router)# bgp fast-external-failover
Celestica-DS2000(config-router)# no bgp fast-external-failover
```

###### BGP graceful-shutdown
Configures graceful shutdown as peR RFC 8326.

**Syntax** :
`bgp graceful-shutdown`

**Parameters** : None

**Command mode** : configure-router-bgp-view

**Usage** : Use no bgp graceful-shutdown to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None


**Example**
```
Celestica-DS2000(config)# router bgp 65100
Celestica-DS3000(config-router)# bgp graceful-shutdown
Celestica-DS3000(config-router)# no bgp graceful-shutdown
```

###### BGP listen
Configures graceful restart commands.

**Syntax** :
`bgp listen {limit <limit_val> | {range <ipv4_neigh_addr> |  ipv6_neigh_addr> peer-group <pg_name>}}`

**Parameters** :
- `limit_val` - Limit value of Dynamic Neighbors listen.
- `ipv4_neigh_addr` - IPV4 Neighbor address range.
- `ipv6_neigh_addr` - IPV6 Neighbor address range.
- `pg_name` - Peer group name.

**Command mode** : configure-router-bgp-view

**Usage** : Use no bgp listen {limit <limit_val> | {range <ipv4_neigh_addr> | ipv6_neigh_addr> peer-group <pg_name>}} to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config-router)# router bgp 65100
Celestica-DS3000(config-router)# bgp listen limit 100
Celestica-DS3000(config-router)# no bgp listen limit 100
```
###### BGP max-med
Logs neighbor up/down and reset reason.

**Syntax** :
`bgp max-med administrative|on-startup [<med_val>]`

**Parameters** :
- `med_val` - Maximum MED value to be used.

**Command mode** : configure-router-bgp-view

**Usage** : Use no bgp max-med administrative|on-startup [<med_val>] to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# bgp max-med administrative 1000
Celestica-DS3000(config-router)# no bgp max-med administrative 1000
Celestica-DS3000(config-router)#  bgp max-med on-startup 1000
Celestica-DS3000(config-router)# no bgp max-med on-startup 1000
```

###### BGP network
Configures network must exist in RIB.

**Syntax** :
`bgp network import-check`

**Parameters** : None

**Command mode** : configure-router-bgp-view

**Usage** : Use no bgp network import-check to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# bgp network import-check
Celestica-DS3000(config-router)# no bgp network import-check
```

###### BGP reject-as-sets
Discard routes incoming/outgoing with AS_SET or CONFED_SET.

**Syntax** :
`bgp reject-as-sets`

**Parameters** : None

**Command mode** : configure-router-bgp-view

**Usage** : Use no bgp reject-as-sets to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# bgp reject-as-sets
Celestica-DS3000(config-router)# no bgp reject-as-sets
```

###### BGP route-map
BGP route-map delay timer. Time in secs to wait before processing route-map changes.

**Syntax** :
`bgp route-map delay-timer <dt_val>`

**Parameters** :
- `dt_val` - Delay timer. 0 disables the timer..

**Command mode** : configure-router-bgp-view

**Usage** : Use no bgp route-map delay-timer <dt_val> to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# bgp route-map delay-timer 60
Celestica-DS3000(config-router)# no bgp route-map delay-timer 60
```

###### BGP route-reflector
Allows modifications made by out route-map.

**Syntax** :
`bgp route-reflector allow-outbound-policy`

**Parameters** : None

**Command mode** : configure-router-bgp-view

**Usage** : Use no bgp route-reflector allow-outbound-policy to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# bgp route-reflector allow-outbound-policy
Celestica-DS3000(config-router)# no bgp route-reflector allow-outbound-policy
```

###### BGP route-id A.B.C.D
Configures the router identifier.

**Syntax** :
`bgp route-id <A.B.C.D>`

**Parameters** :
- `A.B.C.D` -   Manually configured router identifier

**Command mode** : configure-router-bgp-view

**Usage** : Use no bgp router-id <bgp-router-id> to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config-router)# bgp router-id 10.1.1.1
Celestica-DS3000(config-router)# no bgp router-id 10.1.1.1
```

###### BGP session-dscp
Overrides default (C0) bgp TCP session DSCP value.

**Syntax** :
`bgp session-dscp <dscp_val>`

**Parameters** :
- `dscp_val` -  DSCP Value.

**Command mode** : configure-router-bgp-view

**Usage** : Use no bgp session-dscp <dscp_val> to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config-router)# router bgp 65100
Celestica-DS3000(config-router)# bgp session-dscp 46

```

###### BGP shutdown
Administrative shutdown of all BGP peers.

**Syntax** :
`bgp shutdown [message <msg>]`

**Parameters** :
- `msg` - Shutdown message(RCS 8203)

**Command mode** : configure-router-bgp-view

**Usage** : Use no bgp router-id [message<msg>] to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config-router)# router bgp 65100

Celestica-DS3000(config-router)# bgp shutdown message "Shutting down BGP process for maintenance"
Celestica-DS3000(config-router)# no bgp shutdown message "Shutting down BGP process for maintenance"
```

###### address-family
Enters the Address Family command mode.

**Syntax** :
`address-family ipv4|ipv6 unicast`

**Parameters** : None

**Command mode** : configure-router-bgp-view

**Usage** : Use no address-family ipv4|ipv6 unicast to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# address-family ipv4 unicast
Celestica-DS3000(config-router-af-ipv4uc)# exit-address-family
```

###### aggregate-address
Configures BGP aggregate entries.

**Syntax** :
`aggregate-address <A.B.C.D><E.F.G.H>|<A.B.C.D/mask> [as-set | {origin egp|igp|incomplete} |   route-map | summary-only]`

**Parameters** :
- `A.B.C.D` - Aggregate address
- `E.F.G.H` - Aggregate mask.
- `A.B.C.D/mask` - Aggregate prefix

**Command mode** :
- configure-router-bgp-view
- configure-router-bgp-af4-view
- configure-router-bgp-af6-view

**Usage** : Use no aggregate-address <A.B.C.D><E.F.G.H>|<A.B.C.D/mask> [as-set | {origin egp|igp|incomplete} | route-map | summary-only] to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config-router)# router bgp 65100
Celestica-DS3000(config-router)# aggregate-address 10.1.1.1/24
Celestica-DS3000(config-router)# no aggregate-address 10.1.1.1/24

```

###### coalesce-timer
Configures subgroup coalesce timer.

**Syntax** :
`coalesce-time <timer_val]`

**Parameters** :
- `timer_val` - Subgroup coalesce timer value in ms.

**Command mode** : configure-router-bgp-view

**Usage** : Use no coalesce-time <timer_val> to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config-router)# router bgp 65100
Celestica-DS3000(config-router)# coalesce-time 60
Celestica-DS3000(config-router)# no coalesce-time 60
```


###### exit-address-family
Exits from the Address Family command mode.

**Syntax** :
`exit-address-family`

**Parameters** : None

**Command mode** :
- configure-router-bgp-af4-view
- configure-router-bgp-af6-view

**Usage** : None.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config-router)# router bgp 65100
Celestica-DS3000(config-router)# address-family ipv4 unicast
Celestica-DS3000(config-router-af-ipv4uc)# exit-address-family
```

###### Maximum paths
Add or delete maximum paths value for ECMP in EBGP for this BGP instance.

**Syntax** :
`maximum-paths <path-count>`

**Parameters** :
- `path-count` - Max paths count and its range is 1..128.

**Command mode** : IPv4 unicast address-family mode

**Usage** : Use `no maximum-paths <path-count>` to delete the configured maximum paths count.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
sonic(config)# router bgp 65100
sonic(config-router)# address-family ipv4 unicast
sonic(config-router-af-ipv4uc)# maximum-paths 64

sonic(config-router-af-ipv4uc)# no maximum-paths 64
```

###### Neighbor remote as
Creates a new neighbor whose remote-as is ASN.

**Syntax** :
`neighbor <peer> remote-as <asn>`

**Parameters** :
- `peer` - Peer can be an IPv4 address or an IPv6 address or an interface to use for the connection.
- `asn` - ASN identifier for the peer device.

**Command mode** : Router BGP mode

**Usage** : Use `no neighbor <peer> remote-as <asn>` to delete the neighbor.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
sonic(config)# router bgp 65100
sonic(config-router)# neighbor 30.1.1.1 remote-as 65100
sonic(config-router)# neighbor 30::1 remote-as 65100

sonic(config-router)# no neighbor 30.1.1.1 remote-as 65100
```
###### Neighbor activate
Enable/disbale L2VPN address family for a specific neighbor.

**Syntax** :
`neighbor <ip-address> activate`

**Parameters** :
- `ip-address` - The address(A.B.C.D) of IPv4 neighbor to enable L2VPN address family.

**Command mode** : L2VPN address-family mode

**Usage** : Use `no neighbor <ip-address> activate` to disable L2VPN address family for the specific neighbor.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
sonic(config)# router bgp 65100
sonic(config-router)# address-family l2vpn evpn
sonic(config-router-af-l2vpn)# neighbor 30.1.1.1 activate

sonic(config-router-af-l2vpn)# no neighbor 30.1.1.1 activate
```
###### Neighbor addpath-tx-all-paths
Uses addpath to advertise all paths to a neighbor.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> addpath-tx-all-paths`

**Parameters** :
- `A.B.C.D` - Aggregate address
- `E.F.G.H` - Aggregate mask.
- `A.B.C.D/mask` - Aggregate prefix

**Command mode** :
- configure-router-bgp-view
- configure-router-bgp-af4-view
- configure-router-bgp-af6-view

**Usage** : Use no aggregate-address <A.B.C.D><E.F.G.H>|<A.B.C.D/mask> [as-set | {origin egp|igp|incomplete} | route-map | summary-only] to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# address-family ipv4 unicast
Celestica-DS3000(config-router-af-ipv4uc)# neighbor 30.1.1.1 addpath-tx-all-paths
Celestica-DS3000(config-router-af-ipv4uc)# no neighbor 30.1.1.1 addpath-tx-all-paths

```
###### Neighbor addpath-tx-bestpath-per-AS
Uses addpath to advertise all bestpath per each neighboring AS.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> addpath-tx-bestpath-per-A`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.

**Command mode** :
- configure-router-bgp-af4-view
- configure-router-bgp-af6-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> addpath-tx-bestpath-per-AS to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# address-family ipv4 unicast
Celestica-DS3000(config-router-af-ipv4uc)# neighbor 30.1.1.1 addpath-tx-bestpath-per-AS
Celestica-DS3000(config-router-af-ipv4uc)# no neighbor 30.1.1.1 addpath-tx-bestpath-per-AS

```

###### Neighbor advertisement-interval
Specifies neighbor router; Minimum interval between sending BGP routing updates.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> advertisement-interval <adv_interval>`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.
- `adv_interval` - Advertisement interval time in seconds.

**Command mode** : configure-router-bgp-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> advertisement-interval <adv_interval> to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# neighbor 30.1.1.1 advertisement-interval 30
Celestica-DS3000(config-router)# no neighbor 30.1.1.1 advertisement-interval 30
```
###### Neighbor allowas-in
Specifies neighbor router; Accept as-path with my AS present in it.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> allowas-in [<occur_num> | origin]`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.
- `occur_num` - Number of occurrences of AS number.

**Command mode** :
- configure-router-bgp-view
- configure-router-bgp-af4-view
- configure-router-bgp-af6-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> allowas-in [<occur_num> | origin] to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# neighbor 30.1.1.1 allowas-in origin
Celestica-DS3000(config-router)# no neighbor 30.1.1.1 allowas-in origin
```

###### Neighbor as-override
Specifies neighbor router; Override ASNs in outbound updates if aspath equals remote-as.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> as-override`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.

**Command mode** :
- configure-router-bgp-view
- configure-router-bgp-af4-view
- configure-router-bgp-af6-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> as-override to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# neighbor 30.1.1.1 allowas-in origin
Celestica-DS3000(config-router)# no neighbor 30.1.1.1 allowas-in origin
```

###### Neighbor attribute-unchanged
Specifies neighbor router; BGP attribute is propagated unchanged to this neighbor.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> attribute-unchanged [as-path | med | next-hop]`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.

**Command mode** :
- configure-router-bgp-view
- configure-router-bgp-af4-view
- configure-router-bgp-af6-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> attribute-unchanged [as-path |med | next-hop] to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# neighbor 30.1.1.1 attribute-unchanged as-path
Celestica-DS3000(config-router)# no neighbor 30.1.1.1 attribute-unchanged as-path
Celestica-DS3000(config-router)# neighbor 30.1.1.1 attribute-unchanged med
Celestica-DS3000(config-router)# no neighbor 30.1.1.1 attribute-unchanged med
Celestica-DS3000(config-router)# neighbor 30.1.1.1 attribute-unchanged next-hop
Celestica-DS3000(config-router)# no neighbor 30.1.1.1 attribute-unchanged next-hop

```

###### Neighbor capability
Specifies neighbor router; Advertise capability to the peer.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> capability dynamic|extended-nexthop|{orf prefix-list both|send|receive}`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.

**Command mode** :
- configure-router-bgp-view
- configure-router-bgp-af4-view
- configure-router-bgp-af6-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> capability dynamic|extended-nexthop|{orf prefix-list both|send|receive} to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# neighbor 30.1.1.1 capability dynamic
Celestica-DS3000(config-router)# no neighbor 30.1.1.1 capability dynamic
Celestica-DS3000(config-router)# neighbor 30.1.1.1 capability extended-nexthop
Celestica-DS3000(config-router)# no neighbor 30.1.1.1 capability extended-nexthop
```


###### Neighbor default-originate
Specifies neighbor router; Originate default route to this neighbor.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> default-originate [route-map <rmap_name>]`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.
- `rmap_name` - Router map name.


**Command mode** :
- configure-router-bgp-view
- configure-router-bgp-af4-view
- configure-router-bgp-af6-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> default-originate [route-map <rmap_name>] to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# neighbor 30.1.1.1 default-originate route-map my-route-map
Celestica-DS3000(config-router)# no neighbor 30.1.1.1 default-originate route-map my-route-map
```

###### Neighbor description
Specifies neighbor router; Originate default route to this neighbor.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> default-originate [route-map <rmap_name>]`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.
- `desc` - Brief Neighbor description.


**Command mode** :
- configure-router-bgp-view
- configure-router-bgp-af4-view
- configure-router-bgp-af6-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> description [route-map <rmap_name>] to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# neighbor 30.1.1.1 description my-route-map
Celestica-DS3000(config-router)# no neighbor 30.1.1.1 description my-route-map

```

###### Neighbor disable-connected-check
Specifies neighbor router; one-hop away EBGP peer using loopback address.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> disable- connected-check`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.

**Command mode** : configure-router-bgp-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> disable-connected-check to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# neighbor 30.1.1.1 disable-connected-check
Celestica-DS3000(config-router)# no neighbor 30.1.1.1 disable-connected-check
```

###### Neighbor distribute-list
Filters updates to/from this neighbor.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> distribute-list <alst_num>|<alst_num_exp>|<dist_alst> in|out`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.
- `alst_num` - IP access-list number.
- `alst_num_exp`- IP access-list number(expanded range).
- `dist_num` - IP access-list number.

**Command mode** :
- configure-router-bgp-af4-view
- configure-router-bgp-af6-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> distribute-list <alst_num>|<alst_num_exp>|<dist_alst> in|out to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# address-family ipv4 unicast
Celestica-DS3000(config-router-af-ipv4uc)# neighbor 30.1.1.1 distribute-list 100 in
Celestica-DS3000(config-router-af-ipv4uc)# no neighbor 30.1.1.1 distribute-list
```

###### Neighbor dont-capability-negotiate
Specifies neighbor router; Do not perform capability negotiation.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> dont-capability-negotiate`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.

**Command mode** : configure-router-bgp-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> dont-capability-negotiate to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# neighbor 30.1.1.1 dont-capability-negotiate
Celestica-DS3000(config-router)# no neighbor 30.1.1.1 dont-capability-negotiate
```

###### Neighbor ebgp-multihop
Specifies neighbor router; Allow EBGP neighbors not on directly connected networks.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> ebgp-multihop [<hop_count>]`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.
- `hop_count` - Maximum hop count.

**Command mode** : configure-router-bgp-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> ebgp-multihop [<hop_count>] to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# neighbor 30.1.1.1 ebgp-multihop 3
Celestica-DS3000(config-router)# no neighbor 30.1.1.1 ebgp-multihop 3

```

###### Neighbor enforce-first-as
Specifies neighbor router; Enforce the first AS for EBGP routes.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> enforce-first-as`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.

**Command mode** : configure-router-bgp-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> enforce-first-as to remove the configuration.

**Supported Releases** :  1.1@.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# neighbor 30.1.1.1 enforce-first-as
Celestica-DS3000(config-router)# no neighbor 30.1.1.1 enforce-first-as
```

###### Neighbor enforce-multihop
Specifies neighbor router; Enforce EBGP neighbors perform multihop.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> enforce-multihop`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.

**Command mode** : configure-router-bgp-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> enforce-multihop to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# neighbor 30.1.1.1 enforce-multihop
Celestica-DS3000(config-router)# no neighbor 30.1.1.1 enforce-multihop

```

###### Neighbor filter-list
Establishes BGP filters.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> filter-list <aspath_alst> in|out`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.
- `aspath_alst` - AS path access-list name.

**Command mode** :
- configure-router-bgp-af4-view
- configure-router-bgp-af6-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> filter-list <aspath_alst> in|out to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# address-family ipv4 unicast
Celestica-DS3000(config-router-af-ipv4uc)# neighbor 30.1.1.1 filter-list ALLOW_AS_PATH in
Celestica-DS3000(config-router-af-ipv4uc)# no neighbor 30.1.1.1 filter-list ALLOW_AS_PATH in
```


###### Neighbor graceful-restart
Specifies neighbor router; Enable BGP graceful restart functionality at the peer level.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> graceful-restart`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.

**Command mode** : configure-router-bgp-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> graceful-restart to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# neighbor 30.1.1.1 graceful-restart
Celestica-DS3000(config-router)#  no neighbor 30.1.1.1 graceful-restart
```

###### Neighbor graceful-restart-disable
Specifies neighbor router; Disable the entire BGP graceful restart functionality at the peer level.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> graceful-restart-disable`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.

**Command mode** : configure-router-bgp-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> graceful-restart-disable to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# neighbor 30.1.1.1 graceful-restart-disable
Celestica-DS3000(config-router)#  no neighbor 30.1.1.1 graceful-restart-disable
```

###### Neighbor local-as
Specifies neighbor router; Specify the local-as number.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> local-as <local_asn> [no-prepend [replace-as]]`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.
- `local_asn` - AS number used as local AS.

**Command mode** : configure-router-bgp-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> local-as <local_asn> [no-prepend [replace-as]] to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# neighbor 30.1.1.1 local-as 100 no-prepend
Celestica-DS3000(config-router)# no neighbor 30.1.1.1 local-as 100 no-prepend
```
###### Neighbor maximum-prefix
Specifies neighbor router; Maximum number of prefixes that can be received from this peer.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> maximum-prefix <max_prefix> [<thrsh_val>] [force|{restart <rst_intvl>}|warning-only`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.
- `max_prefix` - Maximum number of prefix limit.
- `thrsh_val` - Threshold value (%) at which to generate a warning message.
- `rst_intvl1` - Restart value in minutes.

**Command mode** :
- configure-router-bgp-view
- configure-router-bgp-af4-view
- configure-router-bgp-af4-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> maximum-prefix <max_prefix> [<thrsh_val>] [force|{restart <rst_intvl>}|warning-only] to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# neighbor 30.1.1.1 maximum-prefix 10000 force
Celestica-DS3000(config-router)# no neighbor 30.1.1.1 maximum-prefix 10000 force
```
###### Neighbor maximum-prefix-out
Specifies neighbor router; Maximum number of prefixes that can to be sent to this peer.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> maximum-prefix-out <max_prefix>`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.
- `max_prefix` - Maximum number of prefix limit.

**Command mode** :
- configure-router-bgp-view
- configure-router-bgp-af4-view
- configure-router-bgp-af4-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> maximum-prefix <max_prefix> [<thrsh_val>] [force|{restart <rst_intvl>}|warning-only] to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# neighbor 30.1.1.1 maximum-prefix-out 10000
Celestica-DS3000(config-router)# no neighbor 30.1.1.1 maximum-prefix-out 10000
```

###### Neighbor next-hop-self
Specifies neighbor router; Disable the next hop calculation for this neighbor.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> next-hop-self [force]`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.

**Command mode** :
- configure-router-bgp-view
- configure-router-bgp-af4-view
- configure-router-bgp-af4-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> next-hop-self [force] to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# neighbor 30.1.1.1 next-hop-self force
Celestica-DS3000(config-router)# no neighbor 30.1.1.1 next-hop-self force
```

###### Neighbor next-hop-local
Specifies neighbor router; Configure treatment of outgoing link-local nexthop attribute.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> nexthop-loacl [unchanged]`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.

**Command mode** :
- configure-router-bgp-view
- configure-router-bgp-af4-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> nexthop-local [unchanged] to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

###### Neighbor override-capability
Specifies neighbor router; Override capability negotiation result.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> override-capability.`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.

**Command mode** : Configure-router-bgp-view


**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> override-capability to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# neighbor 30.1.1.1 override-capability
Celestica-DS3000(config-router)# no neighbor 30.1.1.1 override-capability

```
###### Neighbor passive
Specifies neighbor router; Don't send open messages to this neighbor.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> passive`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.

**Command mode** : configure-router-bgp-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> passive to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# neighbor 30.1.1.1 passive
Celestica-DS3000(config-router)# no neighbor 30.1.1.1 passive
```
###### Neighbor password
Specifies neighbor router; Sent an MD5 password.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> password <passwd>`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.
- `passwd` - Password string.

**Command mode** : configure-router-bgp-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> password <passwd> to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# neighbor 30.1.1.1 password my
Celestica-DS3000(config-router)# no neighbor 30.1.1.1 password my
```

###### Neighor peer-group
Specifies neighbor router; Member of Peer Group.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> peer-group <peergrp_name>`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.
- `peergrp_name` - Peer Group Name.

**Command mode** : configure-router-bgp-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> peer-group <peergrp_name> to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# neighbor 30.1.1.1 peer-group
Celestica-DS3000(config-router)# no neighbor 30.1.1.1 peer-group
```

###### Neighbor port
Specifies neighbor router; Neighbor’s BGP port.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> port <port_num>`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.
- `port_num` - TCP port number.

**Command mode** : configure-router-bgp-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> port <port_num> to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# neighbor 30.1.1.1 port 65100
Celestica-DS3000(config-router)# no neighbor 30.1.1.1 port 65100
```

###### Neighbor prefix-list
Filters updates to/from this.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> prefix-list <prfxlst_name> in|out`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.
- `prfxlst_name` - Name of prefix list.

**Command mode** :
- configure-router-bgp-af4-view
- configure-router-bgp-af6-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> prefix-list <prfxlst_name> in|out to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# address-family ipv4 unicast
Celestica-DS3000(config-router-af-ipv4uc)# neighbor 30.1.1.1 prefix-list in out
Celestica-DS3000(config-router-af-ipv4uc)# no neighbor 30.1.1.1 prefix-list in out
```
###### Neighbor remove-private-as
Specifies neighbor router; Remove private ASNs in outbound updates.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> remove-private-as [{all replace-as}|replace-as]`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.

**Command mode** :
- configure-router-bgp-view
- configure-router-bgp-af4-view
- configure-router-bgp-af6-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> remove-private-as [{all replace-as}replace-as] to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# address-family ipv4 unicast
Celestica-DS3000(config-router-af-ipv4uc)# neighbor 30.1.1.1 remove-private-AS all
Celestica-DS3000(config-router-af-ipv4uc)# no neighbor 30.1.1.1 remove-private-AS all
```

###### Neighbor route-map
Specifies neighbor router; Apply route map to neighbor.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> route-map <rmap_name> in|out`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.
- `rmap_name` - Name of route map.

**Command mode** :
- configure-router-bgp-view
- configure-router-bgp-af4-view
- configure-router-bgp-af6-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> route-map <rmap_name> in|out to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# address-family ipv4 unicast
Celestica-DS3000(config-router-af-ipv4uc)# neighbor 30.1.1.1 route-map my-route-map in
Celestica-DS3000(config-router-af-ipv4uc)# no neighbor 30.1.1.1 route-map my-route-map in
```

###### Route Reflector Client
Configures a neighbor as Route Reflector client

**Syntax** :
`neighbor <A.B.C.D>|<A::B>|<L3Inf>|<neigh-tag> route-reflector-client`

**Parameters** :
- `A.B.C.D`   - IPv4 neighbor to enable L2VPN address family.
- `A::B`      - IPv6 neighbor to enable L2VPN address family.
- `L3Inf`     - L3 Interface Name
- `neigh-tag` - Neighbor tag (string)

**Command mode** : L2VPN address-family mode

**Usage** : Use `no neighbor  <A.B.C.D>|<A::B>|<L3Inf>|<neigh-tag> route-reflector-client` to remove the configuration.

**Supported Releases** :  2.0 or later

**Click commands** : None

**Example**
```
sonic(config)# router bgp 65100
sonic(config-router)# neighbor 30.1.1.1 remote-as 1
sonic(config-router)# address-family l2vpn evpn
sonic(config-router-af-l2vpn)# neighbor 30.1.1.1 route-reflector-client
sonic(config-router-af-l2vpn)#
sonic(config-router-af-l2vpn)# no neighbor 30.1.1.1 route-reflector-client
```
###### Neighbor route-server-client
Configures a neighbor as Route Server client.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> route-server-client`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.

**Command mode** :
- configure-router-bgp-view
- configure-router-bgp-af4-view
- configure-router-bgp-af6-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> route-server-client to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# address-family ipv4 unicast
Celestica-DS3000(config-router-af-ipv4uc)# neighbor 30.1.1.1 route-server-client
Celestica-DS3000(config-router-af-ipv4uc)# no neighbor 30.1.1.1 route-server-client
```

###### Neighbor send-community
Specifies neighbor router; Send Community attribute to this neighbor.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> send-community [all|both|extended|large|extended]`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.

**Command mode** :
- configure-router-bgp-view
- configure-router-bgp-af4-view
- configure-router-bgp-af6-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> send-community [all|both|extended|large|extended] to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config-router)# router bgp 65100
Celestica-DS3000(config-router)# neighbor 30.1.1.1 send-community extended
Celestica-DS3000(config-router)# no neighbor 30.1.1.1 send-community extended
```

###### Neighbor sender-as-path-loop-detection
Specifies neighbor router; Detect AS loops before sending to neighbor.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> sender-as-path-loop-detection`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.

**Command mode** :  configure-router-bgp-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> sender-as-path-loop-detection to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config-router)# router bgp 65100
Celestica-DS3000(config-router)# neighbor 30.1.1.1 sender-as-path-loop-detection
Celestica-DS3000(config-router)# no neighbor 30.1.1.1 sender-as-path-loop-detection
```

###### Neighbor shutdown
Specifies neighbor router; Administratively shutdown this neighbor.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> shutdown [message <msg>|rtt <rt_time>]`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.
- `msg` - Shutdown message(RFC 8203).
- `rt_time` - Shutdown if rounded-trip-time is higher than expected.

**Command mode** :  configure-router-bgp-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> shutdown [message <msg>|rtt <rt_time>] to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config-router)# router bgp 65100
Celestica-DS3000(config-router)# neighbor 30.1.1.1 shutdown message "Server is under maintenance"
Celestica-DS3000(config-router)# no neighbor 30.1.1.1 shutdown message "Server is under maintenance"
```

###### Neighbor soft-reconfiguration
Specifies neighbor router; Per neighbor soft reconfiguration.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> soft-reconfiguration inbound`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.

**Command mode** :
- configure-router-bgp-view
- configure-router-bgp-af4-view
- configure-router-bgp-af6-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> soft-reconfiguration inbound to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config-router)# router bgp 65100
Celestica-DS3000(config-router)# address-family ipv4 unicast
Celestica-DS3000(config-router-af-ipv4uc)# neighbor 30.1.1.1 soft-reconfiguration inbound
Celestica-DS3000(config-router-af-ipv4uc)# no neighbor 30.1.1.1 soft-reconfiguration inbound
```


###### Neighbor solo
Specifies neighbor router; Solo peer - part of its own update group.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> solo`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.

**Command mode** :  configure-router-bgp-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> solo to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config-router)# router bgp 65100
Celestica-DS3000(config-router)# neighbor 30.1.1.1 solo
Celestica-DS3000(config-router)# no neighbor 30.1.1.1 solo

```

###### Neighbor strict-capability-match
Specifies neighbor router; Strict capability negotiation match.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> strict-capability-match`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.

**Command mode** :  configure-router-bgp-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> strict-capability-match to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config-router)# router bgp 65100
Celestica-DS3000(config-router)# neighbor 30.1.1.1 strict-capability-match
Celestica-DS3000(config-router)# no neighbor 30.1.1.1 strict-capability-match
```
###### Neighbor timers
Specifies neighbor router; BGP per neighbor timers.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> timers [{<keepalive_time> <hold_time>}|{connect <connect_timer>}`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.
- `keepalive_time` - Keepalive interval.
- `hold_time` - Holdtime.
- `connect_timer` - Connect timer.

**Command mode** :  configure-router-bgp-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> timers [{<keepalive_time> <hold_time>}|{connect <connect_timer>}] to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config-router)# router bgp 65100
Celestica-DS3000(config-router)# neighbor 30.1.1.1 timers connect 60
Celestica-DS3000(config-router)# no neighbor 30.1.1.1 timers connect 60
```

###### Neighbor ttl-security
Specifies neighbor router; BGP ttl-security parameters.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> ttl-security [hops <hops_num>]`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.
- `hops_num` - Number of hops to BGP peer.

**Command mode** :  configure-router-bgp-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> ttl-security [hops <hops_num>] to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config-router)# router bgp 65100
Celestica-DS3000(config-router)# neighbor 30.1.1.1 ttl-security hops 100
Celestica-DS3000(config-router)# no neighbor 30.1.1.1 ttl-security hops 100
Celestica-DS3000(config-router)#
```

###### Neighbor unsuppress-map
Route-map to selectively unsuppress suppressed routes.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> unsuppress-map <rmap_name>`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.
- `rmap_name` - Name of route map.

**Command mode** :  configure-router-bgp-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> unsuppress-map <rmap_name> to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# address-family ipv4 unicast
Celestica-DS3000(config-router-af-ipv4uc)# neighbor 30.1.1.1 unsuppress-map my-route-map
Celestica-DS3000(config-router-af-ipv4uc)# no neighbor 30.1.1.1 unsuppress-map my-route-map
```

###### Neighbor update-source
Specifies neighbor router; Source of routing updates.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> update-source [<A.B.C.D>|<A::B>|<l3_intf>]`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.
- `A.B.C.D` - IPv4 address.
- `A:B` - IPv6 address.
- `l3_intf` - L3 Interface name(requires Zebra to be running).

**Command mode** :  configure-router-bgp-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> update-source [<A.B.C.D>|<A::B>|<l3_intf>] to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# neighbor 30.1.1.1 update-source 50.50.50.1
Celestica-DS3000(config-router)# no neighbor 30.1.1.1 update-source 50.50.50.1
```

###### Neighbor weight
Specifies neighbor router; Set default weight for routes from this neighbor.

**Syntax** :
`neighbor <neigh_addr> | <l3_intf> | <neigh_tag> weight <def_weight>`

**Parameters** :
- `neigh_addr` - IPV4 or IPV6 Neighbor address.
- `l3_intf` - L3 Interface.
- `neigh_tag` - Neighbor tag.
- `def_weight` - Default weight.

**Command mode** :
- configure-router-bgp-view
- configure-router-bgp-af4-view
- configure-router-bgp-af6-view

**Usage** : Use no neighbor <neigh_addr> | <l3_intf> | <neigh_tag> weight <def_weight> to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# address-family ipv4 unicast
Celestica-DS3000(config-router-af-ipv4uc)# neighbor 30.1.1.1 weight 100
Celestica-DS3000(config-router-af-ipv4uc)# no neighbor 30.1.1.1 weight 100
```
###### network
Specifies a network to announce via BGP

**Syntax** :
`network {<A.B.C.D> mask <E.F.G.H>} | <A.B.C.D/mask> [backdoor | route-map <rmap_name>]`

**Parameters** :
- `A.B.C.D` - Network address.
- `E.G.G.H` - Network mask.
- `A.B.C.D/mask` - IPv4 prefix.
- `rmap_name` - Route mpa name.

**Command mode** :
- configure-router-bgp-view

**Usage** : Use no network {<A.B.C.D> mask <E.F.G.H>} | <A.B.C.D/mask> [backdoor | route-map <rmap_name>] to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config-router)# network 30.1.1.1 mask 255.255.255.0
Celestica-DS3000(config-router)# no network 30.1.1.1 mask 255.255.255.0
```

###### redistribute
Redistributes information from another routing protocol.

**Syntax** :
`redistribute connected | kernel | ospf <ospf_id> | static | table <table_id> [metric <def_metric>] [route-map <rmap_ref>]`

**Parameters** :
- `ospf_id` - OSPF Instance ID.
- `table_id` - Table ID.
- `def_metric` - Default Metric.
- `rmap_name` - Name of route map.

**Command mode** :
- configure-router-bgp-af4-view
- configure-router-bgp-af6-view

**Usage** : Use no redistribute connected | kernel | ospf <ospf_id> | static | table <table_id> [metric <def_metric>] [route-map <rmap_ref>] to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS2000(config)# router bgp 65100
Celestica-DS3000(config-router)# address-family ipv4 unicast
Celestica-DS3000(config-router-af-ipv4uc)# redistribute connected metric 100
Celestica-DS3000(config-router-af-ipv4uc)# no redistribute connected metric 100
```

###### table-map
Configures BGP table to RIB route download filter.

**Syntax** :
`table-map <route_map>`

**Parameters** :
- `rmap_name` - Name of route map.

**Command mode** :
- configure-router-bgp-view
- configure-router-bgp-af4-view
- configure-router-bgp-af6-view

**Usage** : Use no table-map <route_map> to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS2000(config)# router bgp 65100
Celestica-DS3000(config-router)# table-map my-route-map
Celestica-DS3000(config-router)# no table-map my-route-map
```

###### timers
Configures BGP table to RIB route download filter.

**Syntax** :
`timers bgp <keepalive_time> <hold_time>`

**Parameters** :
- `keepalive_time` - Keepalive interval.
- `hold_time` - Holdtime.

**Command mode** :
- configure-router-bgp-view

**Usage** : Use no table-map <keepalive_time> <hold_time> to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS2000(config)# router bgp 65100
Celestica-DS3000(config-router)# timers bgp 60 180
Celestica-DS3000(config-router)# no timers bgp 60 180
```

###### update-delay
Forces initial delay for best-path and updates.

**Syntax** :
`update-delay <max_delay> <wait_time>`

**Parameters** :
- `max_delay` - Maximum delay in seconds.
- `wait_time` - Wait time in seconds.

**Command mode** :
- configure-router-bgp-view

**Usage** : Use no update-delay <max_delay> <wait_time> to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
Celestica-DS3000(config)# router bgp 65100
Celestica-DS3000(config-router)# update-delay 180 60
Celestica-DS3000(config-router)# no update-delay 180 60
```

###### IPv4 AFI extension
Multiprotocol extensions enable BGP to carry routing information for multiple network layer protocols. To support IPv4 unicast routing information, use IPv4 unicast Subsequent Address Family Identifier(SAFI) configs. Enters into BGP router IPv4 unicast SAFI mode "config-router-af-ipv4uc".

**Syntax** :
`address-family ipv4 unicast`

**Command mode** : Router BGP mode

**Usage** : Use `exit-address-family` to come out of the IPv4 Unicast Subsequent Address Family config mode.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
sonic(config)# router bgp 65100
sonic(config-router)# address-family ipv4 unicast
sonic(config-router-af-ipv4uc)# exit-address-family
sonic(config-router)#
```

###### IPv4 AFI extension
Multiprotocol extensions enable BGP to carry routing information for multiple network layer protocols. To support IPv4 unicast routing information, use IPv4 unicast Subsequent Address Family Identifier(SAFI) configs. Enters into BGP router IPv4 unicast SAFI mode "config-router-af-ipv4uc".

**Syntax** :
`address-family ipv4 unicast`

**Command mode** : Router BGP mode

**Usage** : Use `exit-address-family` to come out of the IPv4 Unicast Subsequent Address Family config mode.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
sonic(config)# router bgp 65100
sonic(config-router)# address-family ipv4 unicast
sonic(config-router-af-ipv4uc)# exit-address-family
sonic(config-router)#
```

###### Network announcement
Add or delete networks to be announced.

**Syntax** :
`network <ip-address>`

**Parameters** :
- `ip-address` - IPv4 Network address (A.B.C.D/M) to be announced to all of its peers.

**Command mode** : IPv4 unicast address-family mode

**Usage** : Use `no network <ip-address>` to withdraw the IPv4 network announcement.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
sonic(config)# router bgp 65100
sonic(config-router)# address-family ipv4 unicast
sonic(config-router-af-ipv4uc)# network 3.3.3.3/32

sonic(config-router-af-ipv4uc)# no network 3.3.3.3/32
```

###### IPv6 AFI extension
Add or delete IPv6 Unicast Subsequent Address Family Identifier(SAFI) configs to carry routing information for IPv6 unicast type traffic. Enters into BGP router IPv6 unicast SAFI mode "config-router-af-ipv6uc".

**Syntax** :
`address-family ipv6 unicast`

**Command mode** : Router BGP mode

**Usage** : Use `exit-address-family` to come out of the IPv6 Unicast Subsequent Address Family config mode.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
sonic(config)# router bgp 65100
sonic(config-router)# address-family ipv6 unicast
sonic(config-router-af-ipv6uc)# exit-address-family
sonic(config-router)#
```

###### L2VPN AFI extension
Add or delete EVPN Subsequent Address Family Identifier(SAFI) configs to carry routing information for L2VPN EVPN type traffic. Enters into BGP router "config-router-af-l2vpn" mode.

**Syntax** :
`address-family l2vpn evpn`

**Command mode** : Router BGP mode

**Usage** : Use `exit-address-family` to come out of the EVPN Subsequent Address Family config mode.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
sonic(config)# router bgp 65100
sonic(config-router)# address-family l2vpn evpn
sonic(config-router-af-l2vpn)# exit-address-family
sonic(config-router)#
```

###### Neighbor activate
Enable/disbale L2VPN address family for a specific neighbor.

**Syntax** :
`neighbor <A.B.C.D>|<A::B>|<L3Inf>|<neigh-tag> activate`

**Parameters** :
- `A.B.C.D`   - IPv4 neighbor to enable L2VPN address family.
- `A::B`      - IPv6 neighbor to enable L2VPN address family.
- `L3Inf`     - L3 Interface Name
- `neigh-tag` - Neighbor tag (string)

**Command mode** : L2VPN address-family mode

**Usage** : Use `no neighbor <A.B.C.D>|<A::B>|<L3Inf>|<neigh-tag> activate` to disable L2VPN address family for the specific neighbor.

**Supported Releases** :  2.0 or later

**Click commands** : None

**Example**
```
sonic(config)# router bgp 65100
sonic(config-router)# address-family l2vpn evpn
sonic(config-router-af-l2vpn)# neighbor 30.1.1.1 activate

sonic(config-router-af-l2vpn)# no neighbor 30.1.1.1 activate
```

###### Route Reflector Client
Configures a neighbor as Route Reflector client

**Syntax** :
`neighbor <A.B.C.D>|<A::B>|<L3Inf>|<neigh-tag> route-reflector-client`

**Parameters** :
- `A.B.C.D`   - IPv4 neighbor to enable L2VPN address family.
- `A::B`      - IPv6 neighbor to enable L2VPN address family.
- `L3Inf`     - L3 Interface Name
- `neigh-tag` - Neighbor tag (string)

**Command mode** : L2VPN address-family mode

**Usage** : Use `no neighbor  <A.B.C.D>|<A::B>|<L3Inf>|<neigh-tag> route-reflector-client` to remove the configuration.

**Supported Releases** :  2.0 or later

**Click commands** : None

**Example**
```
sonic(config)# router bgp 65100
sonic(config-router)# neighbor 30.1.1.1 remote-as 1
sonic(config-router)# address-family l2vpn evpn
sonic(config-router-af-l2vpn)# neighbor 30.1.1.1 route-reflector-client
sonic(config-router-af-l2vpn)#
sonic(config-router-af-l2vpn)# no neighbor 30.1.1.1 route-reflector-client
```

###### Advertise all vni
Enable/disable advertising of all configured VNIs in its local VTEP.

**Syntax** :
`advertise-all-vni`

**Command mode** : L2VPN address-family mode

**Usage** : Use `no advertise-all-vni` to disable advertisment of all VNIs configured in its local VTEP.

**Supported Releases** :  1.1.0 or later

**Click commands** : None

**Example**
```
sonic(config)# router bgp 65100
sonic(config-router)# address-family l2vpn evpn
sonic(config-router-af-l2vpn)# advertise-all-vni

sonic(config-router-af-l2vpn)# no advertise-all-vni
```

###### Advertise
Advertises prefix routes.

**Syntax** : `advertise ipv4|ipv6 unicast [gateway-ip|route-map <rmap>]`

**Command mode** : L2VPN address-family mode

**Parameters**  :
- `rmap`   - route-map for filtering specific routes

**Usage** : Use `no advertise ipv4|ipv6 unicast [route-map <rmap>]` to remove the configuration.

**Supported Releases** :  2.0 or later

**Click commands** : None

**Example**
```
sonic(config)# router bgp 65100
sonic(config-router)# address-family l2vpn evpn
sonic(config-router-af-l2vpn)# advertise ipv4 unicast
sonic(config-router-af-l2vpn)# no advertise ipv4 unicast
sonic(config-router-af-l2vpn)# advertise ipv6 unicast
sonic(config-router-af-l2vpn)# no advertise ipv6 unicast
```

### VxLAN Show commands
#### Show vxlan interface
Displays VTEP specific configurations such as source interface, IP, nvo etc.,

**Syntax**: `show vxlan interface`

**Command mode** : Exec mode

**Usage** : Use this command to retrieve the vxlan interface/VTEP specific configurations.

**Click command** : `show vxlan interface`

**Example**
```
sonic# show vxlan interface
VTEP Name             : vtep1
VTEP Source IP        : 1.1.1.1
EVPN NVO Name         : nvo1
Source Interface      : Loopback0
sonic#

```

#### Show vxlan vlanvnimap
Displays VLAN VNI Mapping Information in the local VTEP

**Syntax**: `show vxlan vlanvnimap [count]`

**Command mode** : Exec mode

**Usage** : Use this command to retrieve the local VTEP's vlan vni map configurations.

**Click command** : `show vxlan vlanvnimap [count]`

**Example**
```
sonic# show vxlan vlanvnimap
   VLAN      VNI
   ====      ===
  Vlan10    100010
  Vlan11    100011
  Vlan12    100012
  Vlan15    100015
Total count :   4
sonic#
sonic# show vxlan vlanvnimap count
Total count :   4
sonic#
```

#### Show vxlan tunnel
Displays EVPN VxLAN tunnel(s) information such as tunnel-name, source-ip, destination-ip,tunnel-type, oper-status.

**Syntax**: `show vxlan tunnel`

**Command mode** : Exec mode

**Usage** : Use this command to retrieve the vxlan tunnel information and its status.

**Click command** : `show vxlan tunnel`

**Example**
```
sonic# show vxlan tunnel
        Name                SIP                DIP           source     operstatus
        ====                ===                ===           ======     ==========
    EVPN_2.2.2.2          1.1.1.1            2.2.2.2          EVPN       oper_up
    EVPN_3.3.3.3          1.1.1.1            3.3.3.3          EVPN       oper_up
sonic#
```

#### Show vxlan counters
Displays VxLAN tunnel(s)' counters information such as rx_packets, tx_packets count, rate etc., Tunnel flex-counters need to be enabled by using 'counterpoll tunnel enable' CLICK command before executing this command.

**Syntax**: `show vxlan counters [<tunnel-name>]`

**Parameters** :
- `tunnel-name` - VLAN tunnel name in string format

**Command mode** : Exec mode

**Usage** : Use this command to retrieve the vxlan tunnel(s) counters information.
                  Its recommended to change its default polling-interval of 10sec to 1sec(1000ms) by using 'counterpoll tunnel interval 1000' CLICK command, to get the most recent polled tunnel counters.

**Click command** : `show vxlan counters [TUNNEL]`

**Example**
```
sonic# show vxlan counters
Polling Rate : 1 seconds
Interface       RX_PKTS      RX_PPS(P/s)    RX_BYTES      RX_BPS(B/s)    TX_PKTS      TX_PPS(P/s)    TX_BYTES      TX_BPS(B/s)
-----------------------------------------------------------------------------------------------------------------------------
EVPN_2.2.2.2    21343830     899337.84      2433196760    102524513.74   0            0.0            0             0.0
EVPN_3.3.3.3    0            0.0            0             0.0            0            0.0            0             0.0
vtep1           0            0.0            0             0.0            0            0.0            0             0.0
sonic#
```

#### Show vxlan vni-map
Displays the VRF VNI Mapping Information

**Syntax**: `show vxlan vni-map`

**Command mode** : Exec mode

**Usage** : Use this command to retrieve the vxlan vrf vni mapping configuration.

**Click command** : `show vxlan vrfvnimap`

**Example**
```
Celestica-DS1000# show vxlan vni-map
-------------------------
VNI ID          VRF
-------------------------
3000            Vrf01
2000            Vrf02
Celestica-DS1000#
```

#### Show vxlan remote mac
Displays mac entries that are learned from a remote VTEP through EVPN type-2 route advertisements.

**Syntax**: `show vxlan remote mac [<rem-vtep-ip] [count]`

**Parameters** :
- `rem-vtep-ip` - remote VTEP's IPv4 address in (A.B.C.D) format

**Command mode** : Exec mode

**Usage** : Use this command to retrieve the mac entries learned from all remote VTEPs or the specified remote VTEP.

**Click command** : `show vxlan remotemac REMOTE_VTEP_IP [COUNT]`

**Example**
```
sonic# show vxlan remote mac
   Vlan           Mac             RemoteVTEP      VNI       Type
 -----------------------------------------------------------------
  Vlan10   00:00:01:10:01:01       2.2.2.2       100010   DYNAMIC
  Vlan10   00:00:01:10:01:02       2.2.2.2       100010   DYNAMIC
  Vlan10   00:00:03:10:01:01       3.3.3.3       100010   DYNAMIC
  Vlan10   00:00:03:10:01:02       3.3.3.3       100010   DYNAMIC
Total count :   4
sonic# show vxlan remote mac 2.2.2.2
   Vlan           Mac             RemoteVTEP      VNI       Type
 -----------------------------------------------------------------
  Vlan10   00:00:01:10:01:01       2.2.2.2       100010   DYNAMIC
  Vlan10   00:00:01:10:01:02       2.2.2.2       100010   DYNAMIC
Total count :   2
sonic# show vxlan remote mac 3.3.3.3
   Vlan           Mac             RemoteVTEP      VNI       Type
 -----------------------------------------------------------------
  Vlan10   00:00:03:10:01:01       3.3.3.3       100010   DYNAMIC
  Vlan10   00:00:03:10:01:02       3.3.3.3       100010   DYNAMIC
Total count :   2
sonic# show vxlan remote mac count
Total count :   4
sonic# show vxlan remote mac count 2.2.2.2
Total count :   2
sonic#

When no macs are learned
sonic# show vxlan remote mac
Total count :   0
sonic#

```

#### Show vxlan remote vni
 Displays VNIs mapped to vlans in all remote VTEPs or the specified remote VTEP IP.

**Syntax**: `show vxlan remote vni [<rem-vtep-ip>] [count]`

**Parameters** :
- `rem-vtep-ip` - remote VTEP's IPv4 address in (A.B.C.D) format

**Command mode** : Exec mode

**Usage** : Use this command to retrieve the list of VNIs mapped to vlans from all remote VTEPs or the specified remote VTEP.

**Click command** : `show vxlan remotevni REMOTE_VTEP_IP [COUNT]`

**Example**
```
sonic# show vxlan remote vni
   Vlan      RemoteVTEP      VNI
   ====      ==========      ===
  Vlan10      2.2.2.2       100010
  Vlan11      2.2.2.2       100011
  Vlan10      3.3.3.3       100010
  Vlan13      3.3.3.3       100013
  Vlan15      3.3.3.3       100015
Total count :   5
sonic# show vxlan remote vni 3.3.3.3
   Vlan      RemoteVTEP      VNI
   ====      ==========      ===
  Vlan10      3.3.3.3       100010
  Vlan13      3.3.3.3       100013
  Vlan15      3.3.3.3       100015
Total count :   3
sonic# show vxlan remote vni count 3.3.3.3
Total count :   3
sonic# show vxlan remote vni count
Total count :   5
```

#### BGP EVPN show commands
##### Show bgp l2vpn evpn
Display the FRR BGP EVPN routes information.

**Syntax**: `show bgp l2vpn evpn`

**Command mode** : Exec mode

**Usage** : Use this command to get information related EVPN routes.

**Click command** : `None`

**Example**
```
sonic# show bgp l2vpn evpn
BGP table version is 364, local router ID is 2.2.2.2
Status codes: s suppressed, d damped, h history, * valid, > best, i - internal
Origin codes: i - IGP, e - EGP, ? - incomplete
EVPN type-1 prefix: [1]:[ESI]:[EthTag]:[IPlen]:[VTEP-IP]
EVPN type-2 prefix: [2]:[EthTag]:[MAClen]:[MAC]:[IPlen]:[IP]
EVPN type-3 prefix: [3]:[EthTag]:[IPlen]:[OrigIP]
EVPN type-4 prefix: [4]:[ESI]:[IPlen]:[OrigIP]
EVPN type-5 prefix: [5]:[EthTag]:[IPlen]:[IP]

   Network          Next Hop            Metric LocPrf Weight Path
Route Distinguisher: 2.2.2.2:2
*> [2]:[0]:[48]:[00:00:01:10:01:01]
                    2.2.2.2                            32768 i
                    ET:8 RT:65100:100010
*> [2]:[0]:[48]:[00:00:01:10:01:02]
                    2.2.2.2                            32768 i
                    ET:8 RT:65100:100010
*> [3]:[0]:[32]:[2.2.2.2]
                    2.2.2.2                            32768 i
                    ET:8 RT:65100:100010
Route Distinguisher: 2.2.2.2:3
*> [3]:[0]:[32]:[2.2.2.2]
                    2.2.2.2                            32768 i
                    ET:8 RT:65100:100020
Route Distinguisher: 3.3.3.3:2
*>i[3]:[0]:[32]:[3.3.3.3]
                    3.3.3.3                       100      0 i
                    RT:65100:100010 ET:8

Displayed 5 out of 5 total prefixes

sonic#
```

##### Show bgp l2vpn evpn all overlay
Display BGP Overlay Information for all prefixes.

**Syntax**: `show bgp l2vpn evpn all overlay`

**Command mode** : Exec mode

**Usage** : Use this command to get overlay specific information.

**Click command** : `None`

**Example**
```
sonic# show bgp l2vpn evpn all overlay
   Network          Next Hop      EthTag    Overlay Index   RouterMac
Route Distinguisher: 2.2.2.2:2
*> [2]:[0]:[48]:[00:00:01:10:01:01]
                    2.2.2.2         /2.2.2.2
*> [2]:[0]:[48]:[00:00:01:10:01:02]
                    2.2.2.2         /2.2.2.2
*> [3]:[0]:[32]:[2.2.2.2]
                    2.2.2.2         /0.0.0.0
Route Distinguisher: 3.3.3.3:2

Displayed 4 out of 4 total prefixes
sonic#
```

##### Show bgp l2vpn evpn all tags
Display BGP tags for all prefixes.

**Syntax**: `show bgp l2vpn evpn all tags`

**Command mode** : Exec mode

**Usage** : Use this command to get tag specific information.

**Click command** : `None`

**Example**
```
sonic# show bgp l2vpn evpn all tags
   Network          Next Hop      In tag/Out tag
Route Distinguisher: 2.2.2.2:2
*> [2]:[0]:[48]:[00:00:01:10:01:01]
                    2.2.2.2         *> [2]:[0]:[48]:[00:00:01:10:01:02]
                    2.2.2.2         *> [3]:[0]:[32]:[2.2.2.2]
                    2.2.2.2         Route Distinguisher: 3.3.3.3:2

Displayed 4 out of 4 total prefixes

sonic#
```

##### Show bgp l2vpn evpn import-rt
Display all imported route targets.

**Syntax**: `show bgp l2vpn evpn import-rt [json]`

**Parameters** :
- `json` : To get output in JavaScript Object Notation

**Command mode** : Exec mode

**Usage** : Use 'json' option to get output in json format.

**Click command** : `None`

**Example**
```
sonic# show bgp l2vpn evpn import-rt
Route-target: 0:100020
List of VNIs importing routes with this route-target:
  100020
Route-target: 0:100010
List of VNIs importing routes with this route-target:
  100010
sonic#
sonic# show bgp l2vpn evpn import-rt json
{
  "0:100020":{
    "rt":"0:100020",
    "vnis":[
      100020
    ]
  },
  "0:100010":{
    "rt":"0:100010",
    "vnis":[
      100010
    ]
  }
}
sonic#
```

##### Show bgp l2vpn evpn neighbors advertised-routes
Display the routes advertised to a given BGP EVPN neighbor.

**Syntax**: `show bgp l2vpn evpn neighbors <neighbor-ip> advertised-routes [json]`

**Parameters** :
- `neighbor-ip` : Neighbor-ip could be IPv4(A.B.C.D) or IPv6(A::B) address
- `json` : To get output in JavaScript Object Notation

**Command mode** : Exec mode

**Usage** : Use 'json' option to get output in json format.

**Click command** : `None`

**Example**
```
sonic# show bgp l2vpn evpn neighbors 30.1.1.2 advertised-routes
BGP table version is 0, local router ID is 2.2.2.2
Default local pref 100, local AS 65100
Status codes: s suppressed, d damped, h history, * valid, > best, i - internal
Origin codes: i - IGP, e - EGP, ? - incomplete

   Network          Next Hop            Metric LocPrf Weight Path
Route Distinguisher: 2.2.2.2:2
*> [2]:[0]:[48]:[00:00:01:10:01:01]
                                  100  32768 i
*> [2]:[0]:[48]:[00:00:01:10:01:02]
                                  100  32768 i
*> [3]:[0]:[32]:[2.2.2.2]
                                  100  32768 i
Route Distinguisher: 2.2.2.2:3
*> [3]:[0]:[32]:[2.2.2.2]
                                  100  32768 i

Total number of prefixes 4

sonic#
```

##### Show bgp l2vpn evpn neighbors routes
Display routes learned from a given neighbor.

**Syntax**: `show bgp l2vpn evpn neighbors <neighbor-ip> routes [json]`

**Parameters** :
- `neighbor-ip` : Neighbor-ip could be IPv4(A.B.C.D) or IPv6(A::B) address
- `json` : To get output in JavaScript Object Notation

**Parameters** :
- `` :

**Command mode** : Exec mode

**Usage** : Use 'json' option to get output in json format.

**Click command** : `None`

**Example**
```
sonic# show bgp l2vpn evpn neighbors 30.1.1.2 routes
BGP table version is 1, local router ID is 2.2.2.2
Status codes: s suppressed, d damped, h history, * valid, > best, i - internal
Origin codes: i - IGP, e - EGP, ? - incomplete
EVPN type-1 prefix: [1]:[ESI]:[EthTag]:[IPlen]:[VTEP-IP]
EVPN type-2 prefix: [2]:[EthTag]:[MAClen]:[MAC]:[IPlen]:[IP]
EVPN type-3 prefix: [3]:[EthTag]:[IPlen]:[OrigIP]
EVPN type-4 prefix: [4]:[ESI]:[IPlen]:[OrigIP]
EVPN type-5 prefix: [5]:[EthTag]:[IPlen]:[IP]

   Network          Next Hop            Metric LocPrf Weight Path
Route Distinguisher: 3.3.3.3:2
*>i[3]:[0]:[32]:[3.3.3.3]
                    3.3.3.3                       100      0 i
                    RT:65100:100010 ET:8

Displayed 1 out of 5 total prefixes

sonic#
```

##### Show bgp l2vpn evpn route
Displays BGP EVPN route information.

**Syntax**: `show bgp l2vpn evpn route [type <route-type> [json]] | [json]`

**Parameters** :
- `route-type` : Type of the route queried.
                 It can any one of the values among 1 or EAD, 2 or macip, 3 or multicast, 4 or es, 5 or prefix.
- `json` : To get output in JavaScript Object Notation

**Command mode** : Exec mode

**Usage** : Use route-type filter to get a specific route type information.

**Click command** : `None`

**Example**
```
sonic# show bgp l2vpn evpn route
BGP table version is 350, local router ID is 2.2.2.2
Status codes: s suppressed, d damped, h history, * valid, > best, i - internal
Origin codes: i - IGP, e - EGP, ? - incomplete
EVPN type-1 prefix: [1]:[ESI]:[EthTag]:[IPlen]:[VTEP-IP]
EVPN type-2 prefix: [2]:[EthTag]:[MAClen]:[MAC]:[IPlen]:[IP]
EVPN type-3 prefix: [3]:[EthTag]:[IPlen]:[OrigIP]
EVPN type-4 prefix: [4]:[ESI]:[IPlen]:[OrigIP]
EVPN type-5 prefix: [5]:[EthTag]:[IPlen]:[IP]

   Network          Next Hop            Metric LocPrf Weight Path
                    Extended Community
Route Distinguisher: 2.2.2.2:2
*> [2]:[0]:[48]:[00:00:01:10:01:01]
                    2.2.2.2                            32768 i
                    ET:8 RT:65100:100010
*> [2]:[0]:[48]:[00:00:01:10:01:02]
                    2.2.2.2                            32768 i
                    ET:8 RT:65100:100010
*> [3]:[0]:[32]:[2.2.2.2]
                    2.2.2.2                            32768 i
                    ET:8 RT:65100:100010
Route Distinguisher: 2.2.2.2:3
*> [3]:[0]:[32]:[2.2.2.2]
                    2.2.2.2                            32768 i
                    ET:8 RT:65100:100020
Route Distinguisher: 3.3.3.3:2
*>i[3]:[0]:[32]:[3.3.3.3]
                    3.3.3.3                       100      0 i
                    RT:65100:100010 ET:8

Displayed 5 prefixes (5 paths)

sonic#
```

##### Show bgp l2vpn evpn route detail
Displays BGP EVPN route detailed information.

**Syntax**: `show bgp l2vpn evpn route detail [type <route-type> [json]] | [json]`

**Parameters** :
- `route-type` : Type of the route queried.
                 It can any one of the values among 1 or EAD, 2 or macip, 3 or multicast, 4 or es, 5 or prefix.
- `json` : To get output in JavaScript Object Notation

**Command mode** : Exec mode

**Usage** : Use route-type filter to get a specific route type information.

**Click command** : `None`

**Example**
```
sonic# show bgp l2vpn evpn route detail
BGP routing table entry for 2.2.2.2:2:[2]:[0]:[48]:[00:00:00:00:00:00]
Paths: (0 available, no best path)
  Not advertised to any peer
BGP routing table entry for 2.2.2.2:2:[2]:[0]:[48]:[00:00:01:10:01:00]
Paths: (0 available, no best path)
  Not advertised to any peer
Route Distinguisher: 2.2.2.2:2
BGP routing table entry for 2.2.2.2:2:[2]:[0]:[48]:[00:00:01:10:01:01]
Paths: (1 available, best #1)
  Advertised to non peer-group peers:
  30.1.1.2
  Route [2]:[0]:[48]:[00:00:01:10:01:01] VNI 100010
  Local
    2.2.2.2 from 0.0.0.0 (2.2.2.2)
      Origin IGP, weight 32768, valid, sourced, local, best (First path received)
      Extended Community: ET:8 RT:65100:100010
      Last update: Fri Nov 17 12:14:17 2023
BGP routing table entry for 2.2.2.2:2:[2]:[0]:[48]:[00:00:01:10:01:02]
Paths: (1 available, best #1)
  Advertised to non peer-group peers:
  30.1.1.2
  Route [2]:[0]:[48]:[00:00:01:10:01:02] VNI 100010
  Local
    2.2.2.2 from 0.0.0.0 (2.2.2.2)
      Origin IGP, weight 32768, valid, sourced, local, best (First path received)
      Extended Community: ET:8 RT:65100:100010
      Last update: Fri Nov 17 12:14:17 2023
BGP routing table entry for 2.2.2.2:2:[3]:[0]:[32]:[2.2.2.2]
Paths: (1 available, best #1)
  Advertised to non peer-group peers:
  30.1.1.2
  Route [3]:[0]:[32]:[2.2.2.2] VNI 100010
  Local
    2.2.2.2 from 0.0.0.0 (2.2.2.2)
      Origin IGP, weight 32768, valid, sourced, local, best (First path received)
      Extended Community: ET:8 RT:65100:100010
      Last update: Thu Nov 16 15:03:57 2023
      PMSI Tunnel Type: Ingress Replication, label: 100010
Route Distinguisher: 2.2.2.2:3
BGP routing table entry for 2.2.2.2:3:[3]:[0]:[32]:[2.2.2.2]
Paths: (1 available, best #1)
  Advertised to non peer-group peers:
  30.1.1.2
  Route [3]:[0]:[32]:[2.2.2.2] VNI 100020
  Local
    2.2.2.2 from 0.0.0.0 (2.2.2.2)
      Origin IGP, weight 32768, valid, sourced, local, best (First path received)
      Extended Community: ET:8 RT:65100:100020
      Last update: Fri Nov 17 12:08:30 2023
      PMSI Tunnel Type: Ingress Replication, label: 100020
Route Distinguisher: 3.3.3.3:2
BGP routing table entry for 3.3.3.3:2:[3]:[0]:[32]:[3.3.3.3]
Paths: (1 available, best #1)
  Not advertised to any peer
  Local
    3.3.3.3 from 30.1.1.2 (3.3.3.3)
      Origin IGP, localpref 100, valid, internal, best (First path received)
      Extended Community: RT:65100:100010 ET:8
      Last update: Thu Nov 16 15:04:15 2023
      PMSI Tunnel Type: Ingress Replication, label: 100010

Displayed 5 prefixes (5 paths)

sonic#
```

##### Show bgp l2vpn evpn route vni
Displays BGP EVPN VNI specific route information with filters such as vtep-ip, mac, mac and ip, source router ip, route type etc,.

**Syntax**: `show bgp l2vpn evpn route [vni <vnid> [mac <mac-address> [ip <ip-address>]]|[multicast <src-router-ip>]|[type <route-type>]|[vtep <vtep-ip>][json]]|[vni all [vtep <vtep-ip>][json]]`

**Parameters** :
- `vnid` : VNI number and its range is 1..16777215.
- `mac-address` : Mac address to be filtered in format xx:xx:xx:xx:xx.
- `ip-address` : IP address learned as part of type-2 route in format A:B:C:D.
- `src-router-ip` : Originating Router IP address(A:B:C:D).
- `route-type` : Type of the route queried.
                 It can any one of the values among 1 or EAD, 2 or macip, 3 or multicast.
- `vtep-ip` : Remote VTEP IP address(A:B:C:D).
- `json` : To get output in JavaScript Object Notation

**Command mode** : Exec mode

**Usage** : Use different filters to get more granular output available in both all vni and specific vni subcommands.

**Click command** : `None`

**Example**
```
1)sonic# show bgp l2vpn evpn route vni 100010
BGP table version is 309, local router ID is 2.2.2.2
Status codes: s suppressed, d damped, h history, * valid, > best, i - internal
Origin codes: i - IGP, e - EGP, ? - incomplete
EVPN type-1 prefix: [1]:[ESI]:[EthTag]:[IPlen]:[VTEP-IP]
EVPN type-2 prefix: [2]:[EthTag]:[MAClen]:[MAC]:[IPlen]:[IP]
EVPN type-3 prefix: [3]:[EthTag]:[IPlen]:[OrigIP]
EVPN type-4 prefix: [4]:[ESI]:[IPlen]:[OrigIP]
EVPN type-5 prefix: [5]:[EthTag]:[IPlen]:[IP]

   Network          Next Hop            Metric LocPrf Weight Path
*> [2]:[0]:[48]:[00:00:01:10:01:01]
                    2.2.2.2                            32768 i
                    ET:8 RT:65100:100010
*> [2]:[0]:[48]:[00:00:01:10:01:02]
                    2.2.2.2                            32768 i
                    ET:8 RT:65100:100010
*> [3]:[0]:[32]:[2.2.2.2]
                    2.2.2.2                            32768 i
                    ET:8 RT:65100:100010
*>i[3]:[0]:[32]:[3.3.3.3]
                    3.3.3.3                       100      0 i
                    RT:65100:100010 ET:8

Displayed 4 prefixes (4 paths)
sonic#

2)sonic# show bgp l2vpn evpn route vni 100010 mac 00:00:01:10:01:01
BGP routing table entry for [2]:[0]:[48]:[00:00:01:10:01:01]
Paths: (1 available, best #1)
  Not advertised to any peer
  Route [2]:[0]:[48]:[00:00:01:10:01:01] VNI 100010
  Local
    2.2.2.2 from 0.0.0.0 (2.2.2.2)
      Origin IGP, weight 32768, valid, sourced, local, best (First path received)
      Extended Community: ET:8 RT:65100:100010
      Last update: Fri Nov 17 15:26:15 2023

Displayed 1 paths for requested prefix
sonic#

3)sonic# show bgp l2vpn evpn route vni all

VNI: 100020

BGP table version is 1, local router ID is 2.2.2.2
Status codes: s suppressed, d damped, h history, * valid, > best, i - internal
Origin codes: i - IGP, e - EGP, ? - incomplete
EVPN type-1 prefix: [1]:[ESI]:[EthTag]:[IPlen]:[VTEP-IP]
EVPN type-2 prefix: [2]:[EthTag]:[MAClen]:[MAC]:[IPlen]:[IP]
EVPN type-3 prefix: [3]:[EthTag]:[IPlen]:[OrigIP]
EVPN type-4 prefix: [4]:[ESI]:[IPlen]:[OrigIP]
EVPN type-5 prefix: [5]:[EthTag]:[IPlen]:[IP]

   Network          Next Hop            Metric LocPrf Weight Path
*> [3]:[0]:[32]:[2.2.2.2]
                    2.2.2.2                            32768 i
                    ET:8 RT:65100:100020

Displayed 1 prefixes (1 paths)


VNI: 100010

BGP table version is 383, local router ID is 2.2.2.2
Status codes: s suppressed, d damped, h history, * valid, > best, i - internal
Origin codes: i - IGP, e - EGP, ? - incomplete
EVPN type-1 prefix: [1]:[ESI]:[EthTag]:[IPlen]:[VTEP-IP]
EVPN type-2 prefix: [2]:[EthTag]:[MAClen]:[MAC]:[IPlen]:[IP]
EVPN type-3 prefix: [3]:[EthTag]:[IPlen]:[OrigIP]
EVPN type-4 prefix: [4]:[ESI]:[IPlen]:[OrigIP]
EVPN type-5 prefix: [5]:[EthTag]:[IPlen]:[IP]

   Network          Next Hop            Metric LocPrf Weight Path
*> [2]:[0]:[48]:[00:00:01:10:01:01]
                    2.2.2.2                            32768 i
                    ET:8 RT:65100:100010
*> [2]:[0]:[48]:[00:00:01:10:01:02]
                    2.2.2.2                            32768 i
                    ET:8 RT:65100:100010
*> [3]:[0]:[32]:[2.2.2.2]
                    2.2.2.2                            32768 i
                    ET:8 RT:65100:100010
*>i[3]:[0]:[32]:[3.3.3.3]
                    3.3.3.3                       100      0 i
                    RT:65100:100010 ET:8

Displayed 4 prefixes (4 paths)

sonic#
```

##### Show bgp l2vpn evpn statistics
Displays BGP RIB advertisement statistics

**Syntax**: `show bgp l2vpn evpn [statistics [json]]`

**Parameters** :
- `json` : To get output in JavaScript Object Notation

**Command mode** : Exec mode

**Usage** : Use 'json' option to get output in json format.

**Click command** : `None`

**Example**
```
sonic# show bgp l2vpn evpn statistics
BGP L2VPN EVPN RIB statistics (VRF default)
Total Advertisements          :            5
Total Prefixes                :            5
Average prefix length         :       320.00
Unaggregateable prefixes      :            5
Maximum aggregateable prefixes:            0
BGP Aggregate advertisements  :            0
Address space advertised      :            5
                  % announced :         0.00
                /8 equivalent :         0.00
               /24 equivalent :         0.02

Advertisements with paths     :            5
Longest AS-Path (hops)        :            0
Average AS-Path length (hops) :         0.00
Largest AS-Path (bytes)       :            0
Average AS-Path size (bytes)  :         0.00
Highest public ASN            :            0

sonic#
```

##### Show bgp l2vpn evpn summary
Display summary of BGP neighbor status

**Syntax**: `show bgp l2vpn evpn [summary [json]]`

**Parameters** :
- `json` : To get output in JavaScript Object Notation

**Command mode** : Exec mode

**Usage** : Use 'json' option to get output in json format.

**Click command** : `None`

**Example**
```
sonic# show bgp l2vpn evpn summary
BGP router identifier 2.2.2.2, local AS number 65100 vrf-id 0
BGP table version 0
RIB entries 5, using 960 bytes of memory
Peers 1, using 21 KiB of memory

Neighbor        V         AS   MsgRcvd   MsgSent   TblVer  InQ OutQ  Up/Down State/PfxRcd   PfxSnt
30.1.1.2        4      65100      1487      1656        0    0    0 1d00h37m            1        4

Total number of neighbors 1

sonic#
```

##### Show bgp l2vpn evpn update-groups
Display detailed information about dynamic update groups.

**Syntax**: `show bgp l2vpn evpn [update-groups]`

**Command mode** : Exec mode

**Usage** : Use this command to get information specific to dynamic groups.

**Click command** : `None`

**Example**
```
sonic# show bgp l2vpn evpn update-groups
Update-group 3:
  Created: Thu Nov 16 15:01:31 2023
  MRAI value (seconds): 0

  Update-subgroup 3:
    Created: Thu Nov 16 15:01:31 2023
    Join events: 1
    Prune events: 0
    Merge events: 0
    Split events: 0
    Update group switch events: 0
    Peer refreshes combined: 0
    Merge checks triggered: 0
    Coalesce Time: 1100
    Version: 430
    Packet queue length: 0
    Total packets enqueued: 169
    Packet queue high watermark: 1
    Adj-out list count: 4
    Advertise list: empty
    Flags:
    Peers:
      - 30.1.1.2
sonic#
```

##### Show bgp l2vpn evpn vni
Display VNI specific information.

**Syntax**: `show bgp l2vpn evpn [vni <vnid>[json]]`

**Parameters** :
- `vnid` : VNI number and its range is 1..16777215.
- `json` : To get output in JavaScript Object Notation

**Command mode** : Exec mode

**Usage** : Use 'json' option to get output in json format.

**Click command** : `None`

**Example**
```
sonic# show bgp l2vpn evpn vni 100010
VNI: 100010 (known to the kernel)
  Type: L2
  Tenant-Vrf: default
  RD: 2.2.2.2:2
  Originator IP: 2.2.2.2
  Mcast group: 0.0.0.0
  Advertise-gw-macip : Disabled
  Advertise-svi-macip : Disabled
  Import Route Target:
    65100:100010
  Export Route Target:
    65100:100010

sonic#
sonic# show bgp l2vpn evpn vni 100020
VNI: 100020 (known to the kernel)
  Type: L2
  Tenant-Vrf: default
  RD: 2.2.2.2:3
  Originator IP: 2.2.2.2
  Mcast group: 0.0.0.0
  Advertise-gw-macip : Disabled
  Advertise-svi-macip : Disabled
  Import Route Target:
    65100:100020
  Export Route Target:
    65100:100020

sonic#
```

### VxLAN Clear commands
#### Clear vxlan counters
Clears VxLAN tunnels' counters information. Tunnel flex-counters need to be enabled by using 'counterpoll tunnel enable' CLICK command.

**Syntax**: `clear vxlan counters`

**Command mode** : Exec mode

**Usage** : Use this command to clear all vxlan tunnels' counters information.

**Click command** : `sonic-clear tunnelcounters`

**Example**
```
sonic# clear vxlan counters
```

## Layer 3
## OSPF
### OSPF Config commands
#### router ospf
Enables a OSPF protocol process.

**Syntax**: `router ospf [ <instance-id> [vrf <vrfname>] | vrf <vrfname> ]`

**Parameters**  :
- `instance-id` - OSPF Instance ID (1-65535)
- `vrfname`     - VRF Name (Max: 15 characters, prefixed with Vrf)

**Command mode** : CONFIG

**Usage**       : Use `no router ospf [ <instance-id> [vrf <vrfname>] | vrf <vrfname> ]` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config)# router ospf
  <1..65535>  Instance ID
  vrf         Specify the VRF
  <cr>
sonic(config)# router ospf 1
  vrf   Specify the VRF
  <cr>
sonic(config)# router ospf 1 vrf Vrf-1
sonic(config)# router ospf vrf Vrf-1
sonic(config)# no router ospf
  <1..65535>  Instance ID
  vrf         Specify the VRF
  <cr>
sonic(config)# no router ospf 1
  vrf   Specify the VRF
  <cr>
sonic(config)# no router ospf 1 vrf Vrf-1
sonic(config)# no router ospf vrf Vrf-1
```

#### Aggregation command
Sets external route aggregation delay timer.

**Syntax**: `aggregation timer <interval>`

**Parameters**  :
- `interval` - Delay timer interval in seconds (5-1800)

**Command mode** : Router OSPF mode

**Usage**       : Use `no aggregation timer` to remove the configuration.

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
sonic(config-router)# aggregation timer 5
sonic(config-router)# no aggregation timer
```

#### Area commands
##### Authentication
Configures OSPF Area authentication.

**Syntax**: `area <A.B.C.D|area-id> authentication`

**Parameters**  :
- `A.B.C.D` - OSPF area ID in IP address format
- `area-id` - OSPF area ID as a decimal value (0-4294967295)

**Command mode** : Router OSPF mode

**Usage**       : Use `no area <A.B.C.D|area-id> authentication` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# area 1 authentication
sonic(config-router)# area 1 authentication message-digest
sonic(config-router)# no area 1 authentication
sonic(config-router)# no area 1 authentication message-digest
sonic(config-router)#
sonic(config-router)# area 10.1.1.1 authentication
sonic(config-router)# area 10.1.1.1 authentication message-digest
sonic(config-router)# no area 10.1.1.1 authentication
sonic(config-router)# no area 10.1.1.1 authentication message-digest
```

##### Default-Cost
Sets the summary-default cost of a NSSA or stub area.

**Syntax**: `area <A.B.C.D|area-id> default-cost <cost-id>`

**Parameters**  :
- `A.B.C.D` - OSPF area ID in IP address format
- `area-id` - OSPF area ID as a decimal value (0-4294967295)
- `cost-id` - Stub's advertised default summary cost (0-16777215)

**Command mode** : Router OSPF mode

**Usage**       : Use `no area <A.B.C.D|area-id> default-cost <cost-id>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# area 1 default-cost 5
sonic(config-router)# no area 1 default-cost 5
sonic(config-router)#
sonic(config-router)# area 10.1.1.1 default-cost 5
sonic(config-router)# no area 10.1.1.1 default-cost 5
```

##### Export-list
Sets the filter for networks announced to other areas.

**Syntax**: `area <A.B.C.D|area-id> export-list <NAME>`

**Parameters**  :
- `A.B.C.D` - OSPF area ID in IP address format
- `area-id` - OSPF area ID as a decimal value (0-4294967295)
- `NAME`    - Name of the access-list

**Command mode** : Router OSPF mode

**Usage**       : Use `no area <A.B.C.D|area-id> export-list <NAME>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# area 1 export-list explist
sonic(config-router)# no area 1 export-list explist
sonic(config-router)#
sonic(config-router)# area 10.1.1.1 export-list explist
sonic(config-router)# no area 10.1.1.1 export-list explist
```

##### Filter-list
Filters networks between OSPF areas.

**Syntax**: `area <A.B.C.D|area-id> filter-list prefix <NAME> in|out`

**Parameters**  :
- `A.B.C.D` - OSPF area ID in IP address format
- `area-id` - OSPF area ID as a decimal value (0-4294967295)
- `NAME`    - Name of an IP prefix-list

**Command mode** : Router OSPF mode

**Usage**       : Use `no area <A.B.C.D|area-id> filter-list prefix <NAME> in|out` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# area 1 filter-list prefix prflist in
sonic(config-router)# area 1 filter-list prefix prflist out
sonic(config-router)# no area 1 filter-list prefix prflist in
sonic(config-router)# no area 1 filter-list prefix prflist out
sonic(config-router)#
sonic(config-router)# area 10.1.1.1 filter-list prefix prflist in
sonic(config-router)# area 10.1.1.1 filter-list prefix prflist out
sonic(config-router)# no area 10.1.1.1 filter-list prefix prflist in
sonic(config-router)# no area 10.1.1.1 filter-list prefix prflist out
```

##### Import-list
Sets the filter for networks from other areas announced to the specified one.

**Syntax**: `area <A.B.C.D|area-id> import-list <NAME>`

**Parameters**  :
- `A.B.C.D` - OSPF area ID in IP address format
- `area-id` - OSPF area ID as a decimal value (0-4294967295)
- `NAME`    - Name of the access-list

**Command mode** : Router OSPF mode

**Usage**       : Use `no area <A.B.C.D|area-id> import-list <NAME>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# area 1 import-list implist
sonic(config-router)# no area 1 import-list implist
sonic(config-router)#
sonic(config-router)# area 10.1.1.1 import-list implist
sonic(config-router)# no area 10.1.1.1 import-list implist
```

##### NSSA
Configures OSPF area as nssa.

**Syntax**: `area <A.B.C.D|area-id> nssa [translate-candidate|translate-never|translate-always|no-summary]`

**Parameters**  :
- `A.B.C.D` - OSPF area ID in IP address format
- `area-id` - OSPF area ID as a decimal value (0-4294967295)

**Command mode** : Router OSPF mode

**Usage**       : Use `no area <A.B.C.D|area-id> nssa [translate-candidate|translate-never|translate-always|no-summary]` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# area 1 nssa
sonic(config-router)# area 1 nssa no-summary
sonic(config-router)# area 1 nssa translate-never
sonic(config-router)# area 1 nssa translate-always
sonic(config-router)# area 1 nssa translate-candidate
sonic(config-router)# no area 1 nssa no-summary
sonic(config-router)# no area 1 nssa translate-never
sonic(config-router)# no area 1 nssa translate-always
sonic(config-router)# no area 1 nssa translate-candidate
sonic(config-router)# no area 1 nssa
sonic(config-router)#
sonic(config-router)# area 10.1.1.1 nssa
sonic(config-router)# area 10.1.1.1 nssa no-summary
sonic(config-router)# area 10.1.1.1 nssa translate-never
sonic(config-router)# area 10.1.1.1 nssa translate-always
sonic(config-router)# area 10.1.1.1 nssa translate-candidate
sonic(config-router)# no area 10.1.1.1 nssa no-summary
sonic(config-router)# no area 10.1.1.1 nssa translate-never
sonic(config-router)# no area 10.1.1.1 nssa translate-always
sonic(config-router)# no area 10.1.1.1 nssa translate-candidate
sonic(config-router)# no area 10.1.1.1 nssa
```

##### NSSA suppress-fa
Suppress forwarding address in nssa

**Syntax**: `area <A.B.C.D|area-id> nssa [suppress-fa]`

**Parameters**  :
- `A.B.C.D` - OSPF area ID in IP address format
- `area-id` - OSPF area ID as a decimal value (0-4294967295)

**Command mode** : Router OSPF mode

**Usage**       : Use `no area <A.B.C.D|area-id> nssa [suppress-fa]` to remove the configuration.

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
sonic(config-router)# area 1 nssa suppress-fa
sonic(config-router)# no area 1 nssa suppress-fa
```

##### Address Range
Summarizes routes matching address/mask (border routers only).

**Syntax**: `area <A.B.C.D|area-id> range [advertise [cost <cost-id>]|cost <cost-id>|not-advertise|substitute <A.B.C.D/M>]`

**Parameters**  :
- `A.B.C.D` - OSPF area ID in IP address format
- `area-id` - OSPF area ID as a decimal value (0-4294967295)
- `cost-id` - Advertised metric for this range (0-16777215)
- `A.B.C.D/M` - Network prefix to be announced instead of range

**Command mode** : Router OSPF mode

**Usage**       : Use `no area <A.B.C.D|area-id> range [advertise [cost <cost-id>]|cost <cost-id>|not-advertise|substitute <A.B.C.D/M>]`
                  to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# area 1 range 10.1.1.2/24
sonic(config-router)# area 1 range 10.1.1.2/24 advertise
sonic(config-router)# area 1 range 10.1.1.2/24 advertise cost 1
sonic(config-router)# area 1 range 10.1.1.2/24 cost 5
sonic(config-router)# area 1 range 10.1.1.2/24 not-advertise
sonic(config-router)# area 1 range 10.1.1.2/24 substitute
sonic(config-router)# area 1 range 10.1.1.2/24 substitute 11.1.1.1/24
sonic(config-router)# no area 1 range 10.1.1.2/24 advertise
sonic(config-router)# no area 1 range 10.1.1.2/24 advertise cost 1
sonic(config-router)# no area 1 range 10.1.1.2/24 cost 5
sonic(config-router)# no area 1 range 10.1.1.2/24 not-advertise
sonic(config-router)# no area 1 range 10.1.1.2/24 substitute
sonic(config-router)# no area 1 range 10.1.1.2/24 substitute 11.1.1.1/24
sonic(config-router)# no area 1 range 10.1.1.2/24
sonic(config-router)#
sonic(config-router)# area 10.1.1.1/24 range 10.1.1.2/24
sonic(config-router)# area 10.1.1.1/24 range 10.1.1.2/24 advertise
sonic(config-router)# area 10.1.1.1/24 range 10.1.1.2/24 advertise cost 1
sonic(config-router)# area 10.1.1.1/24 range 10.1.1.2/24 cost 5
sonic(config-router)# area 10.1.1.1/24 range 10.1.1.2/24 not-advertise
sonic(config-router)# area 10.1.1.1/24 range 10.1.1.2/24 substitute
sonic(config-router)# area 10.1.1.1/24 range 10.1.1.2/24 substitute 11.1.1.1/24
sonic(config-router)# no area 10.1.1.1/24 range 10.1.1.2/24 advertise
sonic(config-router)# no area 10.1.1.1/24 range 10.1.1.2/24 advertise cost 1
sonic(config-router)# no area 10.1.1.1/24 range 10.1.1.2/24 cost 5
sonic(config-router)# no area 10.1.1.1/24 range 10.1.1.2/24 not-advertise
sonic(config-router)# no area 10.1.1.1/24 range 10.1.1.2/24 substitute
sonic(config-router)# no area 10.1.1.1/24 range 10.1.1.2/24 substitute 11.1.1.1/24
sonic(config-router)# no area 10.1.1.1/24 range 10.1.1.2/24
```

##### Shortcut
Configures the area's shortcutting mode.

**Syntax**: `area <A.B.C.D|area-id> shortcut default|enable|disable`

**Parameters**  :
- `A.B.C.D` - OSPF area ID in IP address format
- `area-id` - OSPF area ID as a decimal value (0-4294967295)

**Command mode** : Router OSPF mode

**Usage**       : Use `no area <A.B.C.D|area-id> shortcut default|enable|disable` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# area 1 shortcut default
sonic(config-router)# area 1 shortcut disable
sonic(config-router)# area 1 shortcut enable
sonic(config-router)# no area 1 shortcut default
sonic(config-router)# no area 1 shortcut disable
sonic(config-router)# no area 1 shortcut enable
sonic(config-router)#
sonic(config-router)# area 10.1.1.1/24 shortcut default
sonic(config-router)# area 10.1.1.1/24 shortcut disable
sonic(config-router)# area 10.1.1.1/24 shortcut enable
sonic(config-router)# no area 10.1.1.1/24 shortcut default
sonic(config-router)# no area 10.1.1.1/24 shortcut disable
sonic(config-router)# no area 10.1.1.1/24 shortcut enable
```

##### Stub
Configures OSPF area as stub.

**Syntax**: `area <A.B.C.D|area-id> stub [no-summary]`

**Parameters**  :
- `A.B.C.D` - OSPF area ID in IP address format
- `area-id` - OSPF area ID as a decimal value (0-4294967295)

**Command mode** : Router OSPF mode

**Usage**       : Use `no area <A.B.C.D|area-id> stub [no-summary]` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# area 1 stub
sonic(config-router)# area 1 stub no-summary
sonic(config-router)# no area 1 stub no-summary
sonic(config-router)# no area 1 stub
sonic(config-router)#
sonic(config-router)# area 10.1.1.1/24 stub
sonic(config-router)# area 10.1.1.1/24 stub no-summary
sonic(config-router)# no area 10.1.1.1/24 stub no-summary
sonic(config-router)# no area 10.1.1.1/24 stub
```

##### Virtual link
Configures a virtual link.

**Syntax**: `area <A.B.C.D|area-id> virtual-link <A.B.C.D> [authentication [<message-digest|null>]|message-digest-key <key-id> md5 <KEY>|authentication-key <KEY>|hello-interval (1-65535)|retransmit-interval (1-65535)|transmit-delay (1-65535)|dead-interval (1-65535)]`

**Parameters**  :
- `A.B.C.D`    - OSPF area ID in IP address format
- `area-id`    - OSPF area ID as a decimal value (0-4294967295)
- `key-id`     - Message digest key id (1-255)
- `KEY`        - The OSPF password (key)
- `hinterval`  - Hello interval in seconds (1-65535)
- `dinterval`  - Dead interval in seconds (1-65535)
- `rtinterval` - Retransmit interval in seconds (1-65535)
- `transdelay` - transmit delay in seconds (1-65535)

**Command mode** : Router OSPF mode

**Usage**       : Use `no area <A.B.C.D|area-id> virtual-link <A.B.C.D> [authentication [<message-digest|null>]|message-digest-key <key-id> md5 <KEY>|authentication-key <AUTH_KEY>|hello-interval (1-65535)|retransmit-interval (1-65535)|transmit-delay (1-65535)|dead-interval (1-65535)]` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# area 1 virtual-link 1.1.1.1 authentication
sonic(config-router)# area 1 virtual-link 1.1.1.1 authentication null
sonic(config-router)# area 1 virtual-link 1.1.1.1 authentication message-digest
sonic(config-router)# area 1 virtual-link 1.1.1.1 authentication-key key1
sonic(config-router)# area 1 virtual-link 1.1.1.1 message-digest-key 1 md5 key2
sonic(config-router)# area 1 virtual-link 1.1.1.1 dead-interval 2
sonic(config-router)# area 1 virtual-link 1.1.1.1 hello-interval 1
sonic(config-router)# area 1 virtual-link 1.1.1.1 retransmit-interval 3
sonic(config-router)# area 1 virtual-link 1.1.1.1 transmit-delay 1
sonic(config-router)#
sonic(config-router)# area 10.1.1.1/24 virtual-link 1.1.1.1 authentication
sonic(config-router)# area 10.1.1.1/24 virtual-link 1.1.1.1 authentication null
sonic(config-router)# area 10.1.1.1/24 virtual-link 1.1.1.1 authentication message-digest
sonic(config-router)# area 10.1.1.1/24 virtual-link 1.1.1.1 authentication-key key1
sonic(config-router)# area 10.1.1.1/24 virtual-link 1.1.1.1 message-digest-key 1 md5 key2
sonic(config-router)# area 10.1.1.1/24 virtual-link 1.1.1.1 dead-interval 2
sonic(config-router)# area 10.1.1.1/24 virtual-link 1.1.1.1 hello-interval 1
sonic(config-router)# area 10.1.1.1/24 virtual-link 1.1.1.1 retransmit-interval 3
sonic(config-router)# area 10.1.1.1/24 virtual-link 1.1.1.1 transmit-delay 1
```

#### Auto-Cost command
Calculates OSPF interface cost according to bandwidth.

**Syntax**: `auto-cost reference-bandwidth <bandwidth>`

**Parameters**  :
- `bandwidth` - The reference bandwidth in terms of Mbits per second (1-4294967)

**Command mode** : Router OSPF mode

**Usage**       : Use `no auto-cost reference-bandwidth <bandwidth>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# auto-cost reference-bandwidth 4
sonic(config-router)# no auto-cost reference-bandwidth 4
```

#### Capability command
Enables OSPF capability opaque.

**Syntax**: `capability opaque`

**Parameters**  : None

**Command mode** : Router OSPF mode

**Usage**       : Use `no capability opaque` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# capability opaque
sonic(config-router)# no capability opaque
```

#### Compatible command
OSPF compatibility list.

**Syntax**: `compatible rfc1583`

**Parameters**  : None

**Command mode** : Router OSPF mode

**Usage**       : Use `no compatible rfc1583` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# compatible rfc1583
sonic(config-router)# no compatible rfc1583
```

#### Default-Information command
Control distribution of default information.

**Syntax**: `default-information originate [{always|metric <metric>|metric-type <type>|route-map <rmap>}]`

**Parameters**  :
- `metric` - OSPF metric (0-16777214)
- `type`   - Set OSPF External Type 1/2 metrics (1-2)
- `rmap`   - Pointer to route-map entries

**Command mode** : Router OSPF mode

**Usage**       : Use `no default-information originate [{always|metric <metric>|metric-type <type>|route-map <rmap>}]` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# default-information originate
sonic(config-router)# default-information originate always metric 1 metric-type 2 route-map rmap1
sonic(config-router)# no default-information originate always metric 1 metric-type 2 route-map rmap1
sonic(config-router)# no default-information originate
```

#### Default-Metric command
Sets metric of redistributed routes.

**Syntax**: `default-metric <metric>`

**Parameters**  :
- `metric` - Default metric (0-16777214)

**Command mode** : Router OSPF mode

**Usage**       : Use `no default-metric <metric>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# default-metric 10
sonic(config-router)# no default-metric 10
```

#### Distance command
##### Administrative distance.

**Syntax**: `distance <dist>`

**Parameters**  :
- `dist` - OSPF Administrative distance (1-255)

**Command mode** : Router OSPF mode

**Usage**       : Use `no distance <dist>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# distance 1
sonic(config-router)# no distance 1
```

##### Administrative distance for intra-area, inter-area and external routes.

**Syntax**: `distance ospf {intra-area <intra>|inter-area <inter>)|external <ext>}`

**Parameters**  :
- `intra` - Distance for intra-area routes (1-255)
- `inter` - Distance for inter-area routes (1-255)
- `ext`   - Distance for external routes (1-255)

**Command mode** : Router OSPF mode

**Usage**       : Use `no distance ospf {intra-area <intra>|inter-area <inter>)|external <ext>}` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# distance ospf external 1 inter-area 2 intra-area 3
sonic(config-router)# no distance ospf external 1 inter-area 2 intra-area 3
```

#### Distribute-list command
Filters networks in routing updates.

**Syntax**: `distribute-list <NAME> out kernel|connected|static|rip|isis|bgp|eigrp|nhrp|table|vnc|babel|sharp|openfabric`

**Parameters**  :
- `NAME` - Access-list name

**Command mode** : Router OSPF mode

**Usage**       : Use `no distribute-list <NAME> out kernel|connected|static|rip|isis|bgp|eigrp|nhrp|table|vnc|babel|sharp|openfabric`
                  to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# distribute-list dlist out babel
sonic(config-router)# distribute-list dlist out bgp
sonic(config-router)# distribute-list dlist out connected
sonic(config-router)# distribute-list dlist out eigrp
sonic(config-router)# distribute-list dlist out isis
sonic(config-router)# distribute-list dlist out kernel
sonic(config-router)# distribute-list dlist out nhrp
sonic(config-router)# distribute-list dlist out openfabric
sonic(config-router)# distribute-list dlist out rip
sonic(config-router)# distribute-list dlist out sharp
sonic(config-router)# distribute-list dlist out static
sonic(config-router)# distribute-list dlist out table
sonic(config-router)# distribute-list dlist out vnc
```

#### Fast-reroute command
Fast Reroute for MPLS and IP resilience

**Syntax**: `fast-reroute ti-lfa [node-protection]`

**Parameters**  : None

**Command mode** : Router OSPF mode

**Usage**       : Use `no fast-reroute ti-lfa [node-protection]` to remove the configuration.

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
sonic(config-router)# fast-reroute ti-lfa
sonic(config-router)# fast-reroute ti-lfa node-protection
sonic(config-router)# no fast-reroute ti-lfa node-protection
sonic(config-router)# no fast-reroute ti-lfa
```

#### Graceful Restart prepare command
Command to prepare for upcoming graceful restart.

**Syntax**: `graceful-restart prepare ip ospf`

**Parameters**  : None

**Command mode** : CONFIG

**Usage**       : None

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
sonic(config-router)# graceful-restart prepare ip ospf
```

#### Graceful Restart grace-period command
Sets grace period for graceful restart.

**Syntax**: `graceful-restart [grace-period <num>]`

**Parameters**  :
- `num` - Maximum length of the 'grace period' in seconds (1-1800)

**Command mode** : Router OSPF mode

**Usage**       : Use `no graceful-restart [grace-period <num>]` to remove the configuration.

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
sonic(config-router)# graceful-restart grace-period 10
sonic(config-router)# no graceful-restart grace-period 10
```

#### Graceful Restart helper command

**Syntax**: `graceful-restart [helper planned-only|enable [<A.B.C.D>]|supported-grace-time <interval>|lsa-check-disable]`

**Parameters**  :
- `A.B.C.D`  - Advertising Router-ID
- `interval` - Grace interval in seconds (10-1800)

**Command mode** : Router OSPF mode

**Usage**       : Use `no graceful-restart [helper planned-only|enable [<A.B.C.D>]|supported-grace-time <interval>|strict-lsa-checking]`
                  to remove the configuration.

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
sonic(config-router)# graceful-restart helper enable
sonic(config-router)# graceful-restart helper enable 1.1.1.1
sonic(config-router)# graceful-restart helper planned-only
sonic(config-router)# graceful-restart helper strict-lsa-checking
sonic(config-router)# graceful-restart helper supported-grace-time 10
sonic(config-router)# no graceful-restart helper enable 1.1.1.1
sonic(config-router)# no graceful-restart helper enable
sonic(config-router)# no graceful-restart helper planned-only
sonic(config-router)# no graceful-restart helper strict-lsa-checking
sonic(config-router)# no graceful-restart helper supported-grace-time 10
```

#### Log Adjacency changes command
Log changes in adjacency state.

**Syntax**: `log-adjacency-changes [detail]`

**Parameters**  : None

**Command mode** : Router OSPF mode

**Usage**       : Use `no log-adjacency-changes [detail]` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# log-adjacency-changes
sonic(config-router)# log-adjacency-changes detail
sonic(config-router)# no log-adjacency-changes detail
sonic(config-router)# no log-adjacency-changes
```

#### Max Metric command
OSPF maximum / infinite-distance metric.

**Syntax**: `max-metric router-lsa administrative|on-shutdown <shutdown-time>|on-startup <startup-time>`

**Parameters**  :
- `shutdown-time` - Time (seconds) to wait till full shutdown (5-100)
- `startup-time`  - Time (seconds) to advertise self as stub-router (5-86400)

**Command mode** : Router OSPF mode

**Usage**       : Use `no max-metric router-lsa administrative|on-shutdown <shutdown-time>|on-startup <startup-time>`
                  to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# max-metric router-lsa administrative
sonic(config-router)# max-metric router-lsa on-startup 5
sonic(config-router)# max-metric router-lsa on-shutdown 5
sonic(config-router)# no max-metric router-lsa administrative
sonic(config-router)# no max-metric router-lsa on-startup 5
sonic(config-router)# no max-metric router-lsa on-shutdown 5
```

#### Maximum paths command
Sets maximum number of multiple paths for ECMP support.

**Syntax**: `maximum-paths <num-paths>`

**Parameters**  :
- `num-paths` -  Number of paths (1-256)

**Command mode** : Router OSPF mode

**Usage**       : Use `no maximum-paths` to remove the configuration.

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
sonic(config-router)# maximum-paths 10
sonic(config-router)# no maximum-paths
```

#### Neighbor command
Specify neighbor router.

**Syntax**: `neighbor A.B.C.D [{priority <priority>|poll-interval <poll-interval>}]`

**Parameters**  :
- `A.B.C.D`        - Neighbor IP address
- `priority`       - Neighbor Priority (0-255)
- `poll-interval`  - Dead Neighbor Polling interval in secods (1-65535)

**Command mode** : Router OSPF mode

**Usage**       : Use `no neighbor A.B.C.D [{priority <priority>|poll-interval <poll-interval>}]` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# neighbor 5.5.5.5
sonic(config-router)# neighbor 5.5.5.5 poll-interval 2 priority 2
sonic(config-router)# no neighbor 5.5.5.5 poll-interval 2 priority 2
sonic(config-router)# no neighbor 5.5.5.5
```

#### Network command
Enables routing on an IP network.

**Syntax**: `network A.B.C.D/M area <A.B.C.D|area-id>`

**Parameters**  :
- `A.B.C.D/M` - OSPF network prefix
- `A.B.C.D`   - OSPF area ID in IP address format
- `area-id`   - OSPF area ID as a decimal value (0-4294967295)

**Command mode** : Router OSPF mode

**Usage**       : Use `no network A.B.C.D/M area <A.B.C.D|area-id>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# network 5.5.5.4/24 area 1
sonic(config-router)# network 6.6.6.6/24 area 10.1.1.1
sonic(config-router)# no network 5.5.5.4/24 area 1
sonic(config-router)# no network 6.6.6.6/24 area 10.1.1.1
```

#### OSPF Abr-type command
Sets OSPF ABR type

**Syntax**: `ospf abr-type cisco|ibm|shortcut|standard`

**Parameters**  : None

**Command mode** : Router OSPF mode

**Usage**       : Use `no ospf abr-type cisco|ibm|shortcut|standard` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# ospf abr-type cisco
sonic(config-router)# ospf abr-type ibm
sonic(config-router)# ospf abr-type shortcut
sonic(config-router)# ospf abr-type standard
sonic(config-router)# no ospf abr-type cisco
sonic(config-router)# no ospf abr-type ibm
sonic(config-router)# no ospf abr-type shortcut
sonic(config-router)# no ospf abr-type standard
```

#### OSPF opaque-lsa command
Enables the Opaque-LSA capability (rfc2370).

**Syntax**: `ospf opaque-lsa`

**Parameters**  : None

**Command mode** : Router OSPF mode

**Usage**       : Use `no ospf opaque-lsa` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# ospf opaque-lsa
sonic(config-router)# no ospf opaque-lsa
```

#### OSPF rfc1583compatibility command
Enables the RFC1583Compatibility flag.

**Syntax**: `ospf rfc1583compatibility`

**Parameters**  : None

**Command mode** : Router OSPF mode

**Usage**       : Use `no ospf rfc1583compatibility` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# ospf rfc1583compatibility
sonic(config-router)# no ospf rfc1583compatibility
```

#### OSPF router-id command
Sets router-id for the OSPF process.

**Syntax**: `ospf router-id <A.B.C.D>`

**Parameters**  :
- `A.B.C.D` - OSPF router-id in IP address format

**Command mode** : Router OSPF mode

**Usage**       : Use `no ospf router-id <A.B.C.D>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# ospf router-id 1.1.1.1
sonic(config-router)# no ospf router-id 1.1.1.1
```

#### OSPF send-extra-data command
Extra data to Zebra for display/use

**Syntax**: `ospf send-extra-data zebra`

**Parameters**  : None

**Command mode** : Router OSPF mode

**Usage**       : Use `no ospf send-extra-data zebra` to remove the configuration.

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
sonic(config-router)# ospf send-extra-data zebra
sonic(config-router)# no ospf send-extra-data zebra
```

#### OSPF write-multiplier command
Sets Write Multiplier.

**Syntax**: `ospf write-multiplier <num>`

**Parameters**  :
- `num` - Maximum number of interface serviced per write (1-100)

**Command mode** : Router OSPF mode

**Usage**       : Use `no ospf write-multiplier <num>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# ospf write-multiplier 5
sonic(config-router)# no ospf write-multiplier 5
```

#### Passive interface command
Suppresses routing updates on an interface.

**Syntax**: `passive-interface default`

**Parameters**  : None

**Command mode** : Router OSPF mode

**Usage**       : Use `no passive-interface default` to remove the configuration.

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
sonic(config-router)# passive-interface default
sonic(config-router)# no passive-interface default
```

#### Proactive ARP command
Allows sending ARP requests proactively.

**Syntax**: `proactive-arp`

**Parameters**  : None

**Command mode** : Router OSPF mode

**Usage**       : Use `no proactive-arp` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# proactive-arp
sonic(config-router)# no proactive-arp
```

#### Redistribute command
Redistributes information from another routing protocol.

**Syntax**: `redistribute kernel|connected|static|rip|isis|bgp|eigrp|nhrp|table|vnc|babel|sharp|openfabric|ospf <instance-id> [{metric <metric>|metric-type <type>|route-map <rmap>}]`

**Parameters**  :
- `instance-id` - Instance ID (0-65535)
- `metric`      - OSPF metric (0-16777214)
- `type`        - Set OSPF External Type 1/2 metrics (1-2)
- `rmap`        - Route map reference

**Command mode** : Router OSPF mode

**Usage**       : Use `no redistribute kernel|connected|static|rip|isis|bgp|eigrp|nhrp|table|vnc|babel|sharp|openfabric|ospf <instance-id> [{metric <metric>|metric-type <type>|route-map <rmap>}]` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# redistribute bgp
sonic(config-router)# redistribute bgp metric 1 metric-type 1 route-map rmap1
sonic(config-router)# redistribute connected
sonic(config-router)# redistribute connected metric 1 metric-type 1 route-map rmap1
sonic(config-router)# redistribute eigrp
sonic(config-router)# redistribute eigrp metric 1 metric-type 1 route-map rmap1
sonic(config-router)# redistribute isis
sonic(config-router)# redistribute isis metric 1 metric-type 1 route-map rmap1
sonic(config-router)# redistribute kernel
sonic(config-router)# redistribute kernel metric 1 metric-type 1 route-map rmap1
sonic(config-router)# redistribute nhrp
sonic(config-router)# redistribute nhrp metric 1 metric-type 1 route-map rmap1
sonic(config-router)# redistribute openfabric
sonic(config-router)# redistribute openfabric metric 1 metric-type 1 route-map rmap1
sonic(config-router)# redistribute rip
sonic(config-router)# redistribute rip metric 1 metric-type 1 route-map rmap1
sonic(config-router)# redistribute sharp
sonic(config-router)# redistribute sharp metric 1 metric-type 1 route-map rmap1
sonic(config-router)# redistribute static
sonic(config-router)# redistribute static metric 1 metric-type 1 route-map rmap1
sonic(config-router)# redistribute table
sonic(config-router)# redistribute table metric 1 metric-type 1 route-map rmap1
sonic(config-router)# redistribute vnc
sonic(config-router)# redistribute vnc metric 1 metric-type 1 route-map rmap1
```

#### Refresh command
Adjusts refresh parameters.

**Syntax**: `refresh timer <time>`

**Parameters**  :
- `time` - Timer value in seconds (10-1800)

**Command mode** : Router OSPF mode

**Usage**       : Use `no refresh timer <time>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# refresh timer 10
sonic(config-router)# no refresh timer 10
```

#### Router-info command
OSPF Router Information specific commands.

**Syntax**: `router-info area|as`

**Parameters**  : None

**Command mode** : Router OSPF mode

**Usage**       : Use `no router-info area|as` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# router-info area
sonic(config-router)# router-info as
sonic(config-router)# no router-info
```

#### Summary address command
Sets external summary address prefix.

**Syntax**: `summary-address <A.B.C.D/M> [no-advertise|tag <val>]`

**Parameters**  :
- `A.B.C.D/M` - Summary address prefix
- `val`       - Router tag value (1-4294967295)

**Command mode** : Router OSPF mode

**Usage**       : Use `no summary-address <A.B.C.D/M> [no-advertise|tag <val>]` to remove the configuration.

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
sonic(config-router)# summary-address 192.5.1.1/24
sonic(config-router)# summary-address 192.5.1.1/24 no-advertise
sonic(config-router)# summary-address 192.5.1.1/24 tag 5
sonic(config-router)# no summary-address 192.5.1.1/24 no-advertise
sonic(config-router)# no summary-address 192.5.1.1/24 tag 5
sonic(config-router)# no summary-address 192.5.1.1/24
```

#### Timers command
##### Adjusts OSPF LSA timers.

**Syntax**: `timers lsa min-arrival <delay>`

**Parameters**  :
- `delay` - Delay in milliseconds (0-600000)

**Command mode** : Router OSPF mode

**Usage**       : Use `no timers lsa min-arrival <delay>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# timers lsa min-arrival 1
sonic(config-router)# no timers lsa min-arrival 1
```

##### Adjusts OSPF Throttle lsa timers.

**Syntax**: `timers throttle lsa all <delay>`

**Parameters**  :
- `delay` - Delay (msec) between sending LSAs (0-5000)

**Command mode** : Router OSPF mode

**Usage**       : Use `no timers throttle lsa all <delay>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# timers throttle lsa all 1
sonic(config-router)# no timers throttle lsa all 1
```

##### Adjusts OSPF Throttle spf timers.

**Syntax**: `timers throttle spf <delay> <hold> <maxhold>`

**Parameters**  :
- `delay`   - Delay (msec) from first change received till SPF calculation (0-600000)
- `hold`    - Initial hold time (msec) between consecutive SPF calculations (0-600000)
- `maxhold` - Maximum hold time (msec) (0-600000)

**Command mode** : Router OSPF mode

**Usage**       : Use `no timers throttle spf <delay> <hold> <maxhold>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# timers throttle spf 1 1 1
sonic(config-router)# no timers throttle spf 1 1 1
```

#### Write-Multiplier command

**Syntax**: `write-multiplier <num>`

**Parameters**  :
- `num` - Maximum number of interface serviced per write (1-100)

**Command mode** : Router OSPF mode

**Usage**       : Use `no write-multiplier <num>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-router)# write-multiplier 10
sonic(config-router)# no write-multiplier 10
```

### OSPF Interface commands
#### Area commands
##### OSPF Area with Instance ID
Configures OSPF Interface Area configs.

**Syntax**: `ip ospf <instance-id> area <A.B.C.D|area-id>`

**Parameters**  :
- `instance-id` - OSPF Instance ID (1-65535)
- `A.B.C.D`     - OSPF area ID in IP address format
- `area-id`     - OSPF area ID as a decimal value (0-4294967295)

**Command mode** : Interface modes (Ethernet, PortChannel, VLAN and Loopback)

**Usage**       : Use `no ip ospf <instance-id> area <A.B.C.D|area-id>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
```

##### OSPF Area without Instance ID
**Syntax**: `ip ospf area <A.B.C.D|area-id>`

**Parameters**  :
- `A.B.C.D`     - OSPF area ID in IP address format
- `area-id`     - OSPF area ID as a decimal value (0-4294967295)

**Command mode** : Interface modes (Ethernet, PortChannel, VLAN and Loopback)

**Usage**       : Use `no ip ospf area <A.B.C.D|area-id>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# ip ospf area 1
sonic(conf-if-Ethernet8)# no ip ospf area 1
sonic(conf-if-Ethernet8)# ip ospf area 1.1.1.1
sonic(conf-if-Ethernet8)# no ip ospf area 1.1.1.1
```

#### Authentication command
##### Authentication
Enable authentication on this interface.

**Syntax**: `ip ospf authentication [null|message-digest]`

**Parameters**  : None

**Command mode** : Interface modes (Ethernet, PortChannel, VLAN and Loopback)

**Usage**       : Use `no ip ospf authentication [null|message-digest]` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# ip ospf authentication
sonic(conf-if-Ethernet8)# ip ospf authentication message-digest
sonic(conf-if-Ethernet8)# ip ospf authentication null
sonic(conf-if-Ethernet8)# no ip ospf authentication null
sonic(conf-if-Ethernet8)# no ip ospf authentication message-digest
sonic(conf-if-Ethernet8)# no ip ospf authentication
```

##### Authentication password (key)

**Syntax**: `ip ospf authentication-key <KEY>`

**Parameters**  :
- `KEY`        - The OSPF password (key)

**Command mode** : Interface modes (Ethernet, PortChannel, VLAN and Loopback)

**Usage**       : Use `no ip ospf authentication-key <KEY>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# ip ospf authentication-key key1
sonic(conf-if-Ethernet8)# no ip ospf authentication-key key1
```

##### Message digest authentication password (key)

**Syntax**: `ip ospf message-digest-key <key-id> md5 <KEY>`

**Parameters**  :
- `key-id`     - Message digest key id (1-255)
- `KEY`        - The OSPF password (key)

**Command mode** : Interface modes (Ethernet, PortChannel, VLAN and Loopback)

**Usage**       : Use `no ip ospf message-digest-key <key-id> md5 <KEY>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# ip ospf message-digest-key 1 md5 key2
sonic(conf-if-Ethernet8)# no ip ospf message-digest-key 1 md5 key2
```

#### BFD command
Enables BFD support.

**Syntax**: `ip ospf bfd [profile <NAME>]`

**Parameters**  :
- `NAME` - BFD Profile name

**Command mode** : Interface modes (Ethernet, PortChannel, VLAN and Loopback)

**Usage**       : Use `no ip ospf [profile <profile_name>]` to remove the configuration.

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# ip ospf bfd
sonic(conf-if-Ethernet8)# no ip ospf bfd
sonic(conf-if-Ethernet8)# ip ospf bfd profile bfd1
sonic(conf-if-Ethernet8)# no ip ospf bfd profile bfd1
```

#### Cost command
Sets Interface cost.

**Syntax**: `ip ospf cost <cost-id>`

**Parameters**  :
- `cost-id` - Interface cost (0-65535)

**Command mode** : Interface modes (Ethernet, PortChannel, VLAN and Loopback)

**Usage**       : Use `no ip ospf cost <cost-id>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# ip ospf cost 1
sonic(conf-if-Ethernet8)# no ip ospf cost 1
```

#### Dead Interval command
Interval time after which a neighbor is declared down.

**Syntax**: `ip ospf dead-interval <dinterval>`

**Parameters**  :
- `dinterval` - Delay interval in seconds (1-65535)

**Command mode** : Interface modes (Ethernet, PortChannel, VLAN and Loopback)

**Usage**       : Use `no ip ospf dead-interval <dinterval>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# ip ospf dead-interval 10
sonic(conf-if-Ethernet8)# no ip ospf dead-interval 10
```

##### Hello-multiplier
Delay interval minimal config. Minimal 1s dead-interval with fast sub-second hellos.

**Syntax**: `ip ospf dead-interval minimal hello-multiplier <num>`

**Parameters**  :
- `num` - Number of Hellos to send each second (1-10)

**Command mode** : Interface modes (Ethernet, PortChannel, VLAN and Loopback)

**Usage**       : Use `no ip ospf dead-interval minimal hello-multiplier <num>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# ip ospf dead-interval minimal hello-multiplier 5
sonic(conf-if-Ethernet8)# no ip ospf dead-interval minimal hello-multiplier 5
```

#### Hello Interval command
Time between HELLO packets.

**Syntax**: `ip ospf hello-interval <hinterval>`

**Parameters**  :
- `hinterval` - Hello interval in seconds (1-65535)

**Command mode** : Interface modes (Ethernet, PortChannel, VLAN and Loopback)

**Usage**       : Use `no ip ospf hello-interval <hinterval>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# ip ospf hello-interval 5
sonic(conf-if-Ethernet8)# no ip ospf hello-interval 5
```

#### Retransmit Interval command
Time between retransmitting lost link state advertisements.

**Syntax**: `ip ospf retransmit-interval <rtinterval>`

**Parameters**  :
- `rtinterval` - Retransmit interval in seconds (1-65535)

**Command mode** : Interface modes (Ethernet, PortChannel, VLAN and Loopback)

**Usage**       : Use `no ip ospf retransmit-interval <rtinterval>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# ip ospf retransmit-interval 3
sonic(conf-if-Ethernet8)# no ip ospf retransmit-interval 3
```

#### Transmit delay command
Sets Link state transmit delay.

**Syntax**: `ip ospf transmit-delay <transdelay>`

**Parameters**  :
- `transdelay` - Transmit delay in seconds (1-65535)

**Command mode** : Interface modes (Ethernet, PortChannel, VLAN and Loopback)

**Usage**       : Use `no ip ospf transmit-delay <transdelay>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# ip ospf transmit-delay 4
sonic(conf-if-Ethernet8)# no ip ospf transmit-delay 4
```

#### MTU ignore command
Disables MTU mismatch detection on this interface.

**Syntax**: `ip ospf mtu-ignore`

**Parameters**  : None

**Command mode** : Interface modes (Ethernet, PortChannel, VLAN and Loopback)

**Usage**       : Use `no ip ospf mtu-ignore` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# ip ospf mtu-ignore
sonic(conf-if-Ethernet8)# no ip ospf mtu-ignore
```

#### Network type command
Sets Network Type.

**Syntax**: `ip ospf network broadcast|non-broadcast|point-to-multipoint|point-to-point`

**Parameters**  : None

**Command mode** : Interface modes (Ethernet, PortChannel, VLAN and Loopback)

**Usage**       : Use `no ip ospf network broadcast|non-broadcast|point-to-multipoint|point-to-point` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# ip ospf network broadcast
sonic(conf-if-Ethernet8)# no ip ospf network broadcast
sonic(conf-if-Ethernet8)# ip ospf network point-to-point
sonic(conf-if-Ethernet8)# no ip ospf network point-to-point
```

#### Passive command
Sets Router priority.

**Syntax**: `ip ospf passive`

**Parameters**  : None

**Command mode** : Interface modes (Ethernet, PortChannel, VLAN and Loopback)

**Usage**       : Use `no ip ospf passive` to remove the configuration.

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# ip ospf passive
sonic(conf-if-Ethernet8)# no ip ospf passive
```

#### Priority command
Sets Router priority.

**Syntax**: `ip ospf priority <prio>`

**Parameters**  :
- `prio` - Priority (0-255)

**Command mode** : Interface modes (Ethernet, PortChannel, VLAN and Loopback)

**Usage**       : Use `no ip ospf priority <prio>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# ip ospf priority 2
sonic(conf-if-Ethernet8)# no ip ospf priority 2
```

### OSPF Show commands
#### Show Running-config command
Displays ospf running configs.

**Syntax**: `show running-config ospf`

**Parameters**  : None

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# show running-config ospf
!
frr log syslog
frr log facility local4
!
interface Ethernet 8
 vrf Vrf-20
 ip ospf area 0
!
router ospf vrf Vrf-20
 ospf router-id 10.10.10.2
sonic# show running-config interface Ethernet 8
!
interface Ethernet 8
 fec none
 mtu 9100
 no shutdown
 speed auto
 vrf Vrf-20
 ip address 20.20.20.2/24
 ip ospf area 0
sonic#
```

#### Displays ospf configs.

**Syntax**: `show ip ospf [<instance-id>|vrf <vrfname>|all]`

**Parameters**  :
- `instance-id` - OSPF Instance ID (1-65535)
- `vrfname`     - VRF Name (Max: 15 characters, prefixed with Vrf)

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# show ip ospf
 OSPF Routing Process, Router ID: 10.10.10.2
 Supports only single TOS (TOS0) routes
 This implementation conforms to RFC2328
 RFC1583Compatibility flag is disabled
 OpaqueCapability flag is disabled
 Initial SPF scheduling delay 0 millisec(s)
 Minimum hold time between consecutive SPFs 50 millisec(s)
 Maximum hold time between consecutive SPFs 5000 millisec(s)
 Hold time multiplier is currently 1
 SPF algorithm last executed 4.407s ago
 Last SPF duration 29 usecs
 SPF timer is inactive
 LSA minimum interval 5000 msecs
 LSA minimum arrival 1000 msecs
 Write Multiplier set to 20
 Refresh timer 10 secs
 Number of external LSA 0. Checksum Sum 0x00000000
 Number of opaque AS LSA 0. Checksum Sum 0x00000000
 Number of areas attached to this router: 1
 Area ID: 0.0.0.0 (Backbone)
   Number of interfaces in this area: Total: 1, Active: 1
   Number of fully adjacent neighbors in this area: 1
   Area has no authentication
   SPF algorithm executed 3 times
   Number of LSA 3
   Number of router LSA 2. Checksum Sum 0x00005f03
   Number of network LSA 1. Checksum Sum 0x00001e9e
   Number of summary LSA 0. Checksum Sum 0x00000000
   Number of ASBR summary LSA 0. Checksum Sum 0x00000000
   Number of NSSA LSA 0. Checksum Sum 0x00000000
   Number of opaque link LSA 0. Checksum Sum 0x00000000
   Number of opaque area LSA 0. Checksum Sum 0x00000000

sonic# show ip ospf vrf Vrf-20
VRF Name: Vrf-20
 OSPF Routing Process, Router ID: 10.10.10.2
 Supports only single TOS (TOS0) routes
 This implementation conforms to RFC2328
 RFC1583Compatibility flag is disabled
 OpaqueCapability flag is disabled
 Initial SPF scheduling delay 0 millisec(s)
 Minimum hold time between consecutive SPFs 50 millisec(s)
 Maximum hold time between consecutive SPFs 5000 millisec(s)
 Hold time multiplier is currently 1
 SPF algorithm last executed 1m50s ago
 Last SPF duration 140 usecs
 SPF timer is inactive
 LSA minimum interval 5000 msecs
 LSA minimum arrival 1000 msecs
 Write Multiplier set to 20
 Refresh timer 10 secs
 Number of external LSA 0. Checksum Sum 0x00000000
 Number of opaque AS LSA 0. Checksum Sum 0x00000000
 Number of areas attached to this router: 1
 Area ID: 0.0.0.0 (Backbone)
   Number of interfaces in this area: Total: 1, Active: 1
   Number of fully adjacent neighbors in this area: 1
   Area has no authentication
   SPF algorithm executed 5 times
   Number of LSA 4
   Number of router LSA 2. Checksum Sum 0x00008415
   Number of network LSA 1. Checksum Sum 0x00004393
   Number of summary LSA 1. Checksum Sum 0x0000757f
   Number of ASBR summary LSA 0. Checksum Sum 0x00000000
   Number of NSSA LSA 0. Checksum Sum 0x00000000
   Number of opaque link LSA 0. Checksum Sum 0x00000000
   Number of opaque area LSA 0. Checksum Sum 0x00000000

```

#### Border Routers show command
Displays all the ABR's and ASBR's.

**Syntax**: `show ip ospf [<instance-id>|vrf <vrfname>|all] border-routers`

**Parameters**  :
- `instance-id` - OSPF Instance ID (1-65535)
- `vrfname`     - VRF Name (Max: 15 characters, prefixed with Vrf)

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
```

#### Database summary show command
Displays OSPF Database summary.

**Syntax**: `show ip ospf [<instance-id>|vrf <vrfname>] database [asbr-summary|external|network|router|summary|nssa-external|opaque-link|opaque-area|opaque-as [A.B.C.D [self-originate|adv-router <A.B.C.D>]]|[adv-router <E.F.G.H>|self-originate]]`

**Parameters**  :
- `instance-id` - OSPF Instance ID (1-65535)
- `vrfname`     - VRF Name (Max: 15 characters, prefixed with Vrf)
- `A.B.C.D`     - Link State ID (as an IP address)
- `E.F.G.H`     - Advertising Router (as an IP address)

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# show ip ospf database

       OSPF Router with ID (10.10.10.2)

                Router Link States (Area 0.0.0.0)

Link ID         ADV Router      Age  Seq#       CkSum  Link count
10.10.10.1      10.10.10.1       123 0x80000007 0x2e01 1
10.10.10.2      10.10.10.2       271 0x80000003 0x31ff 1

                Net Link States (Area 0.0.0.0)

Link ID         ADV Router      Age  Seq#       CkSum
20.20.20.2      10.10.10.2       271 0x80000001 0x1e9e

                Summary Link States (Area 0.0.0.0)

Link ID         ADV Router      Age  Seq#       CkSum  Route
30.30.30.0      10.10.10.1       123 0x80000001 0x9c3d 30.30.30.0/24

sonic#
sonic# show ip ospf database network 20.20.20.2

       OSPF Router with ID (10.10.10.2)


                Net Link States (Area 0.0.0.0)

  LS age: 352
  Options: 0x2  : *|-|-|-|-|-|E|-
  LS Flags: 0x3
  LS Type: network-LSA
  Link State ID: 20.20.20.2 (address of Designated Router)
  Advertising Router: 10.10.10.2
  LS Seq Number: 80000001
  Checksum: 0x1e9e
  Length: 32

  Network Mask: /24
        Attached Router: 10.10.10.1
        Attached Router: 10.10.10.2

sonic#
sonic# show ip ospf vrf Vrf-20 database router
VRF Name: Vrf-20

       OSPF Router with ID (10.10.10.2)


                Router Link States (Area 0.0.0.0)

  LS age: 213
  Options: 0x2  : *|-|-|-|-|-|E|-
  LS Flags: 0x6
  Flags: 0x1 : ABR
  LS Type: router-LSA
  Link State ID: 1.1.1.1
  Advertising Router: 1.1.1.1
  LS Seq Number: 80000004
  Checksum: 0x5216
  Length: 36

   Number of Links: 1

    Link connected to: a Transit Network
     (Link ID) Designated Router address: 20.20.20.2
     (Link Data) Router Interface address: 20.20.20.1
      Number of TOS metrics: 0
       TOS 0 Metric: 100


  LS age: 316
  Options: 0x2  : *|-|-|-|-|-|E|-
  LS Flags: 0x3
  Flags: 0x0
  LS Type: router-LSA
  Link State ID: 10.10.10.2
  Advertising Router: 10.10.10.2
  LS Seq Number: 80000003
  Checksum: 0x31ff
  Length: 36

   Number of Links: 1

    Link connected to: a Transit Network
     (Link ID) Designated Router address: 20.20.20.2
     (Link Data) Router Interface address: 20.20.20.2
      Number of TOS metrics: 0
       TOS 0 Metric: 100


```

##### Displays OSPF Database summary for all VRFs.

**Syntax**: `show ip ospf vrf all database [asbr-summary|external|network|router|summary|nssa-external|opaque-link|opaque-area|opaque-as [A.B.C.D [self-originate|adv-router <A.B.C.D>]]|[adv-router <E.F.G.H>|self-originate]]`

**Parameters**  :
- `instance-id` - OSPF Instance ID (1-65535)
- `vrfname`     - VRF Name (Max: 15 characters, prefixed with Vrf)
- `A.B.C.D`     - Link State ID (as an IP address)
- `E.F.G.H`     - Advertising Router (as an IP address)

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# show ip ospf vrf all database
VRF Name: Vrf-20

       OSPF Router with ID (10.10.10.2)

                Router Link States (Area 0.0.0.0)

Link ID         ADV Router      Age  Seq#       CkSum  Link count
1.1.1.1         1.1.1.1          512 0x80000004 0x5216 1
10.10.10.2      10.10.10.2       614 0x80000003 0x31ff 1

                Net Link States (Area 0.0.0.0)

Link ID         ADV Router      Age  Seq#       CkSum
20.20.20.2      10.10.10.2       614 0x80000002 0x4393

                Summary Link States (Area 0.0.0.0)

Link ID         ADV Router      Age  Seq#       CkSum  Route
30.30.30.0      1.1.1.1          512 0x80000001 0x757f 30.30.30.0/24

VRF Name: Vrf-2

       OSPF Router with ID (11.11.11.2)

                Router Link States (Area 0.0.0.1)

Link ID         ADV Router      Age  Seq#       CkSum  Link count
11.11.11.1      11.11.11.1       143 0x80000003 0xbadf 1
11.11.11.2      11.11.11.2       143 0x80000003 0xb8de 1

                Net Link States (Area 0.0.0.1)

Link ID         ADV Router      Age  Seq#       CkSum
2.2.2.2         11.11.11.2       143 0x80000001 0xcc1d

```

##### Displays OSPF Database summary for MaxAge and Self-originated link states.

**Syntax**: `show ip ospf [<instance-id>|vrf <vrfname>|all] database [max-age|self-originated]`

**Parameters**  :
- `instance-id` - OSPF Instance ID (1-65535)
- `vrfname`     - VRF Name (Max: 15 characters, prefixed with Vrf)

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# show ip ospf database self-originate

       OSPF Router with ID (10.10.10.2)

                Router Link States (Area 0.0.0.0)

Link ID         ADV Router      Age  Seq#       CkSum  Link count
10.10.10.2      10.10.10.2       388 0x80000003 0x31ff 1

                Net Link States (Area 0.0.0.0)

Link ID         ADV Router      Age  Seq#       CkSum
20.20.20.2      10.10.10.2       388 0x80000001 0x1e9e

sonic# show ip ospf vrf all database self-originate
VRF Name: Vrf-20

       OSPF Router with ID (10.10.10.2)

                Router Link States (Area 0.0.0.0)

Link ID         ADV Router      Age  Seq#       CkSum  Link count
10.10.10.2      10.10.10.2       719 0x80000003 0x31ff 1

                Net Link States (Area 0.0.0.0)

Link ID         ADV Router      Age  Seq#       CkSum
20.20.20.2      10.10.10.2       719 0x80000002 0x4393


VRF Name: Vrf-2

       OSPF Router with ID (11.11.11.2)

                Router Link States (Area 0.0.0.1)

Link ID         ADV Router      Age  Seq#       CkSum  Link count
11.11.11.2      11.11.11.2       103 0x80000003 0xb8de 1

                Net Link States (Area 0.0.0.1)

Link ID         ADV Router      Age  Seq#       CkSum
2.2.2.2         11.11.11.2       103 0x80000001 0xcc1d

```

#### Interface show command
Displays OSPF Interface information.

**Syntax**: `show ip ospf [vrf <vrfname>|all] interface [<IFNAME>]|[traffic <IFNAME>]`

**Parameters**  :
- `vrfname` - VRF Name (Max: 15 characters, prefixed with Vrf)
- `IFNAME`  - Interface name(e.g. Ethernet1, Vlan1, PortChannel1..)

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# show ip ospf interface
Ethernet8 is up
  ifindex 106, MTU 9100 bytes, BW 1000 Mbit <UP,BROADCAST,RUNNING,MULTICAST>
  Internet Address 20.20.20.2/24, Broadcast 20.20.20.255, Area 0.0.0.0
  MTU mismatch detection: enabled
  Router ID 10.10.10.2, Network Type BROADCAST, Cost: 100
  Transmit Delay is 1 sec, State DR, Priority 1
  Backup Designated Router (ID) 10.10.10.1, Interface Address 20.20.20.1
  Multicast group memberships: OSPFAllRouters OSPFDesignatedRouters
  Timer intervals configured, Hello 10s, Dead 40s, Wait 40s, Retransmit 5
    Hello due in 0.698s
  Neighbor Count is 1, Adjacent neighbor count is 1


sonic#
sonic# show ip ospf interface traffic

Interface       HELLO            DB-Desc         LS-Req           LS-Update        LS-Ack
                Rx/Tx            Rx/Tx            Rx/Tx            Rx/Tx            Rx/Tx
--------------------------------------------------------------------------------------------
Ethernet8        53/60             3/2             1/1             5/2             2/3

sonic# show ip ospf vrf Vrf-20 interface
VRF Name: Vrf-20
Ethernet8 is up
  ifindex 106, MTU 9100 bytes, BW 1000 Mbit <UP,BROADCAST,RUNNING,MULTICAST>
  Internet Address 20.20.20.2/24, Broadcast 20.20.20.255, Area 0.0.0.0
  MTU mismatch detection: enabled
  Router ID 10.10.10.2, Network Type BROADCAST, Cost: 100
  Transmit Delay is 1 sec, State DR, Priority 1
  Backup Designated Router (ID) 1.1.1.1, Interface Address 20.20.20.1
  Saved Network-LSA sequence number 0x80000002
  Multicast group memberships: OSPFAllRouters OSPFDesignatedRouters
  Timer intervals configured, Hello 10s, Dead 40s, Wait 40s, Retransmit 5
    Hello due in 9.041s
  Neighbor Count is 1, Adjacent neighbor count is 1


```

##### Displays OSPF Interface information for specific Instance.

**Syntax**: `show ip ospf <instance-id> interface [<IFNAME>]`

**Parameters**  :
- `instance-id` - OSPF Instance ID (1-65535)
- `IFNAME`      - Interface name(e.g. Ethernet1, Vlan1, PortChannel1..)

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
```

#### Neighbor show command
Displays OSPF Neighbor list.

**Syntax**: `show ip ospf [<instance-id>] neighbor [<A.B.C.D>|detail [all]|all|<IFNAME> [detail]]`

**Parameters**  :
- `instance-id` - OSPF Instance ID (1-65535)
- `A.B.C.D`     - Neighbor ID (as an IP address)
- `IFNAME`      - Interface name(e.g. Ethernet1, Vlan1, PortChannel1..)

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# show ip ospf neighbor

Neighbor ID     Pri State           Dead Time Address         Interface                        RXmtL RqstL DBsmL
10.10.10.1        1 Full/Backup       33.481s 20.20.20.1      Ethernet8:20.20.20.2                 0     0     0


sonic# show ip ospf neighbor detail
 Neighbor 10.10.10.1, interface address 20.20.20.1
    In the area 0.0.0.0 via interface Ethernet8
    Neighbor priority is 1, State is Full, 4 state changes
    Most recent state change statistics:
      Progressive change 10m42s ago
    DR is 20.20.20.2, BDR is 20.20.20.1
    Options 2 *|-|-|-|-|-|E|-
    Dead timer due in 38.638s
    Database Summary List 0
    Link State Request List 0
    Link State Retransmission List 0
    Thread Inactivity Timer on
    Thread Database Description Retransmision off
    Thread Link State Request Retransmission on
    Thread Link State Update Retransmission on

```

##### Displays OSPF Neighbor list for specific VRF.

**Syntax**: `show ip ospf vrf <vrfname> neighbor [<A.B.C.D>|detail [all]|all|<IFNAME>]`

**Parameters**  :
- `vrfname` - VRF Name (Max: 15 characters, prefixed with Vrf)
- `A.B.C.D` - Neighbor ID (as an IP address)
- `IFNAME`  - Interface name(e.g. Ethernet1, Vlan1, PortChannel1..)

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# show ip ospf vrf Vrf-20 neighbor
VRF Name: Vrf-20

Neighbor ID     Pri State           Dead Time Address         Interface                        RXmtL RqstL DBsmL
1.1.1.1           1 Full/Backup       37.394s 20.20.20.1      Ethernet8:20.20.20.2                 0     0     0


```

##### Displays OSPF Neighbor list for all VRFs.

**Syntax**: `show ip ospf vrf all neighbor [<A.B.C.D>|detail|all|<IFNAME>]`

**Parameters**  :
- `A.B.C.D`     - Neighbor ID (as an IP address)
- `IFNAME`      - Interface name(e.g. Ethernet1, Vlan1, PortChannel1..)

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# show ip ospf vrf all neighbor
VRF Name: Vrf-20

Neighbor ID     Pri State           Dead Time Address         Interface                        RXmtL RqstL DBsmL
1.1.1.1           1 Full/Backup       37.766s 20.20.20.1      Ethernet8:20.20.20.2                 0     0     0

VRF Name: Vrf-2

Neighbor ID     Pri State           Dead Time Address         Interface                        RXmtL RqstL DBsmL
11.11.11.1        1 Full/Backup       31.650s 2.2.2.1         Ethernet9:2.2.2.2                    0     0     0

OSPF instance not found
```

#### Routing table show command
Displays OSPF routing table.

**Syntax**: `show ip ospf [<instance-id>|vrf <vrfname>|all] route`

**Parameters**  :
- `instance-id` - OSPF Instance ID (1-65535)
- `vrfname`     - VRF Name (Max: 15 characters, prefixed with Vrf)

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# show ip ospf route
============ OSPF network routing table ============
N    20.20.20.0/24         [100] area: 0.0.0.0
                           directly attached to Ethernet8
N IA 30.30.30.0/24         [110] area: 0.0.0.0
                           via 20.20.20.1, Ethernet8

============ OSPF router routing table =============
R    10.10.10.1            [100] area: 0.0.0.0, ABR
                           via 20.20.20.1, Ethernet8

============ OSPF external routing table ===========

sonic#
sonic# show ip ospf vrf Vrf-20 route
VRF Name: Vrf-20
============ OSPF network routing table ============
N    20.20.20.0/24         [100] area: 0.0.0.0
                           directly attached to Ethernet8
N IA 30.30.30.0/24         [110] area: 0.0.0.0
                           via 20.20.20.1, Ethernet8

============ OSPF router routing table =============
R    1.1.1.1               [100] area: 0.0.0.0, ABR
                           via 20.20.20.1, Ethernet8

============ OSPF external routing table ===========


```

#### Router Information show command
Displays OSPF Router Information.

**Syntax**: `show ip ospf router-info`

**Parameters**  : None

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# show ip ospf router-info
--- Router Information parameters ---
  Router Capabilities: 0x10000000

```

#### VRFs show command
Displays OSPF VRFs Information.

**Syntax**: `show ip ospf vrfs`

**Parameters**  : None

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# show ip ospf vrfs
Name                       Id     RouterId
Vrf-20                     134    10.10.10.2
Vrf-2                      135    11.11.11.2

Total number of OSPF VRFs: 2

```

#### Graceful Restart helper show command
OSPF Graceful Restart command

**Syntax**: `show ip ospf [vrf <vrfname>|all] graceful-restart helper [detail]`

**Parameters**  :
- `vrfname` - VRF Name (Max: 15 characters, prefixed with Vrf)

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
```

#### Reachable OSPF routers show command
Displays all the reachable OSPF routers.

**Syntax**: `show ip ospf [<instance-id>|vrf <vrfname>|all] reachable-routers`

**Parameters**  :
- `instance-id` - OSPF Instance ID (1-65535)
- `vrfname`     - VRF Name (Max: 15 characters, prefixed with Vrf)

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
```

#### External summary addresses show command
Displays external summary addresses.

**Syntax**: `show ip ospf [vrf <vrfname>|all]  summary-address [detail]`

**Parameters**  :
- `vrfname` - VRF Name (Max: 15 characters, prefixed with Vrf)

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
```

### OSPF Clear commands
#### Interface clear command
Clears OSPF Interface information

**Syntax**: `clear ip ospf interface [<L3intf>]`

**Parameters**  :
- `L3intf` - L3 Interface name

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# clear ip ospf interface
sonic# clear ip ospf interface Ethernet8
```

#### VRF Interface clear command
Clears OSPF Interface information

**Syntax**: `clear ip ospf vrf <vrfname> interface [<L3intf>]`

**Parameters**  :
- `vrfname` - VRF Name (Max: 15 characters, prefixed with Vrf)
- `L3intf`  - L3 Interface name

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# clear ip ospf vrf Vrf-1 interface
sonic# clear ip ospf vrf Vrf-1 interface Ethernet8
```

#### Process clear command
Clears OSPF Interface information

**Syntax**: `clear ip ospf process`

**Parameters**  : None

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# clear ip ospf process
```

#### Neighbor clear command
Clears OSPF Neighbor information

**Syntax**: `clear ip ospf [<instance-id>] neighbor [<A.B.C.D>]`

**Parameters**  :
- `instance-id` - Instance ID (1-65535)
- `A.B.C.D`     - Neighbor ID (as an IP address)

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
sonic# clear ip ospf neighbor
sonic# clear ip ospf neighbor 1.1.1.1
```

### OSPF Debug commands
#### Event and NSSA command
Enables debugs for ospf event and nssa information.

**Syntax**: `debug ospf [<instance-id>] event|nssa`

**Parameters**  :
- `instance-id` - Instance ID (1-65535)

**Command mode** : EXEC

**Click command** : None

**Usage**       : Use `no debug ospf <instance-id> event|nssa` or `no debug ospf [event|nssa]` to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# debug ospf event
sonic# no debug ospf event
sonic# debug ospf 1 event
sonic# no debug ospf 1 event
sonic#
sonic# debug ospf nssa
sonic# no debug ospf nssa
sonic# debug ospf 1 nssa
sonic# no debug ospf 1 nssa
sonic#
sonic# no debug ospf
```

#### ISM and NSM command
Enables debugs for ospf Interface State Machine and Neighbor State Machine.

**Syntax**: `debug ospf [<instance-id>] ism|nsm [status|events|timers]`

**Parameters**  :
- `instance-id` - Instance ID (1-65535)

**Command mode** : EXEC

**Click command** : None

**Usage**       : Use `no debug ospf <instance-id> ism|nsm [status|events|timers]` or `no debug ospf [ism|nsm [status|events|timers]]` to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# debug ospf ism  events
sonic# no debug ospf ism  events
sonic#
sonic# debug ospf nsm events
sonic# no debug ospf nsm events
```

#### Link State Advertisement command
Enables debugs for ospf Link State Advertisement.

**Syntax**: `debug ospf [<instance-id>] lsa [aggregate|generate|flooding|install|refresh]`

**Parameters**  :
- `instance-id` - Instance ID (1-65535)

**Command mode** : EXEC

**Click command** : None

**Usage**       : Use `no debug ospf <instance-id> lsa [aggregate|generate|flooding|install|refresh]` or `no debug ospf [lsa [generate|flooding|install|refresh]]` to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# debug ospf lsa flooding
sonic# no debug ospf lsa flooding
sonic#
```

#### Packet command
Enables debugs for ospf packet.

**Syntax**: `debug ospf [<instance-id>] packet hello|dd|ls-request|ls-update|ls-ack|all [send [detail]|recv [detail]|detail]`

**Parameters**  :
- `instance-id` - Instance ID (1-65535)

**Command mode** : EXEC

**Click command** : None

**Usage**       : Use `no debug ospf <instance-id> packet hello|dd|ls-request|ls-update|ls-ack|all [send [detail]|recv [detail]|detail]` or `no debug ospf [packet hello|dd|ls-request|ls-update|ls-ack|all [send [detail]|recv [detail]|detail]]` to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# debug ospf packet ls-request send detail
sonic# no debug ospf packet ls-request send detail
sonic#
```

#### Zebra command
Enables debugs for zebra information.

**Syntax**: `debug ospf [<instance-id>] zebra [interface|redistribute]`

**Parameters**  :
- `instance-id` - Instance ID (1-65535)

**Command mode** : EXEC

**Click command** : None

**Usage**       : Use `no debug ospf <instance-id> zebra [interface|redistribute]` or `no debug ospf [zebra [interface|redistribute]]` to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# debug ospf zebra interface
sonic# no debug ospf zebra interface
sonic#
```

#### Default Information, SR, TE command
Enables debugs for ospf SR, TE and default information.

**Syntax**: `debug ospf default-information|sr|te`

**Parameters**  : None

**Command mode** : EXEC

**Click command** : None

**Usage**       : Use `no debug ospf [default-information|sr|te]` to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# debug ospf default-information
sonic# no debug ospf default-information
sonic#
sonic# debug ospf sr
sonic# no debug ospf sr
sonic#
sonic# debug ospf te
sonic# no debug ospf te
```

#### BFD, client-api, graceful-restart, ldp-sync and ti-lfa command

**Syntax**: `debug ospf [<instance-id>] bfd|client-api|graceful-restart|ldp-sync|ti-lfa`

**Parameters**  :
- `instance-id` - Instance ID (1-65535)

**Command mode** : EXEC

**Click command** : None

**Usage**       : Use `no debug ospf <instance-id> bfd|client-api|graceful-restart|ldp-sync|ti-lfa` or `no debug ospf [bfd|client-api|graceful-restart|ldp-sync|ti-lfa]` to remove the configuration.

**Supported Releases** :  2.0 or later

**Example**
```
```

### OSPF6 Config commands
#### router ospf6
Enables a OSPF protocol process for IPv6.

**Syntax**: `router ospf6`

**Parameters**  : None

**Command mode** : CONFIG

**Usage**       : Use `no router ospf6` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config)# router ospf6
sonic(config)# no router ospf6
```

#### router ospf6 vrf [NAME]
Enables a OSPF protocol process for IPv6 with Vrf.

**Syntax**: `router ospf6 vrf <NAME>`

**Parameters**  :
- `NAME` - VRF Name (Max: 15 characters, prefixed with Vrf)

**Command mode** : CONFIG

**Usage**       : Use `no router ospf6 vrf <NAME>` to remove the configuration.

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
sonic(config)# router ospf6 vrf Vrf-1
sonic(config)# no router ospf6 vrf Vrf-1
```

#### Aggregation command
Sets external route aggregation delay timer.

**Syntax**: `aggregation timer <interval>`

**Parameters**  :
- `interval` - Delay timer interval in seconds (5-1800)

**Command mode** : Router OSPF6 mode

**Usage**       : Use `no aggregation timer [<interval>]` to remove the configuration.

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
sonic(config-router)# aggregation timer 5
sonic(config-router)# no aggregation timer
```

#### Area commands
##### Export-list
Sets the filter for networks announced to other areas.

**Syntax**: `area <A.B.C.D|area-id> export-list <NAME>`

**Parameters**  :
- `A.B.C.D` - OSPF6 area ID in IP address format
- `area-id` - OSPF6 area ID as a decimal value (0-4294967295)
- `NAME`    - Name of the access-list

**Command mode** : Router OSPF6 mode

**Usage**       : Use `no area <A.B.C.D|area-id> export-list <NAME>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-ospf6)# area 1 export-list explst
sonic(config-ospf6)# no area 1 export-list explst
sonic(config-ospf6)#
sonic(config-ospf6)# area 1.1.1.1 export-list explst
sonic(config-ospf6)# no area 1.1.1.1 export-list explst
```

##### Filter-list
Filters networks between OSPF6 areas.

**Syntax**: `area <A.B.C.D|area-id> filter-list prefix <NAME> in|out`

**Parameters**  :
- `A.B.C.D` - OSPF6 area ID in IP address format
- `area-id` - OSPF6 area ID as a decimal value (0-4294967295)
- `NAME`    - Name of an IP prefix-list

**Command mode** : Router OSPF6 mode

**Usage**       : Use `no area <A.B.C.D|area-id> filter-list prefix <NAME> in|out` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-ospf6)# area 1 filter-list prefix prflst in
sonic(config-ospf6)# area 1 filter-list prefix prflst out
sonic(config-ospf6)# no area 1 filter-list prefix prflst in
sonic(config-ospf6)# no area 1 filter-list prefix prflst out
sonic(config-ospf6)#
sonic(config-ospf6)# area 1.1.1.1 filter-list prefix prflst in
sonic(config-ospf6)# area 1.1.1.1 filter-list prefix prflst out
sonic(config-ospf6)# no area 1.1.1.1 filter-list prefix prflst in
sonic(config-ospf6)# no area 1.1.1.1 filter-list prefix prflst out
```

##### Import-list
Sets the filter for networks from other areas announced to the specified one.

**Syntax**: `area <A.B.C.D|area-id> import-list <NAME>`

**Parameters**  :
- `A.B.C.D` - OSPF6 area ID in IP address format
- `area-id` - OSPF6 area ID as a decimal value (0-4294967295)
- `NAME`    - Name of the access-list

**Command mode** : Router OSPF6 mode

**Usage**       : Use `no area <A.B.C.D|area-id> import-list <NAME>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-ospf6)# area 1 import-list implst
sonic(config-ospf6)# no area 1 import-list implst
sonic(config-ospf6)#
sonic(config-ospf6)# area 1.1.1.1 import-list implst
sonic(config-ospf6)# no area 1.1.1.1 import-list implst
```

##### NSSA
Configures OSPF6 area as nssa.

**Syntax**: `area <A.B.C.D|area-id> nssa [no-summary | default-information-originate [{metric <metric>|metric-type <type>}|no-summary] | range <A::B/M> [cost <id>|not-advertise]`

**Parameters**  :
- `A.B.C.D` - OSPF6 area ID in IP address format
- `area-id` - OSPF6 area ID as a decimal value (0-4294967295)
- `metric`  - OSPF metric (0-16777214)
- `type`    - Set OSPF External Type 1/2 metrics (1-2)
- `A::B/M`  - IPv6 prefix

**Command mode** : Router OSPF6 mode

**Usage**       : Use `no area <A.B.C.D|area-id> nssa [no-summary | default-information-originate [{metric <metric>|metric-type <type>}|no-summary] | range <A::B/M> [cost <id>|not-advertise]` to remove the configuration.

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
sonic(config-router)# area 1 nssa
sonic(config-router)# area 1 nssa no-summary
sonic(config-router)# area 1 nssa default-information-originate
sonic(config-router)# area 1 nssa default-information-originate metric 1 metric-type 1 no-summary
sonic(config-router)# area 1 nssa range 121::1/64
sonic(config-router)# area 1 nssa range 121::1/64 cost 1
sonic(config-router)# area 1 nssa range 121::1/64 not-advertise
sonic(config-router)# no area 1 nssa range 121::1/64 not-advertise
sonic(config-router)# no area 1 nssa range 121::1/64 cost 1
sonic(config-router)# no area 1 nssa range 121::1/64
sonic(config-router)# no area 1 nssa default-information-originate metric 1 metric-type 1 no-summary
sonic(config-router)# no area 1 nssa default-information-originate
sonic(config-router)# no area 1 nssa no-summary
sonic(config-router)# no area 1 nssa
```

##### Address Range
Configures Address range.

**Syntax**: `area <A.B.C.D|area-id> range [advertise|cost <cost-id>|not-advertise]`

**Parameters**  :
- `A.B.C.D` - OSPF6 area ID in IP address format
- `area-id` - OSPF6 area ID as a decimal value (0-4294967295)
- `cost-id` - Advertised metric for this range (0-16777215)
- `A::B/M`  - IPv6 address

**Command mode** : Router OSPF6 mode

**Usage**       : Use `no area <A.B.C.D|area-id> range [advertise|cost <cost-id>|not-advertise]`
                  to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-ospf6)# area 1 range 121::1/64
sonic(config-ospf6)# area 1 range 121::1/64 advertise
sonic(config-ospf6)# area 1 range 121::1/64 cost 2
sonic(config-ospf6)# area 1 range 121::1/64 not-advertise
sonic(config-ospf6)# no area 1 range 121::1/64
sonic(config-ospf6)# no area 1 range 121::1/64 advertise
sonic(config-ospf6)# no area 1 range 121::1/64 cost 2
sonic(config-ospf6)# no area 1 range 121::1/64 not-advertise
```

##### Stub
Configures OSPF6 area as stub.

**Syntax**: `area <A.B.C.D|area-id> stub [no-summary]`

**Parameters**  :
- `A.B.C.D` - OSPF6 area ID in IP address format
- `area-id` - OSPF6 area ID as a decimal value (0-4294967295)

**Command mode** : Router OSPF6 mode

**Usage**       : Use `no area <A.B.C.D|area-id> stub [no-summary]` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-ospf6)# area 1 stub
sonic(config-ospf6)# area 1 stub no-summary
sonic(config-ospf6)# no area 1 stub no-summary
sonic(config-ospf6)# no area 1 stub
```

#### Auto-Cost command
Calculates OSPF6 interface cost according to bandwidth.

**Syntax**: `auto-cost reference-bandwidth <bandwidth>`

**Parameters**  :
- `bandwidth` - The reference bandwidth in terms of Mbits per second (1-4294967)

**Command mode** : Router OSPF6 mode

**Usage**       : Use `no auto-cost reference-bandwidth <bandwidth>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-ospf6)# auto-cost reference-bandwidth 1
sonic(config-ospf6)# no auto-cost reference-bandwidth 1
```

#### Default-Information command
Control distribution of default information.

**Syntax**: `default-information originate [{always|metric <metric>|metric-type <type>|route-map <rmap>}]`

**Parameters**  :
- `metric` - OSPFv3 metric (0-16777214)
- `type`   - Set OSPFv3 External Type 1/2 metrics (1-2)
- `rmap`   - Route map reference

**Command mode** : Router OSPF6 mode

**Usage**       : Use `no default-information originate [{always|metric <metric>|metric-type <type>|route-map <rmap>}]` to remove the configuration.

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
sonic(config-router)# default-information originate
sonic(config-router)# default-information originate always metric 1 metric-type 2 route-map rmap1
sonic(config-router)# no default-information originate always metric 1 metric-type 2 route-map rmap1
sonic(config-router)# no default-information originate
```

#### Distance command
##### Administrative distance.

**Syntax**: `distance <dist>`

**Parameters**  :
- `dist` - OSPF6 Administrative distance (1-255)

**Command mode** : Router OSPF6 mode

**Usage**       : Use `no distance <dist>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-ospf6)# distance 1
sonic(config-ospf6)# no distance 1
```

##### Administrative distance for intra-area, inter-area and external routes.

**Syntax**: `distance ospf6 {intra-area <intra>|inter-area <inter>)|external <ext>}`

**Parameters**  :
- `intra` - Distance for intra-area routes (1-255)
- `inter` - Distance for inter-area routes (1-255)
- `ext`   - Distance for external routes (1-255)

**Command mode** : Router OSPF6 mode

**Usage**       : Use `no distance ospf6 {intra-area <intra>|inter-area <inter>)|external <ext>}` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-ospf6)# distance ospf6 external 1 inter-area 1 intra-area 1
sonic(config-ospf6)# no distance ospf6 external 1 inter-area 1 intra-area 1
```

#### Graceful Restart prepare command
Command to prepare for upcoming graceful restart.

**Syntax**: `graceful-restart prepare ipv6 ospf`

**Parameters**  : None

**Command mode** : CONFIG

**Usage**       : None

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
sonic(config-router)# graceful-restart prepare ipv6 ospf
```

#### Graceful Restart grace-period command
Sets grace period for graceful restart.

**Syntax**: `graceful-restart [grace-period <num>]`

**Parameters**  :
- `num` - Maximum length of the 'grace period' in seconds (1-1800)

**Command mode** : Router OSPF6 mode

**Usage**       : Use `no graceful-restart [grace-period <num>]` to remove the configuration.

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
sonic(config-router)# graceful-restart grace-period 10
sonic(config-router)# no graceful-restart grace-period 10
```

#### Graceful Restart helper command

**Syntax**: `graceful-restart [helper planned-only|enable [<A.B.C.D>]|supported-grace-time <interval>|lsa-check-disable]`

**Parameters**  :
- `A.B.C.D`  - Advertising Router-ID
- `interval` - Grace interval in seconds (10-1800)

**Command mode** : Router OSPF6 mode

**Usage**       : Use `no graceful-restart [helper planned-only|enable [<A.B.C.D>]|supported-grace-time <interval>|lsa-check-disable]`
                  to remove the configuration.

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
sonic(config-router)# graceful-restart helper enable
sonic(config-router)# graceful-restart helper enable 1.1.1.1
sonic(config-router)# graceful-restart helper planned-only
sonic(config-router)# graceful-restart helper lsa-check-disable
sonic(config-router)# graceful-restart helper supported-grace-time 10
sonic(config-router)# no graceful-restart helper enable 1.1.1.1
sonic(config-router)# no graceful-restart helper enable
sonic(config-router)# no graceful-restart helper planned-only
sonic(config-router)# no graceful-restart helper lsa-check-disable
sonic(config-router)# no graceful-restart helper supported-grace-time 10
```
#### Log Adjacency changes command
Log changes in adjacency state.

**Syntax**: `log-adjacency-changes [detail]`

**Parameters**  : None

**Command mode** : Router OSPF6 mode

**Usage**       : Use `no log-adjacency-changes [detail]` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-ospf6)# log-adjacency-changes
sonic(config-ospf6)# log-adjacency-changes detail
sonic(config-ospf6)# no log-adjacency-changes detail
sonic(config-ospf6)# no log-adjacency-changes
```

#### Maximum paths command
Sets maximum number of multiple paths for ECMP support.

**Syntax**: `maximum-paths <num-paths>`

**Parameters**  :
- `num-paths` -  Number of paths (1-256)

**Command mode** : Router OSPF6 mode

**Usage**       : Use `no maximum-paths [<num-paths>]` to remove the configuration.

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
sonic(config-router)# maximum-paths 10
sonic(config-router)# no maximum-paths
```

#### Router-id command
Configures OSPF6 router-id.

**Syntax**: `ospf6 router-id <A.B.C.D>`

**Parameters**  :
- `A.B.C.D` - specify by IPv4 address notation(e.g. 0.0.0.0)

**Command mode** : Router OSPF6 mode

**Usage**       : Use `no ospf6 router-id <A.B.C.D>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-ospf6)# ospf6 router-id 1.1.1.1
sonic(config-ospf6)# no ospf6 router-id 1.1.1.1
```

#### OSPF send-extra-data command
Extra data to Zebra for display/use

**Syntax**: `ospf6 send-extra-data zebra`

**Parameters**  : None

**Command mode** : Router OSPF6 mode

**Usage**       : Use `no ospf6 send-extra-data zebra` to remove the configuration.

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
sonic(config-router)# ospf6 send-extra-data zebra
sonic(config-router)# no ospf6 send-extra-data zebra
```

#### Redistribute command
Redistributes information from another routing protocol.

**Syntax**: `redistribute kernel|connected|static|ripng|isis|bgp|nhrp|table|vnc|babel|openfabric [{metric <metric>|metric-type <type>|route-map <rmap>}]`

**Parameters**  :
- `metric`      - OSPF metric (0-16777214)
- `type`        - Set OSPF External Type 1/2 metrics (1-2)
- `rmap`        - Route map reference

**Command mode** : Router OSPF6 mode

**Usage**       : Use `no redistribute kernel|connected|static|ripng|isis|bgp|nhrp|table|vnc|babel|openfabric [{metric <metric>|metric-type <type>|route-map <rmap>}]` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-ospf6)# redistribute babel
sonic(config-ospf6)# redistribute babel metric 1 metric-type 1 route-map rmap1
sonic(config-ospf6)# redistribute bgp
sonic(config-ospf6)# redistribute bgp metric 1 metric-type 1 route-map rmap1
sonic(config-ospf6)# redistribute connected
sonic(config-ospf6)# redistribute connected metric 1 metric-type 1 route-map rmap1
sonic(config-ospf6)# redistribute isis
sonic(config-ospf6)# redistribute isis metric 1 metric-type 1 route-map rmap1
sonic(config-ospf6)# redistribute kernel
sonic(config-ospf6)# redistribute kernel metric 1 metric-type 1 route-map rmap1
sonic(config-ospf6)# redistribute nhrp
sonic(config-ospf6)# redistribute nhrp metric 1 metric-type 1 route-map rmap1
sonic(config-ospf6)# redistribute openfabric
sonic(config-ospf6)# redistribute openfabric metric 1 metric-type 1 route-map rmap1
sonic(config-ospf6)# redistribute ripng
sonic(config-ospf6)# redistribute ripng metric 1 metric-type 1 route-map rmap1
sonic(config-ospf6)# redistribute static
sonic(config-ospf6)# redistribute static metric 1 metric-type 1 route-map rmap1
sonic(config-ospf6)# redistribute table
sonic(config-ospf6)# redistribute table metric 1 metric-type 1 route-map rmap1
sonic(config-ospf6)# redistribute vnc
sonic(config-ospf6)# redistribute vnc metric 1 metric-type 1 route-map rmap1
```

#### Stub router command
Makes router a stub router.

**Syntax**: `stub-router administrative`

**Parameters**  : None

**Command mode** : Router OSPF6 mode

**Usage**       : Use `no stub-router administrative` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-ospf6)# stub-router administrative
sonic(config-ospf6)# no stub-router administrative
```

#### Summary address command
Sets external summary address prefix.

**Syntax**: `summary-address <A::B/M> [no-advertise|tag <val>|{metric <metric>|metric-type <metric-type>}]`

**Parameters**  :
- `A::B/M`      - Summary address prefix
- `val`         - Router tag value (1-4294967295)
- `metric`      - Advertised metric for this route (0-16777214)
- `metric-type` - Set OSPFv3 External Type 1/2 metrics (1-2)

**Command mode** : Router OSPF6 mode

**Usage**       : Use `no summary-address <A::B/M> [no-advertise|tag <val>|{metric <metric>|metric-type <metric-type>}]`
                  to remove the configuration.

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
sonic(config-router)# summary-address 2001::1/64
sonic(config-router)# summary-address 2001::1/64 no-advertise
sonic(config-router)# summary-address 2001::1/64 tag 5
sonic(config-router)# summary-address 2001::1/64 metric 10
sonic(config-router)# summary-address 2001::1/64 metric-type 1
sonic(config-router)# no summary-address 2001::1/64 no-advertise
sonic(config-router)# no summary-address 2001::1/64 tag 5
sonic(config-router)# no summary-address 2001::1/64 metric 10
sonic(config-router)# no summary-address 2001::1/64 metric-type 1
sonic(config-router)# no summary-address 2001::1/64
```

#### Timers command
##### Adjusts OSPF6 LSA timers.

**Syntax**: `timers lsa min-arrival <delay>`

**Parameters**  :
- `delay` - Delay in milliseconds (0-600000)

**Command mode** : Router OSPF6 mode

**Usage**       : Use `no timers lsa min-arrival <delay>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-ospf6)# timers lsa min-arrival 1
sonic(config-ospf6)# no timers lsa min-arrival 1
```

##### Adjust OSPF6 Throttle spf timers.

**Syntax**: `timers throttle spf <delay> <hold> <maxhold>`

**Parameters**  :
- `delay`   - Delay (msec) from first change received till SPF calculation (0-600000)
- `hold`    - Initial hold time (msec) between consecutive SPF calculations (0-600000)
- `maxhold` - Maximum hold time (msec) (0-600000)

**Command mode** : Router OSPF6 mode

**Usage**       : Use `no timers throttle spf <delay> <hold> <maxhold>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config-ospf6)# timers throttle spf 1 1 1
sonic(config-ospf6)# no timers throttle spf 1 1 1
```

#### Write-Multiplier command

**Syntax**: `write-multiplier <num>`

**Parameters**  :
- `num` - Maximum number of interface serviced per write (1-100)

**Command mode** : Router OSPF6 mode

**Usage**       : Use `no write-multiplier <num>` to remove the configuration.

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
sonic(config-router)# write-multiplier 10
sonic(config-router)# no write-multiplier 10
```

### OSPF6 Interface commands
#### Area command
**Syntax**: `ipv6 ospf6 area <A.B.C.D|area-id>`

**Parameters**  :
- `A.B.C.D`     - OSPF6 area ID in IP address format
- `area-id`     - OSPF6 area ID as a decimal value (0-4294967295)

**Command mode** : Interface modes (Ethernet, PortChannel, VLAN and Loopback)

**Usage**       : Use `no ipv6 ospf6 area <A.B.C.D|area-id>` to remove the configuration.

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# ipv6 ospf6 area 1
sonic(conf-if-Ethernet8)# no ipv6 ospf6 area 1
sonic(conf-if-Ethernet8)# ipv6 ospf6 area 1.1.1.1
sonic(conf-if-Ethernet8)# no ipv6 ospf6 area 1.1.1.1
```

#### Authentication command
##### Authentication key-id
Enables authentication on this interface.

**Syntax**: `ipv6 ospf6 authentication key-id <key-id> hash-algo hmac-sha-1|hmac-sha-256|hmac-sha-384|hmac-sha-512|md5 key <passwd>`

**Parameters**  :
- `key-id`    - Key ID value (1-65535)
- `passwd`    - Password string (key)

**Command mode** : Interface modes (Ethernet, PortChannel, VLAN and Loopback)

**Usage**       : Use `no ipv6 ospf6 authentication key-id <key-id> hash-algo hmac-sha-1|hmac-sha-256|hmac-sha-384|hmac-sha-512|md5 key <passwd>` to remove the configuration.

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# ipv6 ospf6 authentication key-id 1 hash-algo hmac-sha-1 key key1
sonic(conf-if-Ethernet8)# no ipv6 ospf6 authentication key-id 1 hash-algo hmac-sha-1 key key1
```

##### Authentication keychain
Enables authentication on this interface.

**Syntax**: `ipv6 ospf6 authentication keychain <NAME>`

**Parameters**  :
- `NAME`    - Keychain name

**Command mode** : Interface modes (Ethernet, PortChannel, VLAN and Loopback)

**Usage**       : Use `no ipv6 ospf6 authentication keychain <NAME>` to remove the configuration.

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# ipv6 ospf6 authentication keychain kchan1
sonic(conf-if-Ethernet8)# no ipv6 ospf6 authentication keychain kchan1
```

#### Advertise command
Sets Advertising options.

**Syntax**: `ipv6 ospf6 advertise prefix-list <NAME>`

**Parameters**  :
- `NAME`    - Name of an IP prefix-list

**Command mode** : Router OSPF6 mode

**Usage**       : Use `no ipv6 ospf6 advertise prefix-list <NAME>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(config)# interface Ethernet 8
sonic(conf-if-Ethernet8)# ipv6 ospf6 advertise prefix-list prflst
sonic(conf-if-Ethernet8)# no ipv6 ospf6 advertise prefix-list prflst
```

#### BFD command
Enables BFD support.

**Syntax**: `ipv6 ospf6 bfd [profile <NAME>]`

**Parameters**  :
- `NAME` - BFD Profile name

**Command mode** : Interface modes (Ethernet, PortChannel, VLAN and Loopback)

**Usage**       : Use `no ipv6 ospf6 bfd [profile <profile_name>]` to remove the configuration.

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# ipv6 ospf6 bfd
sonic(conf-if-Ethernet8)# no ipv6 ospf6 bfd
sonic(conf-if-Ethernet8)# ipv6 ospf6 bfd profile bfd1
sonic(conf-if-Ethernet8)# no ipv6 ospf6 bfd profile bfd1
```

#### Cost command
Sets Interface cost.

**Syntax**: `ipv6 ospf6 cost <cost-id>`

**Parameters**  :
- `cost-id` - Interface cost (0-65535)

**Command mode** : Interface modes (Ethernet, PortChannel, VLAN and Loopback)

**Usage**       : Use `no ipv6 ospf6 cost <cost-id>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# ipv6 ospf6 cost 1
sonic(conf-if-Ethernet8)# no ipv6 ospf6 cost 1
```

#### Dead Interval command
Interval time after which a neighbor is declared down.

**Syntax**: `ipv6 ospf6 dead-interval <dinterval>`

**Parameters**  :
- `dinterval` - Delay interval in seconds (1-65535)

**Command mode** : Interface modes (Ethernet, PortChannel, VLAN and Loopback)

**Usage**       : Use `no ipv6 ospf6 dead-interval <dinterval>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# ipv6 ospf6 dead-interval 10
sonic(conf-if-Ethernet8)# no ipv6 ospf6 dead-interval 10
```

#### Hello Interval command
Time between HELLO packets.

**Syntax**: `ipv6 ospf6 hello-interval <hinterval>`

**Parameters**  :
- `hinterval` - Hello interval in seconds (1-65535)

**Command mode** : Interface modes (Ethernet, PortChannel, VLAN and Loopback)

**Usage**       : Use `no ipv6 ospf6 hello-interval <hinterval>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# ipv6 ospf6 hello-interval 2
sonic(conf-if-Ethernet8)# no ipv6 ospf6 hello-interval 2
```

#### Retransmit Interval command
Time between retransmitting lost link state advertisements.

**Syntax**: `ipv6 ospf6 retransmit-interval <rtinterval>`

**Parameters**  :
- `rtinterval` - Retransmit interval in seconds (1-65535)

**Command mode** : Interface modes (Ethernet, PortChannel, VLAN and Loopback)

**Usage**       : Use `no ipv6 ospf6 retransmit-interval <rtinterval>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# ipv6 ospf6 retransmit-interval 3
sonic(conf-if-Ethernet8)# no ipv6 ospf6 retransmit-interval 3
```

#### Transmit delay command
Sets Link state transmit delay.

**Syntax**: `ipv6 ospf6 transmit-delay <transdelay>`

**Parameters**  :
- `transdelay` - Transmit delay in seconds (1-3600)

**Command mode** : Interface modes (Ethernet, PortChannel, VLAN and Loopback)

**Usage**       : Use `no ipv6 ospf6 transmit-delay <transdelay>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# ipv6 ospf6 transmit-delay 5
sonic(conf-if-Ethernet8)# no ipv6 ospf6 transmit-delay 5
```

#### Instance ID command
Instance ID for this interface.

**Syntax**: `ipv6 ospf6 instance-id <instance-id>`

**Parameters**  :
- `instance-id` - Instance ID value (0-255)

**Command mode** : Interface modes (Ethernet, PortChannel, VLAN and Loopback)

**Usage**       : Use `no ipv6 ospf6 instance-id <instance-id>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# ipv6 ospf6 instance-id 1
sonic(conf-if-Ethernet8)# no ipv6 ospf6 instance-id 1
```

#### Interface MTU command
Sets Interface MTU.

**Syntax**: `ipv6 ospf6 ifmtu <mtu>`

**Parameters**  :
- `mtu` - OSPFv3 Interface MTU (1-65535)

**Command mode** : Interface modes (Ethernet, PortChannel, VLAN and Loopback)

**Usage**       : Use `no ipv6 ospf6 ifmtu <mtu>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# ipv6 ospf6 ifmtu 9100
sonic(conf-if-Ethernet8)# no ipv6 ospf6 ifmtu 9100
```

#### MTU ignore command
Disables MTU mismatch detection on this interface.

**Syntax**: `ipv6 ospf6 mtu-ignore`

**Parameters**  : None

**Command mode** : Interface modes (Ethernet, PortChannel, VLAN and Loopback)

**Usage**       : Use `no ipv6 ospf6 mtu-ignore` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# ipv6 ospf6 mtu-ignore
sonic(conf-if-Ethernet8)# no ipv6 ospf6 mtu-ignore
```

#### Network type command
Sets Network Type.

**Syntax**: `ipv6 ospf6 network broadcast|point-to-point`

**Parameters**  : None

**Command mode** : Interface modes (Ethernet, PortChannel, VLAN and Loopback)

**Usage**       : Use `no ipv6 ospf6 network broadcast|point-to-point` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# ipv6 ospf6 network broadcast
sonic(conf-if-Ethernet8)# no ipv6 ospf6 network broadcast
sonic(conf-if-Ethernet8)# ipv6 ospf6 network point-to-point
sonic(conf-if-Ethernet8)# no ipv6 ospf6 network point-to-point
```

#### Passive command
Passive interface; no adjacency will be formed on this interface.

**Syntax**: `ipv6 ospf6 passive`

**Parameters**  : None

**Command mode** : Interface modes (Ethernet, PortChannel, VLAN and Loopback)

**Usage**       : Use `no ipv6 ospf6 passive` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# ipv6 ospf6 passive
sonic(conf-if-Ethernet8)# no ipv6 ospf6 passive
```

#### Priority command
Sets Router priority.

**Syntax**: `ipv6 ospf6 priority <prio>`

**Parameters**  :
- `prio` - Priority (0-255)

**Command mode** : Interface modes (Ethernet, PortChannel, VLAN and Loopback)

**Usage**       : Use `no ipv6 ospf6 priority <prio>` to remove the configuration.

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# ipv6 ospf6 priority 5
sonic(conf-if-Ethernet8)# no ipv6 ospf6 priority 5
```

### OSPF6 Show commands
#### Show Running-config command
Displays ospf6 running configs.

**Syntax**: `show running-config ospf6`

**Parameters**  : None

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# show running-config ospf6
!
router ospf6
 ospf6 router-id 194.0.0.2
 interface Vlan50 area 1
sonic# show running-config interface Vlan 50
!
interface Vlan 50
 ipv6 address 50::2/64
 ipv6 use-link-local-only
sonic# show running-config interface Ethernet 47
!
interface Ethernet 47
 fec none
 mtu 9100
 no shutdown
 speed auto
 switchport trunk allowed vlan add 50
sonic#
```

#### Displays ospf6 information.

**Syntax**: `show ipv6 ospf6 [vrf <vrfname>|all]`

**Parameters**  :
- `vrfname` - VRF Name (Max: 15 characters, prefixed with Vrf)

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# show ipv6 ospf6
 OSPFv3 Routing Process (0) with Router-ID 194.0.0.2
 Running 00:12:07
 LSA minimum arrival 1000 msecs
 Initial SPF scheduling delay 0 millisec(s)
 Minimum hold time between consecutive SPFs 50 millsecond(s)
 Maximum hold time between consecutive SPFs 5000 millsecond(s)
 Hold time multiplier is currently 1
 SPF algorithm last executed 00:11:12 ago, reason R+, R-
 Last SPF duration 0 sec 197 usec
 SPF timer is inactive
 Number of AS scoped LSAs is 0
 Number of areas in this router is 1

 Area 1
     Number of Area scoped LSAs is 4
     Interface attached to this area: Vlan50
SPF last executed 672.574877s ago

sonic#
```

#### Area show command
Displays Area information.

**Syntax**: `show ipv6 ospf6 [vrf <vrfname>|all] area <A.B.C.D> spf tree`

**Parameters**  :
- `vrfname` - VRF Name (Max: 15 characters, prefixed with Vrf)
- `A.B.C.D` - Area ID (as an IPv4 notation)

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# show ipv6 ospf6 area 0.0.0.1 spf tree
+-194.0.0.2 [0]
   +-194.0.0.2 Net-ID: 0.0.0.66 [10]
      +-194.0.0.1 [10]

```

#### Border-routers show command
Displays routing table for ABR and ASBR.

**Syntax**: `show ipv6 ospf6 [vrf <vrfname>|all] border-routers [<A.B.C.D>|detail]`

**Parameters**  :
- `vrfname` - VRF Name (Max: 15 characters, prefixed with Vrf)
- `A.B.C.D` - Router ID

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
```

#### Database summary show command
##### Displays Link state database.

**Syntax**: `show ipv6 ospf6 [vrf <vrfname>|all] database [router|network|inter-prefix|inter-router|as-external|group-membership|type-7|link|intra-prefix[[* <E.F.G.H>|<A.B.C.D> self-originated|linkstate-id <A.B.C.D>] [detail|dump|internal]] | [<A.B.C.D> <E.F.G.H>|adv-router <E.F.G.H> linkstate-id <A.B.C.D> [dump|internal]]]`

**Parameters**  :
- `vrfname`     - VRF Name (Max: 15 characters, prefixed with Vrf)
- `A.B.C.D`     - Link State ID (as an IP address)
- `E.F.G.H`     - Advertising Router (as an IP address)

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# show ipv6 ospf6 database

        Area Scoped Link State Database (Area 1)

Type LSId           AdvRouter       Age   SeqNum                        Payload
Rtr  0.0.0.0        194.0.0.1        12 80000003             194.0.0.2/0.0.0.66
Rtr  0.0.0.0        194.0.0.2        11 80000009             194.0.0.2/0.0.0.66
Net  0.0.0.66       194.0.0.2        11 80000001                      194.0.0.2
Net  0.0.0.66       194.0.0.2        11 80000001                      194.0.0.1
INP  0.0.0.0        194.0.0.2      3600 8000000a                        50::/64
INP  0.0.0.66       194.0.0.2        11 80000001                        50::/64

        I/F Scoped Link State Database (I/F Vlan50 in Area 1)

Type LSId           AdvRouter       Age   SeqNum                        Payload
Lnk  0.0.0.1        194.0.0.1        22 80000001           fe80::213:1ff:fe00:1
Lnk  0.0.0.66       194.0.0.2       392 8000000e      fe80::36ad:61ff:fef1:a56c
Lnk  0.0.0.66       194.0.0.2       392 8000000e                           50::

        AS Scoped Link State Database

Type LSId           AdvRouter       Age   SeqNum                        Payload


sonic# show ipv6 ospf6 database router
  *                Any Link state ID
  A.B.C.D          Specify Link state ID as IPv4 address notation
  adv-router       Search by Advertising Router
  detail           Display details of LSAs
  dump             Dump LSAs
  internal         Display LSA's internal information
  linkstate-id     Search by Link state ID
  self-originated  Display Self-originated LSAs
  |                Pipe through a command
  <cr>

sonic# show ipv6 ospf6 database router detail

        Area Scoped Link State Database (Area 1)

Age:   27 Type: Router
Link State ID: 0.0.0.0
Advertising Router: 194.0.0.1
LS Sequence Number: 0x80000003
CheckSum: 0x3513 Length: 40
Duration: 00:00:20
    Bits: -------- Options: --|R|-|--|E|V6
    Type: Transit-Network Metric: 10
    Interface ID: 0.0.0.1
    Neighbor Interface ID: 0.0.0.66
    Neighbor Router ID: 194.0.0.2

Age:   26 Type: Router
Link State ID: 0.0.0.0
Advertising Router: 194.0.0.2
LS Sequence Number: 0x80000009
CheckSum: 0xb44b Length: 40
Duration: 00:00:25
    Bits: -------- Options: --|R|-|--|E|V6
    Type: Transit-Network Metric: 10
    Interface ID: 0.0.0.66
    Neighbor Interface ID: 0.0.0.66
    Neighbor Router ID: 194.0.0.2

sonic#
```

##### Displays Any Link state, Self-originated and Advertising Router database.

**Syntax**: `show ipv6 ospf6 [vrf <vrfname>|all] database [[[* <A.B.C.D> <E.F.G.H>|self-originated|adv-router <E.F.G.H> linkstate-id <A.B.C.D>] [detail|dump|internal]] | [ * * <E.F.G.H>|adv-router * <E.F.G.H>> detail|dump|internal]]`

**Parameters**  :
- `vrfname`     - VRF Name (Max: 15 characters, prefixed with Vrf)
- `A.B.C.D`     - Link State ID (as an IP address)
- `E.F.G.H`     - Advertising Router (as an IP address)

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# show ipv6 ospf6 database * 0.0.0.66 194.0.0.2

        Area Scoped Link State Database (Area 1)

Type LSId           AdvRouter       Age   SeqNum                        Payload
Net  0.0.0.66       194.0.0.2       170 80000001                      194.0.0.2
Net  0.0.0.66       194.0.0.2       170 80000001                      194.0.0.1
INP  0.0.0.66       194.0.0.2       170 80000001                        50::/64

        I/F Scoped Link State Database (I/F Vlan50 in Area 1)

Type LSId           AdvRouter       Age   SeqNum                        Payload
Lnk  0.0.0.66       194.0.0.2       551 8000000e      fe80::36ad:61ff:fef1:a56c
Lnk  0.0.0.66       194.0.0.2       551 8000000e                           50::

        AS Scoped Link State Database

Type LSId           AdvRouter       Age   SeqNum                        Payload

sonic#
```

#### Interface show command
Displays Interface information.

**Syntax**: `show ipv6 ospf6 [vrf <vrfname>|all] interface [[<IFNAME>|traffic] [prefix [<A::B>|<A::B/M match [detail]]]] | [traffic <IFNAME>]> `

**Parameters**  :
- `vrfname` - VRF Name (Max: 15 characters, prefixed with Vrf)
- `IFNAME`  - Interface name(e.g. Ethernet1, Vlan1, PortChannel1..)
- `A::B`    - Display the route bestmatches the address (IPv6 address)
- `A::B/M`  - Display the route matches address and mask (IPv6 address)

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# show ipv6 ospf6 interface traffic Vlan50

Interface       HELLO            DB-Desc         LS-Req           LS-Update        LS-Ack
                Rx/Tx            Rx/Tx            Rx/Tx            Rx/Tx            Rx/Tx
--------------------------------------------------------------------------------------------
Vlan50          133/1127          10/5             0/2             6/2             2/0

sonic# show ipv6 ospf6 interface prefix detail
Destination: 50::/64
Destination type: Network
Installed Time: 01:40:00 ago
  Changed Time: 01:40:00 ago
Lock: 2 Flags: BA--
Memory: prev: 0x0 this: 0x5563573cb910 next: 0x0
Associated Area: 0.0.0.1
Path Type: Intra-Area
LS Origin: 0x0000 Id: 0.0.0.0 Adv: 0.0.0.0
Options: --|-|-|--|-|--
Router Bits: --------
Prefix Options: xxx
Metric Type: 0
Metric: 10 (0)
Paths count: 0
Nexthop count: 1
Nexthop:
  ::1 Vlan50


sonic#
```

#### Link state show command
Displays linkstate routing table.

**Syntax**: `show ipv6 ospf6 [vrf <vrfname>|all] linkstate detail|network <A.B.C.D> <E.F.G.H>|router <A.B.C.D>`

**Parameters**  :
- `vrfname`     - VRF Name (Max: 15 characters, prefixed with Vrf)
- `A.B.C.D`     - Specify Router-ID as IPv4 address notation
- `E.F.G.H`     - Specify Link state ID as IPv4 address notation

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# show ipv6 ospf6 linkstate router 194.0.0.1

        SPF Result in Area 1

Destination: 194.0.0.1
Destination type: Linkstate
Installed Time: 00:04:37 ago
  Changed Time: 00:04:37 ago
Lock: 2 Flags: BA--
Memory: prev: 0x0 this: 0x5563573ca0a0 next: 0x5563573be300
Associated Area: 0.0.0.0
Path Type: Intra-Area
LS Origin: Router Id: 0.0.0.0 Adv: 194.0.0.1
Options: --|R|-|--|E|V6
Router Bits: --------
Prefix Options: xxx
Metric Type: 1
Metric: 10 (1)
Paths count: 0
Nexthop count: 1
Nexthop:
  fe80::213:1ff:fe00:1 Vlan50

sonic#
```

#### Neighbor show command
Displays Neighbor list.

**Syntax**: `show ipv6 ospf6 [vrf <vrfname>|all] neighbor [<A.B.C.D>|detail|drchoice]`

**Parameters**  :
- `vrfname`   - VRF Name (Max: 15 characters, prefixed with Vrf)
- `A.B.C.D`   - Specify Router-ID as IPv4 address notation

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# show ipv6 ospf6 neighbor
Neighbor ID     Pri    DeadTime    State/IfState         Duration I/F[State]
194.0.0.1         0    00:00:31     Full/DROther         00:05:08 Vlan50[DR]

sonic#
```

#### Redistribute show command
Displays redistributing External information.

**Syntax**: `show ipv6 ospf6 [vrf <vrfname>|all] redistribute`

**Parameters**  :
- `vrfname` - VRF Name (Max: 15 characters, prefixed with Vrf)

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
```

#### Routing table show command
Displays Routing table.

**Syntax**: `show ipv6 ospf6 [vrf <vrfname>|all] route [external-1|external-2|inter-area|intra-area [detail]] | [<A::B>|summary] | [<A::B/M> [longer|match [detail]]] | [detail]`

**Parameters**  :
- `vrfname` - VRF Name (Max: 15 characters, prefixed with Vrf)
- `A::B`    - Specify IPv6 address
- `A::B/M`  - Specify IPv6 prefix

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# show ipv6 ospf6 route
*N IA 50::/64                        ::                        Vlan50 00:05:31

sonic#
sonic# show ipv6 ospf6 route summary
Number of OSPFv3 routes: 1
Number of Destination: 1
Number of Alternative routes: 0
Number of Equal Cost Multi Path: 0
Number of Intra-Area routes: 1
Number of Inter-Area routes: 0
Number of External-1 routes: 0
Number of External-2 routes: 0

sonic#
```

#### SPF show command
##### Displays Shortest Path First calculation.

**Syntax**: `show ipv6 ospf6 [vrf <vrfname>|all] spf tree`

**Parameters**  :
- `vrfname`     - VRF Name (Max: 15 characters, prefixed with Vrf)

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# show ipv6 ospf6 spf tree
+-194.0.0.2 [0]
   +-194.0.0.2 Net-ID: 0.0.0.66 [10]
      +-194.0.0.1 [10]

sonic#
```

##### Displays SPF calculation for another router's.

**Syntax**: `show ipv6 ospf6 [vrf <vrfname>|all] simulate spf-tree <A.B.C.D> area <E.F.G.H>`

**Parameters**  :
- `vrfname`     - VRF Name (Max: 15 characters, prefixed with Vrf)
- `A.B.C.D`     - Specify root's router-id to calculate another router's SPF tree
- `E.F.G.H`     - Area ID (as an IPv4 notation)

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# show ipv6 ospf6 simulate spf-tree 194.0.0.2 area 0.0.0.1
+-194.0.0.2 [0]
   +-194.0.0.2 Net-ID: 0.0.0.66 [10]
      +-194.0.0.1 [10]

sonic#
```

#### Zebra show command
Displays Zebra information.

**Syntax**: `show ipv6 ospf6 zebra`

**Parameters**  : None

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# show ipv6 ospf6 zebra
Zebra Information
  fail: 0
  redistribute default: 0
  redistribute: ospf6

sonic#
```

#### Graceful Restart helper show command
OSPF6 Graceful Restart command

**Syntax**: `show ipv6 ospf6 graceful-restart helper [detail]`

**Parameters**  : None

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
```

#### External summary addresses show command
Displays external summary addresses.

**Syntax**: `show ipv6 ospf6 [vrf <vrfname>|all]  summary-address [detail]`

**Parameters**  :
- `vrfname` - VRF Name (Max: 15 characters, prefixed with Vrf)

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
```

#### VRFs show command
Displays OSPF VRFs Information.

**Syntax**: `show ipv6 ospf6 vrfs`

**Parameters**  : None

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
```

### OSPF6 Clear commands
#### Interface clear command
Clears OSPF6 Interface information

**Syntax**: `clear ipv6 ospf6 [vrf <vrfname>] interface [<L3intf>]`

**Parameters**  :
- `vrfname` - VRF Name (Max: 15 characters, prefixed with Vrf)
- `L3intf`  - L3 Interface name

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
sonic# clear ipv6 ospf6 interface
sonic# clear ipv6 ospf6 vrf Vrf-1 interface Vlan10
sonic# clear ipv6 ospf6 interface Ethernet8
```

#### Process clear command
Clears OSPF6 Interface information

**Syntax**: `clear ipv6 ospf6 process`

**Parameters**  : None

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# clear ipv6 ospf6 process
```

#### Interface auth-counters clear command
Clears OSPF6 Interface authentication rx/tx drop counters.

**Syntax**: `clear ipv6 ospf6 [vrf <vrfname>] auth-counters interface [<L3intf>]`

**Parameters**  :
- `vrfname` - VRF Name (Max: 15 characters, prefixed with Vrf)
- `L3intf`  - L3 Interface name

**Command mode** : EXEC

**Click command** : None

**Supported Releases** :  2.0 or later

**Example**
```
sonic# clear ipv6 ospf6 auth-counters interface
sonic# clear ipv6 ospf6 auth-counters interface Vlan10
sonic# clear ipv6 ospf6 vrf Vrf-1 auth-counters interface Ethernet8
```

### OSPF6 Debug commands
#### ABR,ASBR,Flooding and Interface command
Enables debugs for ospf6 abr, asbr, flooding function and interface information.

**Syntax**: `debug ospf6 abr|asbr|flooding|interface`

**Parameters**  : None

**Command mode** : EXEC

**Click command** : None

**Usage**       : Use `no debug ospf6 [abr|asbr|flooding|interface]` to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# debug ospf6 abr
sonic# no debug ospf6 abr
sonic#
sonic# debug ospf6 asbr
sonic# no debug ospf6 asbr
sonic#
sonic# debug ospf6 flooding
sonic# no debug ospf6 flooding
sonic#
sonic# debug ospf6 interface
sonic# no debug ospf6 interface
sonic#
sonic# no debug ospf6
sonic#
```

#### Border routers command
Enables debugs for ospf6 border router.

**Syntax**: `debug ospf6 border-routers [area-id <A.B.C.D>|router-id <E.F.G.H>]`

**Parameters**  :
- `A.B.C.D` - Specify Area-ID
- `E.F.G.H` - Specify border-router's router-id

**Command mode** : EXEC

**Click command** : None

**Usage**       : Use `no debug ospf6 [border-routers [area-id|router-id]]` to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# debug ospf6 border-routers area-id 0.0.0.1
sonic# no debug ospf6 border-routers area-id
sonic#
```

#### Link State Advertisements command
Enables debugs for ospf6 Link State Advertisements.

**Syntax**: `debug ospf6 lsa aggregation|all|router|network|inter-prefix|inter-router|as-external|link|intra-prefix|unknown [originate|examine|flooding]`

**Parameters**  : None

**Command mode** : EXEC

**Click command** : None

**Usage**       : Use `no debug ospf6 [lsa aggregation|all|router|network|inter-prefix|inter-router|as-external|link|intra-prefix|unknown [originate|examine|flooding]]` to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# debug ospf6 lsa intra-prefix examine
sonic# no debug ospf6 lsa intra-prefix examine
sonic#
```

#### Message command
Enables debugs for ospf6 message.

**Syntax**: `debug ospf6 message unknown|hello|dbdesc|lsreq|lsupdate|lsack|all [send|recv|send-hdr|recv-hdr]`

**Parameters**  : None

**Command mode** : EXEC

**Click command** : None

**Usage**       : Use `no debug ospf6 [message unknown|hello|dbdesc|lsreq|lsupdate|lsack|all [send|recv|send-hdr|recv-hdr]]` to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# debug ospf6 message dbdesc recv
sonic# no debug ospf6 message dbdesc recv
sonic#
```

#### Neighbor command
Enables debugs for ospf6 neighbor.

**Syntax**: `debug ospf6 neighbor [event|state]`

**Parameters**  : None

**Command mode** : EXEC

**Click command** : None

**Usage**       : Use `no debug ospf6 [neighbor [event|state]]` to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# debug ospf6 neighbor state
sonic# no debug ospf6 neighbor state
sonic#
```

#### Route command
Enables debugs for ospf6 routes.

**Syntax**: `debug ospf6 route all|table|intra-area|inter-area|memory`

**Parameters**  : None

**Command mode** : EXEC

**Click command** : None

**Usage**       : Use `no debug ospf6 [route all|table|intra-area|inter-area|memory]` to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# debug ospf6 route inter-area
sonic# no debug ospf6 route inter-area
sonic#
```

#### SPF command
Enables debugs for ospf6 spf calculation.

**Syntax**: `debug ospf6 spf database|process|time`

**Parameters**  : None

**Command mode** : EXEC

**Click command** : None

**Usage**       : Use `no debug ospf6 [spf database|process|time]` to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# debug ospf6 spf database
sonic# no debug ospf6 spf database
sonic#
```

#### Zebra command
Enables debugs for zebra information.

**Syntax**: `debug ospf6 zebra [send|recv]`

**Parameters**  : None

**Command mode** : EXEC

**Click command** : None

**Usage**       : Use `no debug ospf6 [zebra [send|recv]]` to remove the configuration.

**Supported Releases** :  1.1.0 or later

**Example**
```
sonic# debug ospf6 zebra send
sonic# no debug ospf6 zebra send
sonic#
```

#### Graceful Restart command
Enables debugs for Graceful Restart.

**Syntax**: `debug ospf6 graceful-restart`

**Parameters**  : None

**Usage**       : Use `no debug ospf6 [graceful-restart]` to remove the configuration.

**Supported Releases** :  2.0 or later

**Example**
```
sonic# debug ospf6 graceful-restart
sonic# no debug ospf6 graceful-restart
```

## POE
**Note** : The feature is supported on PoE platforms only.

### POE Config Commands

### POE global config commands
#### poe disable
Enable/Disable the PoE globally.

**Note** : PoE is enabled by default at global level.

**syntax**: `poe disable`

**Command mode** : CONFIG

**Click command** : 
```
root@sonic:~# config poe global enable 
root@sonic:~# config poe global disable
```
**Usage**       : Use `no poe disable` to enable the PoE on global level.

**Supported Releases** :  2.0 or later

**Example**
```
sonic(config)# poe disable
sonic(config)# no poe disable
sonic(config)#
```

#### power-management
Used to configure PoE global power-management.

**syntax**: `poe power-management {dynamic-with-priority | dynamic-without-priority | static-with-priority | static-without-priority}`

**Command mode** : CONFIG

**Click command** : 
```
root@sonic:~# config poe global power-management
dynamic-without-priority  static-without-priority
dynamic-with-priority     static-with-priority
root@sonic:~# config poe global power-management dynamic-with-priority
root@sonic:~#
```

**Usage**       : Use `no poe power-management` to set default value of dynamic-with-priority.

**Supported Releases** :  2.0 or later

**Example**
```
sonic(config)# poe power-management dynamic-without-priority
sonic(config)# no poe power-management
sonic(config)#
```

#### guard-band
Used to configure PoE global guard-band.

**syntax**: `poe guard-band <5-90 watts>`

**Command mode** : CONFIG

**Click command** : `root@sonic:~# config poe global guard-band 50`

**Usage**       : Use `no poe guard-band` to set the default value of 30.

**Supported Releases** :  2.0 or later

**Example**
```
sonic(config)# poe guard-band 50
sonic(config)# no poe guard-band
sonic(config)#
```

### POE interface level config commands
#### poe enable
Enable/Disable PoE at port level.

**syntax**: `poe enable`

**Command mode** : Physical interface

**Click command** : 
```
root@sonic:~# config poe port Ethernet8 enable
root@sonic:~# config poe port Ethernet8 disable
```

**Usage**       : Use `no poe enable` to disable the PoE in an interface.

**Supported Releases** :  2.0 or later

**Example**
```
sonic(config)# interface Ethernet 8
sonic(conf-if-Ethernet8)# poe enable
sonic(conf-if-Ethernet8)# no poe enable
sonic(conf-if-Ethernet8)#
```

#### power-via-mdi
Enable/Disable the power via media discoverable interface (LLDP).

**syntax**: `poe power-via-mdi enable`

**Command mode** : Physical interface

**Click command** : 
```
root@sonic:~# config poe port Ethernet8 power-via-mdi enable
root@sonic:~# config poe port Ethernet8 power-via-mdi disable
```

**Usage**       : Use `no poe power-via-mdi enable` to disable the power-via-mdi in an interface.

**Supported Releases** :  2.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# poe power-via-mdi enable
sonic(conf-if-Ethernet8)# no poe power-via-mdi enable
sonic(conf-if-Ethernet8)#
```

#### poe reset
Port reset to clear the error status.

**syntax**: `poe reset {auto <10-60 seconds> | manual}`

**Command mode** : Physical interface

**Click command** : 
```
root@sonic:~# config poe port Ethernet8 reset auto 30
root@sonic:~# config poe port Ethernet8 reset manual
```

**Usage**       : Use `no poe reset` to set the default value of manual.

**Supported Releases** :  2.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# poe reset auto 30
sonic(conf-if-Ethernet8)# no poe reset
sonic(conf-if-Ethernet8)# poe reset manual
sonic(conf-if-Ethernet8)#
```

#### detection-type
Used to configure the detection-type.

**syntax**: `poe detection-type {two-point-dot3af | two-point-dot3af-legacy | four-point-dot3af | four-point-dot3af-legacy | legacy-only}`

**Command mode** : Physical interface

**Click command** : 
```
root@sonic:~# config poe port Ethernet8 detection-type
four-point-dot3af         legacy-only               two-point-dot3af-legacy
four-point-dot3af-legacy  two-point-dot3af
root@sonic:~# config poe port Ethernet8 detection-type two-point-dot3af
```

**Usage**       : Use `no poe detection-type` to set the default value of four-point-dot3af.

**Supported Releases** :  2.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# poe detection-type four-point-dot3af-legacy
sonic(conf-if-Ethernet8)# no poe detection-type
sonic(conf-if-Ethernet8)#
```

#### power-up-mode
Used to configure the power-up-mode.

**syntax**: `poe power-up-mode {dot3af | pre-dot3at | dot3at | pre-dot3bt | dot3bt-type3  | dot3bt-type4  | high-inrush}`

**Command mode** : Physical interface

**Click command** : 
```
root@sonic:~# config poe port Ethernet8 power-up-mode
dot3af        dot3bt-type3  high-inrush   pre-dot3bt
dot3at        dot3bt-type4  pre-dot3at
root@sonic:~# config poe port Ethernet8 power-up-mode dot3bt-type4
```

**Usage**       : Use `no poe power-up-mode` to set the default value of dot3bt-type4.

**Supported Releases** :  2.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# poe power-up-mode pre-dot3at
sonic(conf-if-Ethernet8)# no poe power-up-mode
sonic(conf-if-Ethernet8)#
```

#### priority
Used to configure the priority and this configuration will be effective based on the power-management.

**syntax**: `poe priority {critical | high | medium | low}`

**Command mode** : Physical interface

**Click command** : 
```
root@sonic:~# config poe port Ethernet8 priority
critical  high      low       medium
root@sonic:~# config poe port Ethernet8 priority medium
```

**Usage**       : Use `no poe priority` to set the default value of low.

**Supported Releases** :  2.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# poe priority medium
sonic(conf-if-Ethernet8)# no poe priority
sonic(conf-if-Ethernet8)#

```

#### power-threshold
Used to configure the power-threshold.

**syntax**: `poe power-threshold {power-up-based | class-based | user-defined <0.0-45.0 watts>}`

**Command mode** : Physical interface

**Click command** : 
```
root@sonic:~# config poe port Ethernet8 power-threshold user-defined 5
root@sonic:~# config poe port Ethernet8 power-threshold power-up-based
```

**Usage**       : Use `no poe power-threshold` to set the default value of class-based.

**Supported Releases** :  2.0 or later

**Example**
```
sonic(conf-if-Ethernet8)# poe power-threshold user-defined
  1.0..45.0  Enter threshold value (in watts)

sonic(conf-if-Ethernet8)# poe power-threshold user-defined 1.3
% Error: Threshold must be multiple of 0.2
sonic(conf-if-Ethernet8)# poe power-threshold user-defined 1.4
sonic(conf-if-Ethernet8)# no poe power-threshold
sonic(conf-if-Ethernet8)# poe power-threshold power-up-based
sonic(conf-if-Ethernet8)#

```

### POE Clear commands
#### clear counters
Used to clear the port counters information and the interface name should be valid.

**syntax**: `clear poe port counters <eth-interface-name>`

**Command mode** : EXEC

**Click command** : `root@sonic:~# sonic-clear poe port counters Ethernet8`

**Usage**       : Used to clear the port counters information in an interface.

**Supported Releases** :  2.0 or later

**Example**
```
sonic# clear poe port counters Ethernet 8
sonic#
```

#### clear error-status
Used to clear the error-staus which are occured. 
This command can be used only when the port is in error state and it's applicable only when poe reset is configured as manual.

**syntax**: `clear poe port error-status <eth-interface-name>`

**Command mode** : EXEC

**Click command** : `root@sonic:~# sonic-clear poe port error-status Ethernet8`

**Usage**       : Used to clear the error-status information in an interface.

**Supported Releases** :  2.0 or later

**Example**
```
sonic# clear poe port error-status Ethernet 8
```

#### skip-poe command
**syntax**: `reboot skip-poe`

**Command mode** : EXEC

**Click command** : `root@sonic:~# reboot skip-poe`

**Usage**       : Use this option to skip the rebooting of PoE component  which will ensure uninterrupted supply of power to connected Powered Devices(PD).

**Supported Releases** :  2.0 or later

**Example**
```
sonic# reboot skip-poe
Reboot, continue? [y/N]: y
Save running configuration into startup configuration, continue? [y/N]: y
```

### POE Show commands
#### global summary
Shows PoE global parameters summary

**syntax**: `show poe global summary`

**Command mode** : EXEC

**Click command** : `root@sonic:~# show poe global summary`

**Usage**       : Used to display the poe global summary.

**Supported Releases** :  2.0 or later

**Example**
```
sonic# show poe global summary
Status : enabled
Controller mode : unknown
Power management mode : static-with-priority
Total power allocated : 90.65%
Guard band : 30 watts
sonic#
```

#### global detail
Shows PoE global detail.

**syntax**: `show poe global detail`

**Command mode** : EXEC

**Click command** : `root@sonic:~# show poe global detail`

**Usage**       : Used to display the poe global detail.

**Supported Releases** :  2.0 or later

**Example**
```
sonic# show poe global detail
Status : enabled
Controller mode : unknown
Power management mode : static-with-priority
Total power available : 1070 watts
Total power allocated : 970 watts
Guard band : 30 watts
System reset cause : Unknown
Controller type : Nuvoton NUC029ZPoE Mircontroller
Controller status : Ready
Firmware version : 6.0
Ext firmware version : 0.7
```

#### global pse detail
Shows PoE global PSE detail.

**syntax**: `show poe global pse detail`

**Command mode** : EXEC

**Click command** : `root@sonic:~# show poe global pse detail`

**Usage**       : Used to display the poe global detail.

**Supported Releases** :  2.0 or later

**Example**
```
sonic# show poe global pse detail
----------------------------------------------------------------------
ID       Type        Voltage(V)    OTP version   HW address
----------------------------------------------------------------------
0        Generic     54.5          0.0           0x20
1        Generic     54.4          0.0           0x22
2        Generic     54.4          0.0           0x24
3        Generic     54.4          0.0           0x26
4        Generic     54.7          0.0           0x28
5        Generic     54.6          0.0           0x2a
6        Generic     54.5          0.0           0x2c
7        Generic     54.7          0.0           0x2e
8        Generic     54.4          0.0           0x30
9        Generic     54.3          0.0           0x32
10       Generic     54.3          0.0           0x34
11       Generic     54.3          0.0           0x36
```

#### port counters
Shows PoE port counters.

**syntax**: `show poe port counters [<eth-interface-name>]`

**Command mode** : EXEC

**Click command** : `root@sonic:~# show poe port counters`

**Usage**       : Used to display the poe port counters information.

**Supported Releases** :  2.0 or later

**Example**
```
sonic# show poe port counters
---------------------------------------------------------------------------------------------
Port            Mps-absent     Overload      Short      Power-denied    Invalid-signature
---------------------------------------------------------------------------------------------
Ethernet2       160            0             0          0               37
Ethernet3       178            3             0          27              120
Ethernet4       1              13            0          18              104
Ethernet5       2              0             0          7               39
Ethernet6       2              0             0          11              38
Ethernet7       2              0             0          4               108
Ethernet8       2              0             0          15              173
Ethernet9       1              0             0          6               102
Ethernet10      2              0             0          7               76
Ethernet11      2              0             0          14              215
Ethernet15      2              0             0          4               231
Ethernet16      1              0             0          59              216
Ethernet17      10             3             0          204             74
Ethernet18      6              1             0          45              129
Ethernet19      0              0             0          188             128
Ethernet20      0              0             0          194             78
```

#### port summary
Shows PoE port summary.

**syntax**: `show poe port summary {<eth-interface-name>}`

**Command mode** : EXEC

**Click command** : `root@sonic:~# show poe port summary`

**Usage**       : Used to display the poe port summary.

**Supported Releases** :  2.0 or later

**Example**
```
sonic# show poe port summary
P2CH : Primary 2 pair
S2CH : Secondary 2 pair
PS4CH : Both 4 pair
----------------------------------------------------------------------------------------------------------------------------------------
Port        State              Priority  Type:Class    Category   Channel     Power(w)  Threshold(w)  LLDP       LLDP Requested Power(w)
----------------------------------------------------------------------------------------------------------------------------------------
Ethernet2   Open Circuit       low       NA            PD None    NA          0         0             Enabled    -
Ethernet3   Delivering Power   low       Type4:Class8  IEEE PD    PS4CH-90W   2         97            Enabled    71.3
Ethernet4   Delivering Power   medium    Type4:Class8  IEEE PD    PS4CH-90W   93.1      97            Disabled   -
Ethernet5   Delivering Power   medium    Type4:Class8  IEEE PD    PS4CH-90W   91.4      97            Disabled   -
Ethernet6   Delivering Power   medium    Type4:Class8  IEEE PD    PS4CH-90W   89.5      97            Disabled   -
Ethernet7   Delivering Power   medium    Type4:Class8  IEEE PD    PS4CH-90W   90.7      97            Disabled   -
Ethernet8   Delivering Power   medium    Type4:Class8  IEEE PD    PS4CH-90W   92        97            Disabled   -
Ethernet9   Delivering Power   medium    Type4:Class8  IEEE PD    PS4CH-90W   89.2      97            Disabled   -
Ethernet10  Delivering Power   medium    Type4:Class8  IEEE PD    PS4CH-90W   90.1      97            Disabled   -
Ethernet11  Delivering Power   medium    Type4:Class8  IEEE PD    PS4CH-90W   92.3      97            Disabled   -
Ethernet15  Delivering Power   medium    Type4:Class8  IEEE PD    PS4CH-90W   92.2      97            Disabled   -
Ethernet16  Delivering Power   medium    Type4:Class8  IEEE PD    PS4CH-90W   91.3      97            Disabled   -
Ethernet17  Open Circuit       medium    NA            PD None    NA          0         0             Disabled   -
Ethernet18  Open Circuit       medium    NA            PD None    NA          0         0             Disabled   -
Ethernet19  Open Circuit       low       NA            PD None    NA          0         0             Disabled   -
Ethernet20  Open Circuit       low       NA            PD None    NA          0         0             Disabled   -
sonic#
```

#### port detail
Shows PoE port detail.

**syntax**: `show poe port detail {<eth-interface-name>}`

**Command mode** : EXEC

**Click command** : `root@sonic:~# show poe port detail`

**Usage**       : Used to display the poe port detail.

**Supported Releases** :  2.0 or later

**Example**
```
sonic# show poe port detail Ethernet 3
P2CH : Primary 2 pair
S2CH : Secondary 2 pair
PS4CH : Both 4 pair
-------------------------------------------------------------
Port : Ethernet3
    PSE Map : device 0 channel 4, 6
    Port LLDP State : Enabled
    PD LLDP State : disabled
    Priority : low
    Detection type : four-point-dot3af
    Power up mode : dot3bt-type4
    Powered channel : both
    Power State : Delivering Power
    PD class : Type4:Class8
    PD category : IEEE PD
    Channel Status: PS4CH-90W
    PD signature : Single
    Voltage : 54 V
    Current : 0.038A
    Temperature : 30.0C Degree Celcius
    Power Consumed: 2 W
    Primary Power Consumed: 1 W
    Secondary Power Consumed: 1 W
    Maximum power threshold: 97 W
    Dynamic power limit: 86.0 W
    Auto class power: 0.0 W
    LLDP Requested Power: 71.3 W
```

#### running-config poe

**syntax**: `show running-config poe`

**Command mode** : EXEC

**Click command** : None

**Usage**       : Used to display the running configurations of PoE.

**Supported Releases** :  2.0 or later

**Example**
```
sonic# show running-config poe
!
!
poe disable
poe guard-band 50.0
!
interface Ethernet 8
 poe detection-type two-point-dot3af
 poe priority medium
 poe power-threshold power-up-based
sonic#
```

## PNAC
## Dot1X and MAB
### Dot1X config commands

### vsa-vlan
Config vlan description with vlan Id.

**syntax**: `dot1x radius vsa-vlan <vlan_description> <vlan_id>`

**Command mode** : CONFIG

**Click command** : 
```
root@sonic:~# config dot1x radius vsa-vlan add Quality_Team 100
root@sonic:~# config dot1x radius vsa-vlan del Quality_Team
```

**Usage**       : Use `no dot1x radius vsa-vlan <vlan_description>` to remove the vlan description.

**Supported Releases** :  2.0 or later

**Example**
```
sonic(config)# dot1x radius vsa-vlan Quality_Team 100
sonic(config)# no dot1x radius vsa-vlan Quality_Team 100
sonic#
```

### radius server
Used to Configure radius server.

**Note** : 
1. Primay radius server can be deleted only when there is no Dot1X/MAB session enabled.
2. Secondary radius server can be deleted regardless of Dot1X/MAB session. but warning message will be displayed to confirm the operation.
3. VRF is the optional parameter, Incase associating either mgmt or data vrf to the radius server, It should be pre-configured. Otherwise the config would be failed.

**syntax**: `dot1x radius server {Primary|Secondary} <ipaddress> <port> <secret_key> [Vrf<name>|mgmt] [encrypted]`

**Command mode** : CONFIG

**Click command** : 
```
root@sonic:~# config dot1x radius server add 10.208.10.110 1011 YourPaSsWoRd
root@sonic:~# config dot1x radius server del
```
**Usage**       : Use `no dot1x radius server <primary/secondary>` to remove the Radius server.

**Supported Releases** :  2.0 or later

**Example**
```
The following formats are appropriate for configuring a radius server and can also be used for a secondary server:
sonic(config)# dot1x radius server primary 192.168.10.111 1010 YourPaSsWoRd
sonic(config)# dot1x radius server primary 192.168.10.111 1010 YourPaSsWoRd encrypted
sonic(config)# dot1x radius server primary 192.168.10.111 1010 YourPaSsWoRd Vrf-name1
sonic(config)# dot1x radius server primary 192.168.10.111 1010 YourPaSsWoRd mgmt
sonic(config)# dot1x radius server primary 192.168.10.111 1010 YourPaSsWoRd Vrf-name1 encrypted
sonic(config)# dot1x radius server secondary 192.168.10.112 1011 Password@123

sonic(config)# no dot1x radius server primary
%Error: Disable all Dot1X session before deleting primary radius server.
sonic(config)# no dot1x radius server primary
sonic(config)# no dot1x radius server secondary
This will affect the existing PNAC client(s), continue? [y/N]: y
sonic(config)#
```
### Dot1X Interface level config commands
**Note** : 
1. Primary radius server must be configured before enabling Dot1X/MAB session.
2. Dot1X/MAB can be enabled only on Ethernet interface.
3. Dot1X/MAB can't be a destination port for Switch Port Analyzer (SPAN) ie, Mirroring destination port.
4. Dot1X/MAB can't be enabled on router interface.
5. Dot1X/MAB can't be enabled on sticky MAC enabled interface.
6. Dot1X and MAB can be enabled on same interface.
7. Once the Dot1X/MAB is enabled, it can't be re-configure the other parameters until disable them. backoff-timer is exceptional from this.

### dot1x enable
Used to enable Dot1X in an interface.

**syntax**: `dot1x enable`

**Command mode** : Physical interface

**Click command** : 
```
root@sonic:~# config dot1x enable Ethernet4
root@sonic:~# config dot1x disable Ethernet4
```

**Usage**       : Use `no dot1x enable` to disable the Dot1X session.

**Supported Releases** :  2.0 or later

**Example**
```
sonic(conf-if-Ethernet4)# dot1x enable
sonic(conf-if-Ethernet4)# no dot1x enable
```

### auth mode configureation
Used to configure the authentication mode.

**syntax**: `dot1x auth-mode <single-host/multi-host>`

**Command mode** : Physical interface

**Click command** : `root@sonic:~# config dot1x auth-mode <single-host/multi-host> Ethernet4`

**Usage**       : Use `no dot1x auth-mode` to set the default value of multi-host.

**Supported Releases** :  2.0 or later

**Example**
```
sonic(conf-if-Ethernet4)# dot1x auth-mode single-host
sonic(conf-if-Ethernet4)# no dot1x auth-mode
```

### maximim clients
Used to configure the maximum client.

**syntax**: `dot1x max-clients <maxlimit>`

**Command mode** : Physical interface

**Click command** : `root@sonic:~# config dot1x max-clients Ethernet4 12`

**Usage**       : Use `no dot1x max-clients` to set the default value of 16.

**Supported Releases** :  2.0 or later

**Example**
```
sonic(conf-if-Ethernet4)# dot1x max-clients 12
sonic(conf-if-Ethernet4)# no dot1x max-clients
```

### re-auth time
Used to configure the re authentication timer info.

**syntax**: `dot1x reauth-timer <period>`

**Command mode** : Physical interface

**Click command** : `root@sonic:~# config dot1x reauth-timer Ethernet4 5000`

**Usage**       : Use `no dot1x reauth-timer` to set the default value of 3600.

**Supported Releases** :  2.0 or later

**Example**
```
sonic(conf-if-Ethernet4)# dot1x reauth-timer 5000
sonic(conf-if-Ethernet4)# no dot1x reauth-timer
```

### mab enable
Used to enable the MAB session in an interface.

**syntax**:  `dot1x mab enable`

**Command mode** : Physical interface

**Click command** : 
```
root@sonic:~# config dot1x mab enable Ethernet4
root@sonic:~# config dot1x mab disable Ethernet4
```

**Usage**       : Use `no dot1x mab enable` to disable the MAB session in an interface.

**Supported Releases** :  2.0 or later

**Example**
```
sonic(conf-if-Ethernet4)# dot1x mab enable
sonic(conf-if-Ethernet4)# no dot1x mab enable
```

### mab backoff timer
Used to configure the backoff timer.

**syntax**:  `dot1x mab backoff-timer <period>`

**Command mode** : Physical interface

**Click command** : `root@sonic:~# config dot1x mab backoff-timer Ethernet4 50`

**Usage**       : Use `no dot1x mab backoff-timer` to set the default value of 60.

**Supported Releases** :  2.0 or later

**Example**
```
sonic(conf-if-Ethernet4)# dot1x mab backoff-timer 50
sonic(conf-if-Ethernet4)# no dot1x mab backoff-timer
```

### Dot1X show commands
### Show radius server

**syntax**:  `show dot1x radius server`

**Command mode** : EXEC

**Click command** : `root@sonic:~# show dot1x radius server`

**Usage**       : Display the Radius server information.

**Supported Releases** :  2.0 or later

**Example**
```
sonic# show dot1x radius server
-----------------------------------------------------
RADIUS ROLE          RADIUS IP       RADIUS PORT
-----------------------------------------------------
Primary              192.168.1.123   1011
Secondary            192.168.1.124   1012
sonic#
```

### Show vsa-vlan
**syntax**:  `show dot1x radius vsa-vlan {<vsa-name>}`

**Command mode** : EXEC

**Click command** : `root@sonic:~# show dot1x radius vsa-vlan {<vsa-name>}`

**Usage**       : Display the Radius vsa vlan information.

**Supported Releases** :  2.0 or later

**Example**
```
sonic# show dot1x radius vsa-vlan
-------------------------------------------------------
VLAN Description                         VLAN ID
-------------------------------------------------------
Dev_Team                                 500
Quality_Team                             100
Security_Team                            200
sonic#
```

### Active clients
**syntax**:  `show dot1x clients active {<interface-name>}`

**Command mode** : EXEC

**Click command** : `root@sonic:~# show dot1x clients active {<interface-name>}`

**Usage**       : Display the active clients information.

**Supported Releases** :  2.0 or later

**Example**
```
sonic# show dot1x clients active
------------------------------------------------------------------------------------------------------------------
PORT            MAC                  VLAN ID   TYPE       STATE                            TIMESTAMP
------------------------------------------------------------------------------------------------------------------
Ethernet44      00:00:00:11:33:01    1001      MAB        AUTH-ACCEPTED                    02-04-2024 03:40:28
sonic#
```

### Auth failures
**syntax**:  `show dot1x clients auth-failures {<interface-name>}`

**Command mode** : EXEC

**Click command** : `root@sonic:~# show dot1x clients auth-failures {<interface-name>}`

**Usage**       : Display the client's authentication failures information.

**Supported Releases** :  2.0 or later

**Example**
```
sonic# show dot1x clients auth-failures
------------------------------------------------------------------------------------------------------------------
PORT            MAC                  VLAN ID      STATE                                  TIMESTAMP
------------------------------------------------------------------------------------------------------------------
Ethernet40      34:73:5a:f8:a7:3b    1001         DOT1X-AUTH-FAIL-Radius-Timeout         15-03-2024 10:55:57
Ethernet40      34:73:5a:f8:a7:3b    1001         DOT1X-AUTH-FAIL-Radius-Timeout         15-03-2024 11:01:08
sonic#
```

### Dot1X port info
**syntax**:  `show dot1x port {<interface-name>}`

**Command mode** : EXEC

**Click command** : `root@sonic:~# show dot1x port {<interface-name>}`

**Usage**       : Display the port level Dot1X and MAB configurations.

**Supported Releases** :  2.0 or later

**Example**
```
sonic# show dot1x port
------------------------------------------------------------------------------------------------------------------------------------------
Clients         Dot1x Status      Auth-Mode       Reauthentication Timer(sec)    MAB Status      MAB Backoff Timer(sec)     Max Clients
------------------------------------------------------------------------------------------------------------------------------------------
Ethernet4       Enabled           single-host     5000                           Disabled        50                         10
Ethernet20      Disabled          single-host     6000                           Enabled         60                         6
Ethernet50      Disabled          multi-host      3600                           Disabled        50                         16
sonic#
```

### Dot1X running configurations
**syntax**:  `show running-config dot1x`

**Command mode** : EXEC

**Click command** : None

**Usage**       : Display the running configuration of Dot1X and MAB.

**Supported Releases** :  2.0 or later

**Example**
```
sonic# show running-config dot1x
!
!
dot1x radius vsa-vlan Dev_Team 500
dot1x radius vsa-vlan Quality_Team 100
dot1x radius vsa-vlan Security_Team 200
!
dot1x radius server primary 192.168.1.123 1011 U2FsdGVkX18O3JiO4f5xeEGtA48L9EmHD/65DBHWixg= encrypted
dot1x radius server secondary 192.168.1.124 1012 U2FsdGVkX19HMDIjzZ8LBwdm8XNhCQlnbt85gfPfnjU= encrypted
!
interface Ethernet 4
 dot1x reauth-timer 5000
 dot1x auth-mode single-host
 dot1x max-clients 10
 dot1x mab backoff-timer 50
 dot1x enable
!
interface Ethernet 20
 dot1x reauth-timer 6000
 dot1x auth-mode single-host
 dot1x max-clients 6
 dot1x mab enable
sonic#

```

## Edge security
### Edge security config commands
**Note** : 
1. Edge security can be enabled only on Ethernet interface.
2. Edge security can't be configured on router interface.
3. Edge security cannot be a destination port for Switch Port Analyzer (SPAN) ie Mirroring destination port.
4. Edge security cannot be enabled on Dot1X or MAB enabled port.
5. Edge-security can be enabled only on access port.
6. Edge security enabled port cannot be unconfigured from vlan.
7. Not allowed to enable Edge security on static MAC configured interface.
8. Once Edge-security id enabled, subsequent parameter changes are not allowed.
9. Not allowed to disable the edge security if the interface has any sticky MAC configuration.

### Edge security enable

**syntax**:  `edge-security enable`

**Command mode** : Physical interface

**Click command** : 
```
root@sonic:~# config edge-security enable Ethernet12
root@sonic:~# config edge-security disable Ethernet12
```

**Usage**       : Use `no edge-security enable` to disable the Edge security.

**Supported Releases** :  2.0 or later

**Example**
```
sonic(conf-if-Ethernet12)# edge-security enable
sonic(conf-if-Ethernet12)# no edge-security enable
```

### Sticky MAC configuration
**Note** :
1. Edge security must be enabled before configuring sticky MAC.
2. Opeartion not allowed if the given MAC is already configured in another interface.

**syntax**:  `edge-security sticky-mac [nn:nn:nn:nn:nn:nn|nn-nn-nn-nn-nn-nn|nnnn.nnnn.nnnn]`

**Command mode** : Physical interface

**Click command** : 
```
root@sonic:~# config edge-security enable Ethernet12
root@sonic:~# config edge-security disable Ethernet12
```

**Usage**       : Use `no edge-security sticky-mac [nn:nn:nn:nn:nn:nn|nn-nn-nn-nn-nn-nn|nnnn.nnnn.nnnn]` to remove the sticky MAC.

**Supported Releases** :  2.0 or later

**Example**
```
sonic(conf-if-Ethernet12)# edge-security sticky-mac 00:B0:D0:63:C2:26
sonic(conf-if-Ethernet12)# no edge-security sticky-mac 00:B0:D0:63:C2:26
```

### Set dynamic learn max count

**syntax**:  `edge-security dynamic-learn-max <max-count>`

**Command mode** : Physical interface

**Click command** : `root@sonic:~# config edge-security dynamic-learn-max Ethernet12 13`

**Usage**       : Use `no edge-security dynamic-learn-max` to set the default value of 0.

**Supported Releases** :  2.0 or later

**Example**
```
sonic(conf-if-Ethernet12)# edge-security dynamic-learn-max 13
sonic(conf-if-Ethernet12)# no edge-security dynamic-learn-max
```

### violation action

**syntax**:  `edge-security violation-action [restrict|shutdown]`

**Command mode** : Physical interface

**Click command** : `root@sonic:~# config edge-security violation-action [restrict|shutdown]`

**Usage**       : Use `no edge-security violation-action` to set the default value of restrict.

**Supported Releases** :  2.0 or later

**Example**
```
sonic(conf-if-Ethernet12)# edge-security violation-action shutdown
sonic(conf-if-Ethernet12)# no edge-security violation-action
```

## Edge security clear commands

### Clear secure-sticky | secure-dynamic
**syntax**:  `clear edge-security [secure-sticky|secure-dynamic] [<interface-name>]`

**Command mode** : EXEC

**Click command** : None

**Usage**       : Used to clear the secure-sticky and secure-dynamic MACs.

**Supported Releases** :  2.0 or later

**Example**
```
sonic# clear edge-security secure-sticky Ethernet 12
```

### Clear violation
**syntax**:  `clear edge-security violation [<interface-name>]`

**Command mode** : EXEC

**Click command** : None

**Usage**       : Used to clear the Edge security violation.

**Supported Releases** :  2.0 or later

**Example**
```
sonic# clear edge-security violation Ethernet 12
```

## Edge security show commands
### show Edge security MAC
**syntax**:  `show edge-security mac {<interface-name>}`

**Command mode** : EXEC

**Click command** : `show edge-security mac {<interface-name>}`

**Usage**       : Display the Edge security MAC information.

**Supported Releases** :  2.0 or later

**Example**
```
sonic# show edge-security mac
-------------------------------------------------------------------------------------------------------------------------
PORT            MAC                  VLAN ID      Type               Violation Action               TIMESTAMP
-------------------------------------------------------------------------------------------------------------------------
Ethernet40      34:73:5a:f8:a7:3b    1001         STICKY-CONFIGURED  None                           05-04-2024 07:02:11
Ethernet44      00:00:00:11:33:01    1001         LEARNT-DYNAMIC     None                           05-04-2024 07:02:47
```

### show Edge security port
**syntax**:  `show edge-security port {<interface-name>}`

**Command mode** : EXEC

**Click command** : `show edge-security config {<interface-name>}`

**Usage**       : Display the Edge security port information.

**Supported Releases** :  2.0 or later

**Example**
```
sonic# show edge-security port
--------------------------------------------------------------------------------
Port          Edge-security Status   Max Dynamic-learn-macs   Violation Action
--------------------------------------------------------------------------------
Ethernet4     Disabled               0                        restrict
Ethernet12    Enabled                13                       shutdown
Ethernet20    Disabled               0                        restrict
Ethernet50    Disabled               0                        restrict
sonic#
```


### show running-config edge security
**syntax**:  `show running-config edge-security`

**Command mode** : EXEC

**Click command** : None

**Usage**       : Display the running-configurations of Edge security.

**Supported Releases** :  2.0 or later

**Example**
```
sonic# show running-config edge-security
!
interface Ethernet 4
!
interface Ethernet 12
 edge-security dynamic-learn-max 13
 edge-security violation-action shutdown
 edge-security enable
 edge-security sticky-mac 00:b0:d0:63:c2:26
!
interface Ethernet 20
sonic#
```

## Crypto PKI
### show ssh host-key
show ssh host keys 

**Syntax**: `show ssh host-key [dsa | rsa | ecdsa | ed25519]`

**Command mode**: EXEC

**Usage**       : Use `show ssh host-key` to list the supported host keys on the device.

**Supported Releases** :  2.0.0 or later

**Click command**: None

**Example**:
```

Celestica-DS1000# show ssh host-key
-----------------------------------------------------------------------------
SSH HOST KEY DSA
-----------------------------------------------------------------------------
Type          : dsa
Bits          : 1024
Fingerprint   : SHA256:TysiqkHAA5+QPO3SRf86yBH/dftHa3N8ZKUB29fXQ6g

Public Key:
ssh-dss AAAAB3NzaC1kc3MAAACBAOUe7kIyy8YGWN1IW58ovjPPjBAxjxlbWhdqNoYVd1JSiBcJC/P2ecrunTCvFt9+NJXqoFsCaOVdkbdpCFCC8GdhoXpyGmkTxY6fIF17LkDhOgc/yNcmbRiek0QKOkcPw4uwvlph97thbc8tCl2TicLqm4VU5EV4hFJqvbV5dqW9AAAAFQC861HOxL1m/SvtdNO5XAtwwGUY8wAAAIAgWvPdo+aNvqgQp+arX+YwfR3TEzQBVjRt5mYMr3c06GN5YwJzG+W7PLj2e82cXl6mNeX4i+T2lzc9qAiXDlBP8E789y+rs9H7ByTuH+eY1W/1zYC2eKOZO0eh4epdOzthVo8RSBLexVXzMl83+JINONVhE3CWq/3oczqFqyRvKwAAAIAzqjB1CUt3Ql+XkJCtu81Ivc171xXW1vhWEG3nW2DisTqYrN8vVeOrPlTDvwqVI7m1DsNsPBAjwiZ3c95+RDHfTu0WgxzVYYqOReUfwjKr3rD39oEozDJaJSw28eeBAFcXdYGCdkzQiKBUAbTbsv5S5GENYtAQFggfmm0TXyP6mQ== root@Celestica-DS1000

-----------------------------------------------------------------------------
SSH HOST KEY RSA
-----------------------------------------------------------------------------
Type          : rsa
Bits          : 3072
Fingerprint   : SHA256:4DaEFQV534EHzYBjX3OClgvAXCnEgvyrJIQ0xVTDHpI

Public Key:
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQCjdp2+Y3Jsu7bn+rzRMEXmMaT3e8ACJ/rk7bMUg1yvemrZ5EqZAxXV+/RQrrke0Ykwf9v7XtTt/QF3usKHD+GlNCSJc+cQfWEp3z5yrYR2oUJCFLtPDjQWvFYDwNAVkPLTXQMzj7c8FNczsDhY2u5jMeICbvRknibvbnVxKsdMxK3jFDUGKvqsGVCVbwe1HDpG9OtnklgDOmxzF8Sek7v1a+lA+U3CtNRn4CTLUx3avHkZ1kmPzCNfIXiLv04rTVkQVpCUynsYgWGEfwdSfI/xCaFewRkypbZIEx8Ljvl+5TVUX+Zk7xLRVqUSeNzJnMPO64v/KD+S+VhwFtwLhREDP9tn9dYaUlzu52QJB7lTpvK9W+rp/I1zMAoRb9+/OKWus5qSJ5mjDnapVaIdIXwa9jipBFPCjVyqQNdQWOjb6tONZhv+Of/m4IhC2jQBdPl+eAQHUdyXQjnj10f+w/Q5CIgst50XuNVgWgcwbg4+r4U4NQxun9UQPUu/n1EzAiU= root@Celestica-DS1000

Celestica-DS1000#
```

### ssh generate host-key
Generate ssh host key

**Syntax**: `ssh generate host-key <dsa | rsa <2048|3072|4096> | ecdsa <256|384|521> | ed25519>`

**Command mode**: EXEC

**Usage**       : Use `ssh generate host-key` to generate a host key for the device.

**Supported Releases** :  2.0.0 or later

**Click command**: None

**Example**:
```
Celestica-DS1000# ssh generate host-key ecdsa 384
Celestica-DS1000# ssh generate host-key rsa 2048
Celestica-DS1000# ssh generate host-key dsas
```
## STP
### STP config commands

### ageing time
Used to configure STP ageing time.

**syntax**: `stp ageing-time <ageing-time value>`

**Command mode** : CONFIG

**Click command** : `config stp ageing-time <value>`

**Usage**       : Use `no stp ageing-time` to set the default value of 300.

**Supported Releases** :  2.0 or later

**Example**
```
Celestica-DS1000(config)# stp ageing-time 300
Celestica-DS1000(config)# no stp ageing-time
```

### fwd delay
Used to configure STP forward delay.

**syntax**: `stp fwd-delay <delay-value>`

**Command mode** : CONFIG

**Click command** : `config stp fwd-delay <value>`

**Usage**       : Use `no stp fwd-delay` to set the default value of 15.

**Supported Releases** :  2.0 or later

**Example**
```
Celestica-DS1000(config)# stp fwd-delay 10
Celestica-DS1000(config)# no stp fwd-delay 
```
### hello time
### max age
Used to configure hello time stp global configuration.

**syntax**: `stp hello-time <hello-time value>`

**Command mode** : CONFIG

**Click command** : `config stp hello-time 8`

**Usage**       : Use `no stp hello-time` to set the default value of 2.

**Supported Releases** :  2.0 or later

**Example**
```
Celestica-DS1000(config)# stp hello-time 8
Celestica-DS1000(config)# no stp hello-time
```

### max hops
Used to configure the max hops of stp.

**syntax**: `stp max-hops 10`

**Command mode** : CONFIG

**Click command** : `config stp max-hops 10`

**Usage**       : Use `no stp max-hops` to set the default value of 20.

**Supported Releases** :  2.0 or later

**Example**
```
Celestica-DS1000(config)# stp max-hops 20
Celestica-DS1000(config)# no stp max-hops
```

### priority
Used to configure the priority of stp.

**syntax**: `stp priority <priority-value>`

**Command mode** : CONFIG

**Click command** : `config stp priority <priority>`

**Usage**       : Use `no stp priority` to set the default value of 8.

**Supported Releases** :  2.0 or later

**Example**
```
Celestica-DS1000(config)# stp priority 10
Celestica-DS1000(config)# no stp priority 
```

### protocol
Used to enable rstp global configuration on the device.

**syntax**: `stp protocol rstp`

**Command mode** : CONFIG

**Click command** : `config stp protocol rstp`

**Usage**       : Use `no stp protocol` to disable the STP on global level.

**Supported Releases** :  2.0 or later

**Example**
```
Celestica-DS1000(config)# stp protocol rstp
Celestica-DS1000(config)# no stp protocol
```
### STP Interface config commands 
### stp enable
Used to enable STP in an interface.

**syntax**: `stp enable`

**Command mode** : Physical interface

**Click command** : `config stp port <enable|disable> <port>`

**Usage**       : Use `no stp enable` to disable the STP on interface.

**Supported Releases** :  2.0 or later

**Example**
```
sonic(conf-if-Ethernet4)# stp enable
sonic(conf-if-Ethernet4)# no stp enable
```

### admin edge
Used to configure the authentication mode.

**syntax**: `stp admin-edge <enable|disable>`

**Command mode** : Physical interface

**Click command** : `config stp port admin-edge <enable|disable> <port>`

**Usage**       : Use `no stp admin-edge` to disable the admin edge on the STP enabled port.

**Supported Releases** :  2.0 or later

**Example**
```
Celestica-DS1000(conf-if-Ethernet10)# stp admin-edge enable
Celestica-DS1000(conf-if-Ethernet10)# no stp admin-edge
```

### cost
Used to STP bridge cost in the STP enabled interface.

**syntax**: `stp cost <cost-value>`

**Command mode** : Physical interface

**Click command** : `config stp port cost <port> <cost>`

**Usage**       : Use `no stp cost` to set the default value of 0.

**Supported Releases** :  2.0 or later

**Example**
```
Celestica-DS1000(conf-if-Ethernet10)# stp cost 10
sonic(conf-if-Ethernet4)# no stp cost
```

### bpdu guard
Used to enable the bpdu guard on the STP enabled interfaces.

**syntax**: `stp bpdu-guard <enable|disable>`

**Command mode** : Physical interface

**Click command** : `config stp port bpdu-guard <enable|disable> <port>`

**Usage**       : Use `no stp bpdu-guard` to disable the bpdu guard on the interface.

**Supported Releases** :  2.0 or later

**Example**
```
Celestica-DS1000(conf-if-Ethernet10)# stp bpdu-guard enable
Celestica-DS1000(conf-if-Ethernet10)# no stp bpdu-guard

```

### network state
Used to enable the STP network state on the interface.

**syntax**:  `stp network-state enable`

**Command mode** : Physical interface

**Click command** : `config stp port network-state <enable|disable> <port>`

**Usage**       : Use `no stp netword-state` to disable the STP network-state on the interface.

**Supported Releases** :  2.0 or later

**Example**
```
Celestica-DS1000(conf-if-Ethernet10)# stp network-state enable
Celestica-DS1000(conf-if-Ethernet10)# no stp network-state
```

### p2p
Used to configure the p2p in a STP enabled interface.

**syntax**:  `stp p2p <enable | auto>`

**Command mode** : Physical interface

**Click command** : `config stp port p2p <enable|auto|disable> <port>`

**Usage**       : Use `no stp p2p` to disable the p2p on the interface.

**Supported Releases** :  2.0 or later

**Example**
```
Celestica-DS1000(conf-if-Ethernet10)# stp p2p auto
Celestica-DS1000(conf-if-Ethernet10)# no stp p2p
```


### STP show commands
### show stp port
**syntax**:  `show stp port <Ethernet <id>| PortChannel <id>`

**Command mode** : EXEC

**Click command** : `show stp port <port-name>`

**Usage**       : Display the interface level status of STP enabled port. 

**Supported Releases** :  2.0 or later

**Example**
```
Celestica-DS1000# show stp port Ethernet 10
                      Stp Port Status
------------------------------------------------------------
Name                        : Ethernet10
Ba Inconsistent             : no
Num RX BPDU Filtered        : 0
Num RX TCN                  : 0
Num TX BPDU                 : 0
Num Transition BLK          : 1
Rcvd BPDU                   : no
Rcvd RSTP                   : no
Rcvd TC Ack                 : no
Rcvd TCN                    : no
Send RSTP                   : yes
Admin External Cost         : 0
Admin Internal Cost         : 0
Admin Point-to-Point        : auto
Auto Edge Port              : yes
Admin Edge Port             : no
BPDU Filter Port            : no
BPDU Guard Error            : no
BPDU Guard Port             : no
Designated Bridge           : 8.000.34:AD:61:F1:B5:D6
Designated Port             : 0.000
Designated Root             : 8.000.34:AD:61:F1:B5:D6
Disputed                    : no
Dsgn External Cost          : 0
Dsgn Internal Cost          : 0
Dsgn Regional Root          : 8.000.34:AD:61:F1:B5:D6
Enabled                     : no
External Port Cost          : 200000000
Internal Port Cost          : 200000000
Network Port                : no
Oper Edge Port              : no
Point-to-Point              : no
Port Hello Time             : 2
Port ID                     : 8.001
Restricted TCN              : no
Restricted Role             : no
Role                        : Disabled
State                       : discarding
Topology Change Ack         : no
Celestica-DS1000#
```

### show stp state-log
**syntax**:  `show stp state-log`

**Command mode** : EXEC

**Click command** : `show stp state-log`

**Usage**       : Display the state log of STP enabled interfaces.

**Supported Releases** :  2.0 or later

**Example**
```
Celestica-DS1000# show stp state-log
-----------------------------------------------------------------------------------------------------------------------------------
INDEX           PORT            STATE_TRANSITION                              ADMIN STATE     TIMESTAMP
-----------------------------------------------------------------------------------------------------------------------------------
1               Ethernet10      BR_STATE_BLOCKING                             Disabled        12-08-2024 06:50:46
Celestica-DS1000# s
```

### show stp status
**syntax**:  `show stp status`

**Command mode** : EXEC

**Click command** : `show stp status`

**Usage**       : Display the current global status of of STP feature.

**Supported Releases** :  2.0 or later

**Example**
```
Celestica-DS1000# show stp status
                      Stp Status
------------------------------------------------------------
Ageing Time                : 300
Bridge Forward Delay       : 15
Bridge Id                  : 8.000.34:AD:61:F1:B5:D6
Bridge Max Age             : 20
Designated Root            : 8.000.34:AD:61:F1:B5:D6
Enabled                    : yes
Force Protocol Version     : rstp
Hello Time                 : 2
Internal Path Cost         : 0
Last Topology Change Port  : None
Max Age                    : 20
Max Hops                   : 20
Path Cost                  : 0
Regional Root              : 8.000.34:AD:61:F1:B5:D6
Root Port                  : none
Time since topology change : 6
Topology change            : no
Topology change count      : 0
Topology change port       : None
TX Hold Count              : 6

```

## CLI translate
### CLI translate config commands

### CLI translate enable
**syntax**:  `cli translate enable`

**Command mode** : EXEC

**Click command** : None

**Usage**       : Translate CLI commands to REST/GNMI requests. Use `no cli translate enable` command to disable the CLI translation.

**Supported Releases** :  4.0 or later

**Example**
```
Show command output:
---------------------
Celestica-DS1000# show vlan
Flags:  d - Dynamic config done by system
        c - User configuration
------------------------------------------------------------
Name       Id         Members              Mode
------------------------------------------------------------
Vlan100    100        Ethernet4 (c)        untagged
------------------------------------------------------------
Celestica-DS1000# cli translate enable
Celestica-DS1000(TRANSLATE-MODE)# show vlan
RESTCONF request:
------------------
curl -i -k -H "accept: application/yang-data+json" -u $USER_NAME:$PASSWORD -X GET https://$DEVICE_IP/restconf/data/openconfig-interfaces:interfaces/openconfig-if-cls-ext:vlans/vlan

gNMI request:
--------------
operation : GET
xpath     : /openconfig-interfaces:interfaces/openconfig-if-cls-ext:vlans/vlan/

Celestica-DS1000(TRANSLATE-MODE)#

Config command output:
-----------------------
Celestica-DS1000(TRANSLATE-MODE)#
Celestica-DS1000(TRANSLATE-MODE)# configure terminal
Celestica-DS1000(TRANSLATE-MODE)(config)# interface Vlan 200
RESTCONF request:
------------------
curl -i -k -H "accept: application/yang-data+json" -H "Content-Type: application/yang-data+json" -u $USER_NAME:$PASSWORD -d "{\"openconfig-interfaces:interfaces\": {\"interface\": [{\"name\": \"Vlan200\", \"config\": {\"name\": \"Vlan200\"}}]}}" -X PATCH https://$DEVICE_IP/restconf/data/openconfig-interfaces:interfaces

gNMI request:
--------------
operation : UPDATE
xpath     : /openconfig-interfaces:interfaces/
body      : {\"openconfig-interfaces:interfaces\": {\"interface\": [{\"name\": \"Vlan200\", \"config\": {\"name\": \"Vlan200\"}}]}}

Celestica-DS1000(TRANSLATE-MODE)(conf-if-Vlan200)#
Celestica-DS1000(TRANSLATE-MODE)(conf-if-Vlan200)# exit
Celestica-DS1000(TRANSLATE-MODE)(config)# exit
Celestica-DS1000(TRANSLATE-MODE)# no cli translate enable
Celestica-DS1000#
```
### UDF hash support and enhancements

#### ip switch-hash ecmp ipv4 
Configure ECMP hash field selection for IPv4 packets

**Syntax** : `ip switch-hash ecmp ipv4`
```
  dst-ipv4        Select IPv4 destination address
  ip-protocol     Select IP protocol
  l4-dst-port     Select L4 destination port
  l4-src-port     Select L4 source port
  src-ipv4        Select IPv4 source address
  symmetric-hash  Enable Symmetric hashing

```
**Parameters**  :
- `dst-ipv4` - Destination IPv4 field is selected for IPv4 hashing
- `src-ipv4` - Source IPv4 field is selected for IPv4 hashing
- `ip-protocol` - IP protocol field is selected for IPv4 hashing
- `l4-dst-port` - L4 destination port field is selected for IPv4 hashing
- `l4-src-port` - L4 source port field is selected for IPv4 hashing
- `symmetric-hash` - Symmetric hashing is enabled for IPv4 ECMP

**Command mode** : CONFIG

**Usage**       : Use `no ip switch-hash ecmp ipv4 dst-ipv4 / src-ipv4 / ip-protocol / l4-src-port / l4-dst-port / symmetric-hash` to reset to default value.

**Supported Releases** :  3.0.0 or later

**Click command** : 'config switch-hash global ecmp-hash-ipv4 --dstipv4 --srcipv4 --ip-protocol --l4-src-port --l4-dst-port --symmetric-hash'

**Example**
```
sonic(config)# ip switch-hash ecmp ipv4 dst-ipv4
sonic(config)# no ip switch-hash ecmp ipv4 dst-ipv4
sonic(config)# ip switch-hash ecmp ipv4 src-ipv4
sonic(config)# no ip switch-hash ecmp ipv4 src-ipv4
```
#### ip switch-hash ecmp ipv6 
ECMP hash field selection for IPv6 packets
**Syntax** : `ip switch-hash ecmp ipv6`
```
  dst-ipv6     Select IPv6 destination address
  l4-dst-port  Select L4 destination port
  l4-src-port  Select L4 source port
  next-header  Select IPv6 next header
  src-ipv6     Select IPv6 source address
  symmetric-hash  Enable Symmetric hashing
```
**Parameters**  :
- `dst-ipv6` - Destination IPv6 field is selected for IPv6 hashing
- `src-ipv6` - Source IPv6 field is selected for IPv6 hashing
- `next-header` - Next Header field is selected for IPv6 hashing
- `l4-dst-port` - L4 destination port field is selected for IPv6 hashing
- `l4-src-port` - L4 source port field is selected for IPv6 hashing
- `symmetric-hash` - Symmetric hashing is enabled for IPv6 ECMP

**Command mode** : CONFIG

**Usage**       : Use `no ip switch-hash ecmp ipv6 dst-ipv6 / src-ipv6 / next-header / l4-src-port / l4-dst-port / symmetric-hash` to reset to default value.

**Supported Releases** :  3.0.0 or later

**Click command** : 'config switch-hash global ecmp-hash-ipv6 --dstipv6 --srcipv6 --next-header --l4-src-port --l4-dst-port --symmetric-hash'

**Example**
```
sonic(config)# ip switch-hash ecmp ipv6 dst-ipv6
sonic(config)# no ip switch-hash ecmp ipv6 dst-ipv6
sonic(config)# ip switch-hash ecmp ipv6 src-ipv6
sonic(config)# no ip switch-hash ecmp ipv6 src-ipv6
```

#### ip switch-hash ecmp src-port
Source port/in port selected as ECMP hash field for IPv4 and IPv6 packets

**Syntax** : `ip switch-hash ecmp src-port`

**Parameters**  : `none`

**Command mode** : CONFIG

**Usage**       : Use `no ip switch hash ecmp src-port` to reset to default value.

**Supported Releases** :  3.0.0 or later

**Click command** : 'config switch-hash global ecmp-hash-ipv4 --in-port'

**Example**
```
sonic(config)# ip switch hash ecmp src-port
sonic(config)# no ip switch hash ecmp src-port
```

#### ip switch-hash ecmp algorithm
configure hash algorithm for ECMP

**Syntax** : `ip switch-hash ecmp algorithm <algorithm-value>`

**Parameters**  :
 - `algorithm-value` - CRC/XOR/CRC_32LO/CRC_32HI/CRC_CCITT/CRC_XOR default: CRC_32HI

**Command mode** : CONFIG

**Usage**       : Use `no ip switch-hash ecmp algorithm` to reset to default value.

**Supported Releases** :  3.0.0 or later

**Click command** : 'config switch-hash global ecmp-hash-algorithm'

**Example**
```
sonic(config)# ip switch-hash ecmp algorithm CRC
sonic(config)# no ip switch-hash ecmp algorithm
sonic(config)#
```

#### ip switch-hash ecmp hash-seed
configure seed value to be used for ECMP hashing

**Syntax** : `ip switch-hash ecmp hash-seed <seed-value>`

**Parameters**  :
 - `seed-value` - <1..16777215>  Configure hash seed value. default: random value

**Command mode** : CONFIG

**Usage**       : Use `no ip switch-hash ecmp hash-seed` to reset to default value.

**Supported Releases** :  3.0.0 or later

**Click command** : 'config switch-hash global ecmp-hash-seed <seed value>'

**Example**
```
sonic(config)# ip switch-hash ecmp hash-seed 1000
sonic(config)# no ip switch-hash ecmp hash-seed
sonic(config)#

```
#### ip switch-hash ecmp hash-offset
configure hash offset value to be configured for ECMP hashing.

**Syntax** : `ip switch-hash ecmp hash-offset offset <offset-value>`

**Parameters**  :
 - `offset-value` - range 0-15

**Command mode** : CONFIG

**Usage**       : Use `no ip switch-hash ecmp hash-offset` to reset to default value.

**Supported Releases** :  3.0.0 or later

**Click command** : 'config switch-hash global –-hash_offset <0-15> '

**Example**
```
sonic(config)# ip switch-hash ecmp hash-offset offset 5
sonic(config)#

```
#### ip switch-hash ecmp dst-queue-pair
configure destination queue pair field based hashing for infiniband packets encapsulated in ROCEv2 protocol.

**Syntax** : `ip switch-hash ecmp dst-queue-pair`

**Parameters**  : `none`

**Command mode** : CONFIG

**Usage**       : Use `no ip switch-hash ecmp dst-queue-pair` to reset to default value.

**Supported Releases** :  3.0.0 or later

**Click command** : 'config switch-hash global ecmp-dst-queue-pair true/false'

**Example**
```
sonic(config)# ip switch-hash ecmp dst-queue-pair
sonic(config)# no ip switch-hash ecmp dst-queue-pair
sonic(config)#
```

#### show ip switch-hash ecmp brief
Display attributes of ECMP based hashing attributes.

**Syntax**: `show ip switch-hash ecmp brief`

**Parameters**  : `none`

**Command mode** : Exec mode

**Usage**       : `show ip switch-hash ecmp brief`

**Click command** : `show switch-hash global`

**Example**
```
sonic# show ip switch-hash ecmp brief
-----------------------------------------------------------
Ecmp IPv4 hash fields     : DST_IP
Ecmp IPv6 hash fields     : DST_IP
Ecmp source port          : disabled
ECMP hash algorithm       : CRC
ECMP hash seed            : 10
Ecmp dst queue pair       : disabled
-----------------------------------------------------------
```
#### ip switch-hash lag ipv4
Configure LAG hash field selection for IPv4 packets (Only supported option is symmetric hashing)

**Syntax** : `ip switch-hash lag ipv4 symmetric-hash`

**Parameters**  :
- `symmetric-hash` - Symmetric hashing is enabled for IPv4 LAG

**Command mode** : CONFIG

**Usage**       : Use `no ip switch-hash lag ipv4 symmetric-hash` to reset to default value.

**Supported Releases** :  3.0.0 or later

**Example**
```
sonic(config)# ip switch-hash lag ipv4 symmetric-hash
sonic(config)# no ip switch-hash lag ipv4 symmetric-hash
```
#### ip switch-hash lag ipv6
Configure LAG hash field selection for IPv6 packets (Only supported option is symmetric hashing)

**Syntax** : `ip switch-hash lag ipv6 symmetric-hash`


**Parameters**  :
- `symmetric-hash` - Symmetric hashing is enabled for IPv6 LAG

**Command mode** : CONFIG

**Usage**       : Use `no ip switch-hash lag ipv6 symmetric-hash` to reset to default value.

**Supported Releases** :  3.0.0 or later

**Example**
```
sonic(config)# ip switch-hash lag ipv6 symmetric-hash
sonic(config)# no ip switch-hash lag ipv6 symmetric-hash
```

#### show ip switch-hash lag brief
Display attributes of LAG based hashing attributes.

**Syntax**: `show ip switch-hash lag brief`

**Parameters**  : `none`

**Command mode** : Exec mode

**Usage**       : `show ip switch-hash lag brief`

**Example**
```
show ip switch-hash lag brief
-----------------------------------------------------------
LAG IPv4 hash fields      : SYMMETRIC_HASH
LAG IPv6 hash fields      : SYMMETRIC_HASH
-----------------------------------------------------------
```
## MACsec
**Note** : The feature is supported on MACsec platforms only.

### MACsec Config Commands
#### MACsec profile 

Configures a MACsec profile

**Syntax** : 

`macsec profile  <profile-name> primary-cak <primary-cak-value> primary-ckn <primary-ckn-value> priority <priority-value> cipher-suite <cipher-suite-value> policy <policy-value> replay-protect <replay-protect-value> replay-window <replay-protect-window-value> rekey-period <rekey-period-value>`

**Parameters** :
- `profile-name` - Profile name for the MACsec profile. Valid string is acceptable
- `primary-ckn-value` - Primary Connectivity Association key Name (CKN) value. Accepts valid hex string
- `primary-cak-value` - Primary Connectivity Association Key for the MACsec profile. Accepts type7 encoded hex string value
- `priority-value` - Priority used for MACsec key server selection which ranges from 0 to 255 (default:255)
- `cipher-suite-value` - Cipher suite type used for MACsec profile; Acceptable values are GCM-AES-128,GCM-AES-256,GCM-AES-XPN-128,GCM-AES-XPN-256 (default:GCM-AES-128)
- `policy-value` - Policy of MACsec profile; Acceptable values are integrity_only,security (default:security)
- `replay-protect-value` - Denotes whether replay protect is enabled or not. Acceptable values are enable,disable (default:disable)
- `replay-window-value` - Replay protect window size which is valid only when replay protect is enabled. Accepts integer values.
- `rekey-period` - Rekey period for the MACsec profile. Accepts integer value (default: 0)

**Command mode** : CONFIG

**Usage**       : Use `no macsec profile <profile-name>` to remove the configured MACsec profile.

Sending Secure Channel Identifier(SCI) as part of MACsec tag header is not supported

**Supported Releases** :  4.0.0 or later

**Click commands** :
- config macsec profile add [OPTIONS] <profile_name>
- config macsec profile del [OPTIONS] <profile_name>

**Click command Example** : 
```
root@Celestica-ES1000-48C:~# config macsec profile add test --cipher_suite GCM-AES-XPN-256 --primary_cak "207b757a60617745504e5a20747a7c76725e524a450d0d01040a0c75297822227e07554155500e5d5157786d6c2a3d2031425a5e577e7e727f6b6c033124322627" --primary_ckn "6162636465666768696A6B6C6D6E6F707172737475767778797A303132333435"  --priority 1 --no_send_sci
```

**Example**
```
Celestica-ES1000-48C(config)# macsec profile test primary-cak 207b757a60617745504e5a20747a7c76725e524a450d0d01040a0c75297822227e07554155500e5d5157786d6c2a3d2031425a5e577e7e727f6b6c033124322627 primary-ckn 6162636465666768696A6B6C6D6E6F707172737475767778797A303132333435 priority 1 cipher-suite GCM-AES-XPN-256 rekey-period 5
Celestica-ES1000-48C(config)#
Celestica-ES1000-48C(config)# no macsec profile test
Celestica-ES1000-48C(config)#
```

### MACsec interface level config commands
#### macsec-profile
Attach macsec profile to an port.

**syntax**: `macsec-profile <profile-name>`

**Command mode** : Physical interface

**Click command** : 
```
root@Celestica-ES1000-48C:~# config macsec port add Ethernet30 test
root@Celestica-ES1000-48C:~# config macsec port del Ethernet30
root@Celestica-ES1000-48C:~#
```

**Usage**       : Use `no macsec-profile` to detach the MACsec profile from an interface.

**Supported Releases** :  4.0 or later

**Example**
```
Celestica-ES1000-48C(config)# interface Ethernet 40
Celestica-ES1000-48C(conf-if-Ethernet40)#
Celestica-ES1000-48C(conf-if-Ethernet40)# macsec-profile test
Celestica-ES1000-48C(conf-if-Ethernet40)# no macsec-profile
Celestica-ES1000-48C(conf-if-Ethernet40)#
```

### MACsec Clear commands
#### clear counters
Used to clear the MACsec counts.

**syntax**: `clear macsec counters`

**Command mode** : EXEC

**Click command** : 
```
root@Celestica-ES1000-48C:~# sonic-clear macsec
Clear MACsec counters
root@Celestica-ES1000-48C:~#
```

**Usage**       : Used to clear the port counters related to MACsec.

**Supported Releases** :  4.0 or later

**Example**
```
Celestica-ES1000-48C# clear macsec counters
Celestica-ES1000-48C#
```

### MACsec Show commands
#### show macsec profile
Display macsec profiles created in the device

**syntax**: `show macsec profiles`

**Command mode** : EXEC

**Click command** : `root@Celestica-ES1000-48C:~# show macsec`

**Usage**       : Used to display all the macsec profiles created so far in the device.

**Supported Releases** :  4.0 or later

**Example**
```
Celestica-ES1000-48C# show macsec profiles
MACsec profile : test
        ------------  ----------------------------------------------------------------
        cipher_suite          GCM-AES-XPN-256
        policy                security
        primary_ckn           6162636465666768696A6B6C6D6E6F707172737475767778797A303132333435
        priority              1
        send_sci              False
        ------------  ----------------------------------------------------------------
Celestica-ES1000-48C#
```

#### macsec interface
Shows MACsec interface related information and counters.

**syntax**: `show macsec interface [<eth-interface-name>]`

**Command mode** : EXEC

**Click command** : `root@sonic:~# show macsec`

**Usage**       : Used to display the MACsec interface information and the SAI related counters.

**Supported Releases** :  4.0 or later

**Example**
```
Celestica-ES1000-48C# show macsec interface Ethernet 46
MACsec port(Ethernet46)
---------------------  ---------------
cipher_suite          GCM-AES-XPN-256
enable                True
enable_encrypt        True
enable_protect        True
enable_replay_protect False
profile               test
replay_window         0
send_sci              False
---------------------  ---------------
        MACsec Egress SC (b4db91e8b8980001)
        -----------  -
        encoding_an 1
        -----------  -
                MACsec Egress SA (1)
                -------------------------------------  ----------------------------------------------------------------
                auth_key                               93D629EC0F353EA20FACF8B07548A668
                next_pn                                1
                sak                                    BB01B0CA8804ABE5B02330BEECFC1C9BCEB51D3A9B8BFDD34B8EDF62CB406EDF
                salt                                   41634400289F224FCF0DDDED
                ssci                                   2
                SAI_MACSEC_SA_ATTR_CURRENT_XPN         5
                SAI_MACSEC_SA_STAT_OCTETS_ENCRYPTED    1144
                SAI_MACSEC_SA_STAT_OCTETS_PROTECTED    1144
                SAI_MACSEC_SA_STAT_OUT_PKTS_ENCRYPTED  4
                SAI_MACSEC_SA_STAT_OUT_PKTS_PROTECTED  4
                -------------------------------------  ----------------------------------------------------------------

        MACsec Ingress SC (b4db91e8b8d40001)
                MACsec Ingress SA (1)
                -------------------------------------  ----------------------------------------------------------------
                active                                  True
                auth_key                                93D629EC0F353EA20FACF8B07548A668
                lowest_acceptable_pn                    1
                sak                                     BB01B0CA8804ABE5B02330BEECFC1C9BCEB51D3A9B8BFDD34B8EDF62CB406EDF
                salt                                    41634400289F224FCF0DDDED
                ssci                                    1
                SAI_MACSEC_SA_ATTR_CURRENT_XPN          15
                SAI_MACSEC_SA_STAT_OCTETS_ENCRYPTED     0
                SAI_MACSEC_SA_STAT_OCTETS_PROTECTED     0
                -------------------------------------  ----------------------------------------------------------------
Celestica-ES1000-48C#
Celestica-ES1000-48C#
```

#### running-config macsec

**syntax**: `show running-config macsec`

**Command mode** : EXEC

**Click command** : None

**Usage**       : Used to display the running configurations of MACsec.

**Supported Releases** :  4.0 or later

**Example**
```
Celestica-ES1000-48C# show running-config macsec
!
!
macsec profile test primary-cak 207b757a60617745504e5a20747a7c76725e524a450d0d01040a0c75297822227e07554155500e5d5157786d6c2a3d2031425a5e577e7e727f6b6c033124322627 primary-ckn 6162636465666768696A6B6C6D6E6F707172737475767778797A303132333435 priority 1 cipher-suite GCM-AES-XPN-256
Celestica-ES1000-48C#
```
