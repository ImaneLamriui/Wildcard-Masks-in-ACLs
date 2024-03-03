# Wildcard-Masks-in-ACLs

<p align="center">
<img src="net-SEC.png"></p>

__ACLs__: __"Access Control Lists"__ are configurations implemented on networking devices like routers or firewalls. They're used to manage and regulate the flow of traffic entering or exiting a network based on specific criteria. These criteria could include factors such as IP addresses, protocols, or ports. ACLs are typically applied to specific network interfaces on networking devices and can be configured to manage both inbound and outbound traffic flows. They serve as critical tools for __enforcing security policies__ and __access controls__ within a network environment, enabling administrators to regulate traffic effectively and maintain __network integrity__.

### ACLs can be categorized into two primary types:

__Standard Access Control Lists (Standard ACLs)__: These ACLs primarily focus on the source IP address of the traffic. They're capable of permitting or denying traffic based solely on the source IP address.

__Extended Access Control Lists (Extended ACLs)__: In contrast, Extended ACLs offer a broader range of criteria for filtering. They can specify various parameters such as source and destination IP addresses, protocols, ports, and more, providing more detailed control over traffic.

https://community.cisco.com/t5/networking-knowledge-base/cisco-access-control-lists-acl/ta-p/4182349

###### __Example__

We want to apply a __wildcard__ for a range that goes from 172.16.8.0 to 172.16.15.0.
We'll need a block size of 8 because we have 8 subnets.
The network number will be 172.16.8.0 and the wildcard will be __0.0.7.247__-.

So, is __the first__ wildcard __0.0.7.255__?

No, actually, the first wildcard in this case would be __0.0.7.247__.

Here's the breakdown:

The first octet of the IP address range goes from 172 to 172, which means it doesn't change. Therefore, the wildcard for the first octet would be 0.
The second octet of the IP address range goes from 16 to 16, which also means it doesn't change. The wildcard for the second octet would also be 0.
The third octet of the IP address range goes from 8 to 15, which means there are 8 possible values. The block size is 8, so the wildcard for the third octet would be 8 - 1 = 7.

__The wildcard__ value is calculated by subtracting the block size minus one from the highest value in the corresponding octet.

For the third octet, the block size is 8 (since there are 8 subnets) and the highest value in that octet is 15. Therefore, to calculate the wildcard in that octet, we subtract 15 minus 7 (block size minus one), which gives us 8.

In binary, 8 is represented as 00001000. Wildcards are represented as the one's complement of the binary value. Therefore, to get the correct wildcard value, we flip all the bits, which gives us 11110111. In decimal, this is equal to 247.

So, the correct wildcard for the third octet would be 247. Therefore, the complete wildcard would be __0.0.7.247__.

The calculation for the last wildcard is done by subtracting the lowest value of the range (8) minus 1 from the maximum possible value for the third octet (15), resulting in 7. Since the maximum value an octet of an IP address can have is 255, the last wildcard would be __255 - 7 = 248__.
