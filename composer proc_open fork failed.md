dd if=/dev/zero of=/var/swap.1 bs=1M count=1024
mkswap /var/swap.1
swapon /var/swap.1


https://cloud.tencent.com/developer/article/1584362