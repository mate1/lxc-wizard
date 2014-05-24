lxc-wizard
---

lxc-wizard creates LXC containers according to specified templates. Templates can provide the following pieces of functionality:

* `addsshkey` add an SSH key for a user
* `adduser` add a user
* `dns` set up DNS
* `etc_hosts` set up /etc/hosts
* `extras` do extra work
* `main` main OS installation
* `network` network set up
* `rootpass` set the root password

A Debian/Squeeze template has the following structure:

    templates
    ├── debian
        └── squeeze
            ├── addsshkey
            ├── adduser
            ├── dns
            ├── etc_hosts
            ├── extras
            ├── main
            ├── network
            └── rootpass

lxc-wizard supports the following options during container creation:

   --template TPL  template (dir) that will define the container's layout

    --fqdn DQDN     full qualified domain name of the target container
    --hostname HOST hostname (if it can't be extracted from the fqdn)
    --domain DOMAIN domain name (if it can't be extracted from the fqdn)
    --dnsdomain DOMAIN domain used in resolv.conf
    --search SEARCH dns search domains in resolv.conf
                    (can be passed multiple times)
    --ns1    NS1    first name server
    --ns1    NS1    second name server
    --ipaddr IPADDR ip address (if it can't be found by gethost call)
    --gwaddr IPADDR gateway address

    --rootpass      the root password to set
    --user          user to add in the format user:pass
                    (can be passed multiple times)
    --key           add the key to given user, in the format
                    user:/path/to/key
                    (can be passed multiple times)

    --postcreate    script to copy into the container and run
                    after the container is created (in the chroot)

    Anything passed at the end after -- will be passed along to the
    post create script. For example: -- --cluster-id 1

lxc-conjure
---

lxc-conjure is a wrapper around lxc-wizard that makes creating complete environments via spell (definition) files quick
and pretty painless.

The following dependencies must be met:

    Parallel::Runner
    Number::Spell
    libtie-ixhash-perl libfile-slurp-perl libfile-slurp-unicode-perl libmojolicious-perl libdata-section-simple-perl

lxc-conjure uses spells to define hosts or environments that should be built.

lxc-conjure supports the following options:

    --spell     Spell (file) to get containers from.
     
    Actions:
    --create    Create containers.
    --start     Start containers.
    --stop      Stop containers.
    --restart   Restart containers.
    --destroy   Destroy containers.
    --info      Get containers' information.
    
    Spell enhancers:
    
    --parallel  Create containers in parallel across
                different hosts.
 

