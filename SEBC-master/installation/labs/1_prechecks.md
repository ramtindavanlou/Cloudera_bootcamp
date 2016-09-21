### nscd

```sh
[root@ip-172-31-15-53 ec2-user]# nscd -g
nscd configuration:

              0  server debug level
            10s  server runtime
              5  current number of threads
             32  maximum number of threads
              0  number of times clients had to wait
             no  paranoia mode enabled
           3600  restart internal
              5  reload count

passwd cache:

            yes  cache is enabled
            yes  cache is persistent
            yes  cache is shared
            211  suggested size
         216064  total data pool size
              0  used data pool size
            600  seconds time to live for positive entries
             20  seconds time to live for negative entries
              0  cache hits on positive entries
              0  cache hits on negative entries
              0  cache misses on positive entries
              0  cache misses on negative entries
              0% cache hit rate
              0  current number of cached values
              0  maximum number of cached values
              0  maximum chain length searched
              0  number of delays on rdlock
              0  number of delays on wrlock
              0  memory allocations failed
            yes  check /etc/passwd for changes

group cache:

            yes  cache is enabled
            yes  cache is persistent
            yes  cache is shared
            211  suggested size
         216064  total data pool size
              0  used data pool size
           3600  seconds time to live for positive entries
             60  seconds time to live for negative entries
              0  cache hits on positive entries
              0  cache hits on negative entries
              0  cache misses on positive entries
              0  cache misses on negative entries
              0% cache hit rate
              0  current number of cached values
              0  maximum number of cached values
              0  maximum chain length searched
              0  number of delays on rdlock
              0  number of delays on wrlock
              0  memory allocations failed
            yes  check /etc/group for changes

hosts cache:

            yes  cache is enabled
            yes  cache is persistent
            yes  cache is shared
            211  suggested size
         216064  total data pool size
              0  used data pool size
           3600  seconds time to live for positive entries
             20  seconds time to live for negative entries
              0  cache hits on positive entries
              0  cache hits on negative entries
              0  cache misses on positive entries
              0  cache misses on negative entries
              0% cache hit rate
              0  current number of cached values
              0  maximum number of cached values
              0  maximum chain length searched
              0  number of delays on rdlock
              0  number of delays on wrlock
              0  memory allocations failed
            yes  check /etc/hosts for changes

services cache:

            yes  cache is enabled
            yes  cache is persistent
            yes  cache is shared
            211  suggested size
         216064  total data pool size
              0  used data pool size
          28800  seconds time to live for positive entries
             20  seconds time to live for negative entries
              0  cache hits on positive entries
              0  cache hits on negative entries
              0  cache misses on positive entries
              0  cache misses on negative entries
              0% cache hit rate
              0  current number of cached values
              0  maximum number of cached values
              0  maximum chain length searched
              0  number of delays on rdlock
              0  number of delays on wrlock
              0  memory allocations failed
            yes  check /etc/services for changes

netgroup cache:

            yes  cache is enabled
            yes  cache is persistent
            yes  cache is shared
            211  suggested size
         216064  total data pool size
              0  used data pool size
          28800  seconds time to live for positive entries
             20  seconds time to live for negative entries
              0  cache hits on positive entries
              0  cache hits on negative entries
              0  cache misses on positive entries
              0  cache misses on negative entries
              0% cache hit rate
              0  current number of cached values
              0  maximum number of cached values
              0  maximum chain length searched
              0  number of delays on rdlock
              0  number of delays on wrlock
              0  memory allocations failed
            yes  check /etc/netgroup for changes

SELinux AVC Statistics:

              1  entry lookups
              0  entry hits
              1  entry misses
              0  entry discards
              1  CAV lookups
              0  CAV hits
              0  CAV probes
              1  CAV misses
```

### ntpd

```
[root@ip-172-31-15-53 etc]# cat ntp.conf
# For more information about this file, see the man pages
# ntp.conf(5), ntp_acc(5), ntp_auth(5), ntp_clock(5), ntp_misc(5), ntp_mon(5).

driftfile /var/lib/ntp/drift

# Permit time synchronization with our time source, but do not
# permit the source to query or modify the service on this system.
restrict default nomodify notrap nopeer noquery

# Permit all access over the loopback interface.  This could
# be tightened as well, but to do so would effect some of
# the administrative functions.
restrict 127.0.0.1
restrict ::1

# Hosts on local network are less restricted.
#restrict 192.168.1.0 mask 255.255.255.0 nomodify notrap

# Use public servers from the pool.ntp.org project.
# Please consider joining the pool (http://www.pool.ntp.org/join.html).
server 0.rhel.pool.ntp.org iburst
server 1.rhel.pool.ntp.org iburst
server 2.rhel.pool.ntp.org iburst
server 3.rhel.pool.ntp.org iburst

#broadcast 192.168.1.255 autokey        # broadcast server
#broadcastclient                        # broadcast client
#broadcast 224.0.1.1 autokey            # multicast server
#multicastclient 224.0.1.1              # multicast client
#manycastserver 239.255.254.254         # manycast server
#manycastclient 239.255.254.254 autokey # manycast client

# Enable public key cryptography.
#crypto

includefile /etc/ntp/crypto/pw

# Key file containing the keys and key identifiers used when operating
# with symmetric key cryptography.
keys /etc/ntp/keys

# Specify the key identifiers which are trusted.
#trustedkey 4 8 42

# Specify the key identifier to use with the ntpdc utility.
#requestkey 8

# Specify the key identifier to use with the ntpq utility.
#controlkey 8

# Enable writing of statistics records.
#statistics clockstats cryptostats loopstats peerstats

# Disable the monitoring facility to prevent amplification attacks using ntpdc
# monlist command when default restrict does not include the noquery flag. See
# CVE-2013-5211 for more details.
# Note: Monitoring will not be disabled with the limited restriction flag.
disable monitor
```
