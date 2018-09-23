# VMware manage vCenter clusters
Ansible role that manages clusters in vCenter Server

The configuration of the role is done so that it shouldn't be necessary to
modify the role for any configuration.
All settings can be configured by changing role parameters or by declaring new
config as variable.

Please report any issues or send PR.

## Examples
```yaml
---

- name: Example of how to add a couple clusters in a dc
  hosts: vcenter
    vars:
      vcenter_auth:
        hostname: 192.0.2.1
        username: administrator@abc.lan
        password: super_pass
        validate_certs: False
      vmware_datacenter:
        dc1:
          clusters:
            c1:
              name: prod
              state: present
            c2:
              name: stag
              state: present
  roles:
    - ansible-vmware_cluster  

- name: Example of how to add a cluster and enable some options
  hosts: vcenter
    vars:
      vcenter_auth:
        hostname: 192.0.2.1
        username: administrator@abc.lan
        password: super_pass
        validate_certs: False
      vmware_datacenter:
        dc1:
          clusters:
            c1:
              name: prod
              enable_drs: yes
              enable_ha: yes
              enable_vsan: yes
  roles:
    - ansible-vmware_cluster

  ```

## Role variables
```yaml
# ---------------------------------------------------------------------------
# Define the vcenter auth details to be used
# ---------------------------------------------------------------------------
vcenter_auth: { }


# ---------------------------------------------------------------------------
# Define the vmware datacenter and clusters details to be added/removed
# ---------------------------------------------------------------------------
vmware_datacenters: { }
```

## License
Apache

## Author
Dan Murarasu
