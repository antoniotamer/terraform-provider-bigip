---
layout: "bigip"
page_title: "BIG-IP: bigip_ltm_node"
sidebar_current: "docs-bigip-resource-node-x"
description: |-
    Provides details about bigip_ltm_node resource
---

# bigip\_ltm\_node

`bigip_ltm_node` Manages a node configuration

For resources should be named with their "full path". The full path is the combination of the partition + name of the resource. For example /Common/my-pool.


## Example Usage


```hcl
resource "bigip_ltm_node" "node" {
  name = "/Common/terraform_node1"
  address = "10.10.10.10"
  connection_limit = "0"
	dynamic_ratio = "1"
	monitor = "default"
	rate_limit = "disabled"
	fqdn = { interval = "3000"}
}

```      

## Argument Reference

* `name` - (Required) Name of the node

* `address` - (Required) IP or hostname of the node

* `state` - (Optional) Default is "user-up" you can set to "user-down" if you want to disable

`connection_limit` - (Optional) Specifies the maximum number of connections allowed for the node or node address, default is 0

 * `monitor` - (Optional) Specifies the name of the monitor or monitor rule that you want to associate with the node.

 * `dynamic_ratio` - (Optional)  Specifies the ratio weight to assign to the node. Valid values range from 1 through 65535. The default is 1, which means that each node has an equal ratio proportion.


 * `rate_limit` - (Optional) Specifies the maximum number of connections per second allowed for a node or node address. The default value is 'disabled'.

 * `interval` - (Optional) Specifies the amount of time before sending the next DNS query. It can also take value as "ttl" when "ttl" is specified the  it sets the Interval to the TTL of the DNS record.
