# qdSSHFS
# Quick &amp; Dirty SSH Filesystem Implementation
# Quick & Dirty SSH Filesystem Mount - Bash Implementation
# Copyright (C) 2015  OpenCloudSolutions@gmail.com
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# http://www.gnu.org/licenses/gpl.txt

#!/bin/bash
remote="remoteserverdomain.tld"
port="22"
user="user"
localMount="/local/mount/location"
remoteMount="/remote/mount/location"
echo 'Q&D SSHFS MOUNT'
nc -z $remote $port  >/dev/null 2>&1
online=$?
if [ $online -eq 0 ]; then
    echo "System is online. Mounting remote directory."
    sshfs -p $port $user@$remote:$remoteMount $localMount
else
    echo "System is offline. Exiting quietly."
    exit
fi
