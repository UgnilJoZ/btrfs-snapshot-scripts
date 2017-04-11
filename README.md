# btrfs snapshot scripts
## Filesystem creation
```bash
# Ensure that the system resides on a normal (not the root-) subvolume, so we can easily rollback
mkfs.btrfs -L SYSTEM /dev/sdXn
mount -L SYSTEM -o compress=lzo /target
cd /target
btrfs subvolume create scratch
btrfs subvolume create system
btrfs subvolume show system
# Now grap the subvol id in the output and declare the default subvolume:
btrfs subvolume set-default 258 /target # Can differ from yours!
scratch shall be a subvolume w/o COW
chattr +C scratch
mkdir /system/...
cd -
umount /target
mount -L SYSTEM -o compress=lzo /target
test -d /target/... && echo "Success"
```
