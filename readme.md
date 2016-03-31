# ci-lxc
ci-lxc is a ci for testing ansible playbooks with lxd / lxc containers. It will create a lxc container from a local lxd image, run a ansible playbook and destroy the lxc.

## Usage

    $ ./ci-lxc.sh <lxc name> <lxc image> [ansible playbook]

## Requirements

    - lxd / lxc
    - local lxd image (see how to below)
    - ansible
    
## how to

### install lxd/lxc

    sudo apt-add-repository ppa:ubuntu-lxc/lxd
    sudo apt-get update
    sudo apt-get install lxd
    newgrp lxd
    
### create a image to work with ci-lxc.sh
    
    lxc launch images:ubuntu/trusty/amd64 a
    lxc exec a 'apt-get update'
    lxc exec a 'apt-get upgrade'
    lxc exec a 'apt-get install aptitude'
    lxc image list
    lxc image alias create <alias name> <fingerprint>
    
### install ansible
    
    sudo apt-add-repository ppa:ansible/ansible
    sudo apt-get update
    sudo apt-get install ansbile
