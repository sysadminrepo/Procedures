# A simple script for remotely rebooting a Ubiquiti UniFi access point

You can download the script [here](https://github.com/sysadminrepo/Procedures/edit/main/Cloud%20Services/Microsoft%20Azure/4-Mount-an-Azure-blob-storage-on-Linux-using-NFSv3-protocol.md)

## Requires bash and sshpass (https://sourceforge.net/projects/sshpass/)
which should be available via dnf, yum, or apt on your *nix distro.

# USER-CONFIGURABLE SETTINGS
```console
username=<USERNAME>
password=<PASSWORD>
known_hosts_file=/dev/null
uap_list=( 192.168.2.200 192.168.2.66 192.168.2.56 192.168.2.57 )
```
# SHOULDN'T NEED TO CHANGE ANYTHING PAST HERE
```console
for i in "${uap_list[@]}"
do

        echo "Rebooting UniFi access point at $i..."
        if sshpass -p $password ssh -oStrictHostKeyChecking=no -oUserKnownHostsFile=$known_hosts_file $username"@$i" reboot; then
                echo "Access point at $i rebooted!" 1>&2
        else
                echo "Could not reboot access point at $i." 1>&2
        fi
done
exit 0
```
