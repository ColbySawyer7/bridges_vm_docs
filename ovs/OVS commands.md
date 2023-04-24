OpenVSwitch Commands 

ovs-vsctl add-br "name": Creates a bridge

ovs-vsctl del-br "name": Deletes a bridge

ovs-vsctl add/del-port "Bridge name" "port name" : Add or delete a port to the specific bridge

ovs-vsctl add-port "Bridge name" "interface name and number" tag="number of VLAN"

ovs-vsctl show: Shows all bridges

ifconfig "Bridge name" up/down : Brings up or down bridges

ifconfig "vport name" up/down: Brings up or down tap interfaces

ifconfig "port name" 0: removes Ip address from the port

dhclient "bridge name": gives the bridge an Ip address via DHCP

ip tuntap add mode tap "interface name and number": Creates tap interfaces for VMs 

ovs-appctl fdb/show "Bridge name": Mac address connections for the VM connections
^Connect the VMs to the tap interfaces otherwise you will not see anything

ovs-ofctl show "Bridge name": Shows port mapping in the bridge

ovs-vsctl add-port "Bridge name" "Tap interface name" -- add-port "Bridge name" "Tap interface name"
^Puts the tap interfaces to the bridge, this is if you wanna add multiple with one command

Normally, for an openflow-enabled switch you would need to connect to an SDN controller 
or manually add open entries but by default OVS has a regular flow entry to make it act like a 
normal layer 2 switch.

ovs-ofctl dump-flows "Bridge name": shows all flow entries on the bridge (action will say normal by default)

ovs-vsctl list Bridge/Port/Interface : shows config details of bridges or ports or Interfaces