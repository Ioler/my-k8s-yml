# nfs-server
sudo su
yum -y install nfs-utils
mkdir /mnt/nfsserv/
vi /mnt/nfsserv/text.txt
vi /etc/exports
systemctl start rpcbind
systemctl start nfs-server
systemctl enable rpcbind
systemctl enable nfs-server

# nfs-client
sudo su
yum -y install nfs-utils
mkdir /mnt/nfsclient/
systemctl start rpcbind
mount -t nfs -o vers=3 10.128.0.10:/mnt/nfsserv/ /mnt/nfsclient/

##mountコマンドのIPアドレスは書き換えること
