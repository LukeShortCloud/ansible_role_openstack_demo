# TripleO Overcloud, Ansible Role

An Ansible role to create demo resources on the Overcloud. These tasks are based on the example usage for setting up a [standalone TripleO containers](https://docs.openstack.org/tripleo-docs/latest/install/containers_deployment/standalone.html) lab environment.

## Requirements

None.

## Dependencies

None.

## Role Variables

### Instance Creation

* tripleo_overcloud_image_url
* tripleo_overcloud_image_name
* tripleo_overcloud_flavor
    * name
    * vcpus
    * disk
    * ram

### Networks

#### Public

* tripleo_overcloud_public_cidr
* tripleo_overcloud_public_allocation_pool
    * start
    * end
* tripleo_overcloud_public_gateway_ip
* tripleo_overcloud_public_dns_nameservers

#### Private

* tripleo_overcloud_private_cidr

## Example Playbook

```
---
- hosts: localhost
  gather_facts: False
  roles:
    - ansible_role_tripleo_overcloud
```

When the playbook is finished, find the IP address of the instance and then log in via SSH.

```
$ export OS_CLOUD=standalone
$ openstack server show --format value --column addresses cirros_instance
$ ssh -l cirros 192.168.24.X # Replace X
password: gocubsgo
```

## License

Apache v2.0
