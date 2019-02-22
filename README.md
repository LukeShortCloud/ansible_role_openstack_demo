# OpenStack Demo, Ansible Role

An Ansible role to create demo resources on the Overcloud. These tasks are based on the example usage for setting up project resources after deploying a [standalone TripleO containers](https://docs.openstack.org/tripleo-docs/latest/install/containers_deployment/standalone.html) lab environment. This role requires the use of an `admin` account on the Overcloud to create and manage the public network.

## Requirements

* Ansible >= 2.6
* openstacksdk

## Dependencies

None.

## Role Variables

* openstack_demo_method = Create the demo resources using `ansible` or `heat`. Default: `ansible`.

### Instance Creation

* openstack_demo_image_url
* openstack_demo_image_name
* openstack_demo_flavor
    * name
    * vcpus
    * disk
    * ram

### Networks

#### Public

* openstack_demo_public_cidr
* openstack_demo_public_allocation_pool
    * start
    * end
* openstack_demo_public_gateway_ip
* openstack_demo_public_dns_nameservers

#### Private

* openstack_demo_private_cidr

## Example Playbook

```
---
- hosts: localhost
  gather_facts: False
  roles:
    - ansible_role_openstack_demo
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
