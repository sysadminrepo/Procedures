# A simple script for remotely rebooting a Ubiquiti UniFi access point

## Requires bash and sshpass (https://sourceforge.net/projects/sshpass/)
which should be available via dnf, yum, or apt on your *nix distro.

# USER-CONFIGURABLE SETTINGS
username=albatros
password=4lqu!m!574
known_hosts_file=/dev/null
uap_list=( 192.168.253.200 192.168.254.66 192.168.254.56 192.168.254.57 )

# SHOULDN'T NEED TO CHANGE ANYTHING PAST HERE
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
