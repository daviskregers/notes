# Add new VM to Xen Server

```

xe vm-install template="Debian Wheezy 7.0 (64-bit)" new-name-label="PHP7"
xe cd-list

UUID=d0a30d43-94b4-de03-e746-0ac8dea5e587
NAME="PHP7"
ISO="debian-7.11.0-amd64-netinst.iso"
NETWORK=43eb06af-7ab7-3c44-d20e-a3a62662042a

xe vm-disk-list vm="$NAME"
VDI=6b5d3560-c4fe-4a58-936d-c78f1adc279c

xe vm-cd-add uuid=$UUID  cd-name=$ISO device=1
xe vm-param-set HVM-boot-policy="BIOS order" uuid=$UUID

#network 619d8790-cf2d-b6f7-ae73-114eea800c63

xe vm-memory-limits-set dynamic-max=4000MiB dynamic-min=512MiB static-max=4000MiB static-min=512MiB uuid=$UUID
xe vdi-resize uuid=$VDI disk-size=200GiB

xe vm-start uuid=$UUID

DOMID=`list_domains | grep $UUID | awk '{ print $1 }'`
xenstore-read /local/domain/$DOMID/console/vnc-port

```