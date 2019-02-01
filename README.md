# TripleO Overcloud, Ansible Role

An Ansible role to create demo resources on the Overcloud.

## Requirements

None.

## Dependencies

None.

## Role Variables

* tripleo_overcloud_cirros_url = The URL to download the CirrOS image from.

## Example Playbook

```
---
- hosts: localhost
  gather_facts: False
  roles:
    - ansible_role_tripleo_overcloud
```

If using a [standalone TripleO deployment](https://docs.openstack.org/tripleo-docs/latest/install/containers_deployment/standalone.html), add an IP address on the Overcloud's floating IP network interface to access the default CirrOS instance.

```
$ sudo ip address add 10.0.0.5/24 dev br-ctlplane
$ export OS_CLOUD=standalone
$ openstack server show --format value --column addresses cirros_instance
$ ssh -l cirros 10.0.0.X # Replace X
password: gocubsgo
```

## License

Apache v2.0
