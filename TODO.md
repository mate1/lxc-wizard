* add ability to write /etc/hosts from within conjure itself in case the IPs / hostnames are not in DNS
* support running multiple profiles for a single container install
* set time zone in containers
* disable respawing error
* fix perl: warning: Please check that your locale settings:
* login prompt does not show on lxc-start
  - in the inittab replace `1:2345:respawn:/sbin/getty 38400 tty1` with `1:2345:respawn:/sbin/getty 38400 console`

