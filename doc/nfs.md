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



## ubuntu22.04

安装服务器端

sudo apt update

sudo apt install nfs-kernel-server

sudo systemctl is-enabled nfs-server
sudo systemctl status nfs-server

nfs 默认的配置文件是
 "/etc/nfs.conf"

sudo mkdir -p /data
chown nobody:nogroup /data
chown mod 777 /data

sudo vim /etc/exports

/data 192.168.3.0/24(rw,sync,no_subtree_check)

生效
sudo exportfs -a

重启：
sudo systemctl restart nfs-server
sudo systemctl status nfs-server


### 客户端：
sudo apt update
sudo apt install nfs-common
sudo mkdir -p /mnt/data
sudo mount nfs_server_ip:/data /mnt/data

查看
sudo df -h
