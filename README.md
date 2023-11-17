# SWAP
How to stop worrying and enable the fucking SWAP on Linux server
```bash
swapon -s

df -h

# Create 2GB Swap file 2048K
dd if=/dev/zero of=/mnt/swapfile bs=1024 count=2048k

mkswap /mnt/swapfile

swapon /mnt/swapfile

echo /mnt/swapfile none swap defaults 0 0 >> /etc/fstab

chown root:root /mnt/swapfile 

chmod 0600 /mnt/swapfile

#swappiness = 0: swap is only used when RAM is used up.
#swappiness = 10: swap is used when 10% RAM is available.
#swappiness = 60: swap is used when the RAM is 60% free.
#swappiness = 100: swap takes precedence as RAM.

cat /proc/sys/vm/swappiness

sysctl vm.swappiness=10

nano  /etc/sysctl.conf
#add: vm.swappiness=30

sysctl -p

```
