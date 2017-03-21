Knoten "Wentorf_Free_And_Open_002" (WDR4300)
Dient als normaler WiFi Access Point, der Switch wurde umkonfiguriert und verteilt die VLANs für DSL uplink, Futro und Mesh on LAN
* WAN: Unbenutzt
* LAN1: DSL Uplink (VLAN7)
* LAN2: Futro (VLAN1 und VLAN7/tagged)
* LAN3: Mesh on LAN (VLAN1)
* LAN4: Mesh on LAN (VLAN1)

'''Config''' (nur die geänderten/hinzugefügten Werte sind aufgelistet)
Über luci "Mesh über LAN" einschalten erstellt die wichtigsten Parameter in /etc/config/network, dann muss der Switch umkonfiguriert werden
    # /etc/sysconfig/network changes auf Wentorf_Free_And_Open_002
    config switch_vlan                        
        option device 'switch0'           
        option vlan '1'
        # port 2(=LAN1) aus VLAN1 (Mesh) entfernt                   
        option ports '0t 3t 4 5' 
    
    # neues VLAN7 erzeugen auf port 2(=LAN1/DSL Uplink) und getagged senden auf port 3(=LAN2/Futro)
    config switch_vlan                        
        option device 'switch0'           
        option vlan '7'                   
        option ports '2 3t'
