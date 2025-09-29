**Make Sure** 
 You Powered On the GNS3 VM Machine and unchecked the Virtualize Intel VT-x/EPT or AMD-V/RVI at the Proccessor section of the VM Setting Before Open GNS3 File.


- Topology Summary

HQ: FortiGate 7.0.9-1 (edge firewall/gateway) connects to IOU4 (core switch/router). IOU4 links to four access switches (Switch1–Switch4) for HR, Sales, IT, and Management VLANs. Each access switch has 2–3 VPCS hosts (PC1–PC12) in its department. FortiGate port to Cloud1 provides a WAN link to Branch.

Branch: FortiGate 7.0.9-2 (edge firewall/gateway) connects to IOU1 (core switch/router). IOU1 connects to four access switches (Switch5–Switch8) for HR, Sales, IT, and Management VLANs. Each access switch has 2 PCs (PC13–PC20) in its department (including a management PC20). FortiGate port to Cloud1 links to HQ.

- What’s Working Well

Clear hierarchical design: FortiGate at core with IOU distribution and VLAN-specific access switches.

Departmental VLAN segregation (HR, Sales, IT, Management ) simplifies traffic isolation.

Consistent device types at both sites (same FortiGate model, IOU core, similar switch setup).

Simulated WAN via “Cloud1” connects HQ and Branch firewalls logically.

- What to Fix or Check

Verify FortiGate port assignments (ensure internal/external ports match design, e.g., Port1 to internal IOU, Port2 to cloud).

Ensure IOU–Switch and IOU–FortiGate links are configured as trunks carrying all VLANs.

Confirm each switch port is in the correct VLAN for its department PCs.

Check any mislabeled or missing connections (e.g., PC3 appears mis-aligned on branch side).

Plan DHCP or static IP addressing for all hosts; ensure default gateways are set (likely FortiGate IPs).

- What to Add Before Configuration

Assign IP addressing schemes to FortiGate interfaces, IOU interfaces, and PC default gateways.

Configure VLANs on IOUs and switches (match HR, Sales, IT, Mgmt VLANs on both sites).

Establish trunk ports between FortiGate and IOU, and between IOU and access switches.

Add any missing devices (ensure all PCs shown are added in GNS3, including management PC20).

Double-check cloud/WAN link settings between HQ and Branch FortiGates.
