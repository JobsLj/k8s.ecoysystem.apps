# ������ǩ��֤��
$ mkdir -p certs

$ openssl req \
  -newkey rsa:4096 -nodes -sha256 -keyout certs/domain.key \
  -x509 -days 365 -out certs/domain.crt

Be sure to use the name [Ŀ������] as a CN.

# docker client��װCA֤��
sudo mkdir -p /etc/docker/certs.d/registry.geekbuy.cn
sudo cp certs/domain.crt /etc/docker/certs.d/registry.geekbuy.cn/ca.crt
# ��װ֤�������Docker Daemon
sudo service docker restart
