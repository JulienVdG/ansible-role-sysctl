ansible-role-sysctl
===================

Applies sysctl settings.

Role Variables
--------------

### Role configuration

`sysctl_default_settings` : The default configuration for sysctl.

You can override this variable to change the default values (unless you use `hash_behaviour=merge`).
The default are based on ansible-role-harden-linux values ie recommendations
from Google Compute Cloud OS images and from UFW firewall.

For more information about this settings have a look at:
- https://cloud.google.com/compute/docs/images/building-custom-os
- https://cloud.google.com/compute/docs/images/configuring-imported-images
- https://git.launchpad.net/ufw/tree/conf/sysctl.conf

The 3 following variables are merged with `sysctl_default_settings` to build the final setting applied to the host.

`sysctl_settings` : This variable allows updating the default settings for all hosts.

`sysctl_group_settings` : This variable should be set for a group to update the settings for that group.

`sysctl_host_settings` : This variable should be set for a host to update the settings for that host.

### Configuration snippets

`sysctl_no_ipv6_autoconf` : Add this to `sysctl_settings` to turn off ipv6 autoconfiguration.

`sysctl_ipv6_use_tempaddr`: Add this to `sysctl_settings` to enable ipv6 privacy addressing.

`sysctl_router` : Add this to `sysctl_settings` to allow to route packets between interfaces.

#### Examples

To enable a group to be a router, add the following to your group vars:
```
sysctl_group_settings: '{{ sysctl_router }}'
```

Dependencies
------------

n/a

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: ansible-role-sysctl }

License
-------

Copyright 2019 Julien Viard de Galbert

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <https://www.gnu.org/licenses/>.

Credits
-------

I want to credit the following sources that inspired me in writing this module:

- [ansible-role-harden-linux](https://github.com/githubixx/ansible-role-harden-linux) by Robert Wimmer were I took all the sysctl initial configuration. This role can be considered a simplified fork of it :)

- The 4 variables override levels default/normal/group/host idea from [nftables](https://github.com/ipr-cnrs/nftables) role by Jérémy Gardais (himself inspired from [Mike Gleason firewall role](https://github.com/mikegleasonjr/ansible-role-firewall)).

Author Information
------------------

Julien Viard de Galbert

http://silicone.blogsite.org/

