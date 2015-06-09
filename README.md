# tutum-openstack

Collection of tools to manipulate tutum nodes launched on an openstack public cloud.

Only `create` for now. `terminate` should follow.

**Author**: Jean-Christophe Hoelt <hoelt@fovea.cc>

## Requirements

 * tutum-cli
 * docker-machine

## Usage

Set your openstack environment.

```sh
export OS_AUTH_URL=
export OS_TENANT_ID=
export OS_TENANT_NAME=
export OS_USERNAME=
export OS_PASSWORD=
export OS_REGION_NAME=
```

Set your tutum environment.

```sh
export TUTUM_USER=
export TUTUM_APIKEY=
```

Bring it on!

```sh
tutum-openstack-create [options] my-node-name
```

### Options

```sh
--tag "name"                  Tag added to the tutum node (can set multiple).
--openstack-auth-url          OpenStack authentication URL [$OS_AUTH_URL]
--openstack-endpoint-type     OpenStack endpoint type (adminURL, internalURL or publicURL) [$OS_ENDPOINT_TYPE]
--openstack-flavor-id         OpenStack flavor id to use for the instance
--openstack-flavor-name       OpenStack flavor name to use for the instance
--openstack-floatingip-pool   OpenStack floating IP pool to get an IP from to assign to the instance
--openstack-image-id          OpenStack image id to use for the instance
--openstack-image-name        OpenStack image name to use for the instance
--openstack-insecure          Disable TLS credential checking.
--openstack-net-id            OpenStack network id the machine will be connected on
--openstack-net-name          OpenStack network name the machine will be connected on
--openstack-password          OpenStack password [$OS_PASSWORD]
--openstack-region            OpenStack region name [$OS_REGION_NAME]
--openstack-sec-groups        OpenStack comma separated security groups for the machine
--openstack-ssh-port "22"     OpenStack SSH port
--openstack-ssh-user "root"   OpenStack SSH user
--openstack-tenant-id         OpenStack tenant id [$OS_TENANT_ID]
--openstack-tenant-name       OpenStack tenant name [$OS_TENANT_NAME]
--openstack-username          OpenStack username [$OS_USERNAME]
```

### Example

```sh
tutum-openstack-create \
    --openstack-flavor-name "ra.intel.sb.m" \
    --openstack-image-name "Ubuntu 14.04" \
    --openstack-net-name "Ext-Net" \
    --openstack-sec-groups "default" \
    --openstack-ssh-user "admin" \
    --tag "cpu" --tag "cluster1" \
    cluster1-node01
```

### Note

The machine name will also be added as a tag to the added node.

