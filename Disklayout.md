# partitions:
GPT fdisk (gdisk) version 1.0.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Number	| Start (sector) | End (sector) | Size | Code  Name
------------------------------------------------------------------
1    |       2048 |         88063 | 42.0 MiB  | EF00 | EFI System
2    |      88064 |       4282367 | 2.0 GiB   | 8200 | Linux swap
3    |    4282368 |      92362751 | 42.0 GiB  | 8304 | Linux x86-64 root (/)
4    |   92362752 |    4294965214 | 2.0 TiB   | 8306 | Linux /srv

# fstab:
 
    # /dev/sda3
    LABEL=SYSCHDEM      	/      	btrfs     	rw,relatime,compress=lzo,ssd,discard,space_cache,subvol=/system 0 0

    # /dev/sda3
    LABEL=SYSCHDEM      	/...  	btrfs     	rw,relatime,compress=lzo,ssd,discard,space_cache,subvolid=5	0 0

    # /dev/sda4 
    LABEL=BINNEN        	/srv  	xfs       	rw,relatime,attr2,inode64,noquota	0 2

    # /dev/sda1
    LABEL=BUTEN         	/boot 	vfat      	rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro	0 2

    # /dev/sda2
    LABEL=SCHWAPP       	none      	swap      	defaults  	0 0

    localhost:gv0		/storage	glusterfs	defaults	0 0

