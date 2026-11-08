# Network Reference

## VLANs

| VLAN ID | Name | Subnet | Gateway | DHCP range | Purpose |
| ---: | --- | --- | --- | --- | --- |
| 1 | Native Unifi Network | 192.168.1.0/27 | 192.168.1.1 | 192.168.1.1 - 192.168.1.30 | Management |
| 10 | Client | 192.168.10.0/27 | 192.168.10.1 | 192.168.10.1 - 192.168.10.30 | Client devices |
| 20 | IoT | 192.168.20.0/26 | 192.168.20.1 | 192.168.20.1 - 192.168.20.62 | IoT devices |
| 30 | Prod | 192.168.30.0/27 | 192.168.30.1 | 192.168.30.1 - 192.168.30.30 | Prod Homelab |
| 40 | Dev | 192.168.40.0/27 | 192.168.40.1 | 192.168.40.1 - 192.168.40.30 | Dev Homelab |
| 50 | Work | 192.168.50.0/29 | 192.168.50.1 | 192.168.50.1 - 192.168.50.6 | Work devices |
| 60 | CCTV | 192.168.50.0/28 | 192.168.60.1 | 192.168.60.1 - 192.168.60.14 | CCTV devices |


## Wi‑Fi SSIDs

| SSID | VLAN | Security | Purpose | Notes |
| --- | ---: | --- | --- | --- |
| csbdc | 10 | WPA2/WPA3 | General client devices |  |
| csbdc_iot | 60 | WPA2/WPA3 | Local only IoT devices | Internet blocked |
| csbdc_work | 50 | WPA2/WPA3 | Work devices only | No lan access |

## Inter-VLAN ACLs

Default policy: `deny`

| Source VLAN | Destination VLAN | Allowed service / port | Action | Reason |
| --- | --- | --- | --- | --- |
| 30 | 60 | * | Allow | Access CCTV cameras |
| 30 | 20 | * | Allow | Access IoT Devices |
| 10 | 30 | * | Allow | Access Kubernetes hosted applications |
| 10 | 40 | * | Allow | Access Kubernetes hosted applications |
| 10 | External | * | Allow | Access Internet |
| 30 | External | * | Allow | Access Internet |
| 40 | External | * | Allow | Access Internet |
| 50 | External | * | Allow | Access Internet |

## Port Forwards

| WAN port | Protocol | Internal host | Internal port | Service | Notes / review date |
| ---: | --- | --- | ---: | --- | --- |
|  |  |  |  |  |  |
|  |  |  |  |  |  |
|  |  |  |  |  |  |
