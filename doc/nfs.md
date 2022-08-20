yum -y install nfs-utils
mkdir /data/mysql -p
cat /etc/exports
/data *(rw,sync,no_root_squash)
systemctl restart nfs-server
systemctl enable rpcbind
systemctl enable nfs-server
showmount -e
Export list for master:
/data *
