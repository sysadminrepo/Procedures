# Increase Linux TCP connections


## How To Fix

You may need to temporarily or permanently increase this value. You should consult with a qualified systems administrator before making these changes.

Check how many active connections are being tracked.

cat /proc/sys/net/netfilter/nf_conntrack_count

Check the current max value of nf_conntrack

cat /proc/sys/net/netfilter/nf_conntrack_max

Change the value temporarily to something higher (please note, that increasing this number will likely increase the system resource usage and load as it will be handling more connections at a time)

echo 524288 > /proc/sys/net/netfilter/nf_conntrack_max

To make this change permanent, please add the following line to the end /etc/sysctl.conf

net.netfilter.nf_conntrack_max = 524288