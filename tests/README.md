TEST: ansible-role-sysctl
=========================

This file describe the manual step to test the role.

## Setup

- Create a host for testing (a vm, a container, an instance on a cloud provider...)
- Update the `inventory` file to configure your new host, add `ansible_become=yes` if needed.

## Test1 : bootstrap

### Launch

    ansible-playbook -i inventory test.yml

### Results

It should:
 - connect to your host
 - setup sysctl

*Note:* You have to verify all that manually.

## Test2 : idempotent

### Launch

    ansible-playbook -i inventory test.yml

### Results

It should:
 - not change anything.

