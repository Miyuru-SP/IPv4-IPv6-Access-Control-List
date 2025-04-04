# ACL Configuration Files

## Overview
This repository contains separate ACL configuration files for IPv4 and IPv6 networks. These configurations help in setting up and managing Access Control Lists (ACLs) on routers to regulate network traffic.

## Files
- `ipv4_acl_config.md`: Contains IPv4 ACL configurations, including standard and extended ACLs.
- `ipv6_acl_config.md`: Contains IPv6 ACL configurations, including named ACLs.

## IPv4 ACL Configurations
- **Basic Router Configuration**: Setup of interfaces and static routing.
- **Standard ACLs**: Configurations for blocking and permitting specific hosts and networks.
- **Extended ACLs**: Configurations for advanced filtering based on source/destination IP, ports, and protocols.

## IPv6 ACL Configurations
- **Basic Router Configuration**: IPv6 address assignments and RIP routing.
- **Named ACLs**: Rules for denying or permitting specific traffic types based on IPv6 addresses and services.

## Usage
1. Copy the relevant configuration commands into your router's CLI.
2. Apply ACLs to the appropriate interfaces as shown in the configuration.
3. Verify ACL implementation using `show access-lists` for IPv4 and `show ipv6 access-list` for IPv6.

## Notes
- IPv4 ACLs can be numbered or named, while IPv6 ACLs only support named ACLs.
- Always test ACL configurations in a lab environment before deploying them in production.

For any issues or contributions, please raise an issue or submit a pull request.
