## Blueprints
* [Multilayer-APP-Blueprint](#multilayer-app-blueprint)
* [REAN-VPN-between-VPCs-Blueprint](#rean-vpn-between-vpcs-blueprint)
* [REAN-Jenkins-Blueprint](#rean-jenkins-blueprint)
* [REAN-HealNow-Blueprint](#rean-healnow-blueprint)
* [SoftNAS-HA.deploynow](#softnas-ha)
* [REAN-RADAR](#rean-radar)

* [REAN-VerifyNow-Blueprint](#rean-verifynow-blueprint)


## Multilayer APP Blueprint
<TBC>

## REAN Jenkins Blueprint
<TBC>

## REAN HealNow Blueprint
<TBC>

## SoftNAS HA
<TBC>

## REAN RADAR
<TBC>

## REAN VerifyNow Blueprint
<TBC>

## REAN VPN between VPCs Blueprint

### Openswan
  Amazon Virtual Private Cloud (Amazon VPC) provides customers with tremendous network routing flexibility. This document describes how a customer can create a secure IPSec tunnel to connect multiple VPCs into a larger virtual private network that allows instances in each VPC to seamlessly connect to each other using private IP addresses.

### Example VPC Setup

![alt tag](http://awsmedia.s3.amazonaws.com/articles/connecting-multiple-vpcs-with-ec2-instances/example_vpc_setup.jpg)

### Steps to deploy

- Import environment from blueprint in DeployNow from location : https://github.com/reancloud/deploynow-blueprints
- Update input variable on DeployNow UI deploynow_ip, my_public_ip, EIP1_allocation_id, EIP2_allocation_id
   eg. Input variables
   ```json
  {
  "VPC1_CIDR": "10.0.0.0/16",
  "VPC2_CIDR": "172.16.0.0/16",
  "deploynow_ip": "54.69.86.230",
  "my_public_ip": "202.149.218.202",
  "EIP1_allocation_id": "eipalloc-5928d33f",
  "EIP2_allocation_id": "eipalloc-2628d340"
  }
  ```

- Deploy environment
1. REAN-VPN-between-VPCs-Network-Blueprint
2. REAN-VPN-between-VPCs-Blueprint
- Your instances from different VPC's can communicate.

- Destroy environment
1. REAN-VPN-between-VPCs-Blueprint
2. REAN-VPN-between-VPCs-Network-Blueprint
