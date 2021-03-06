--安装 Docker
sudo apt-get install docker-ce=17.03.0~ce-0~ubuntu-xenial
或
apt-get update && apt-get install docker.io
--安装 kubelet、kubeadm 和 kubectl
apt-get update && apt-get install -y apt-transport-httpscurl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -cat <<EOF >/etc/apt/sources.list.d/kubernetes.listdeb http://apt.kubernetes.io/ kubernetes-xenial mainEOFapt-get updateapt-get install -y kubelet kubeadm kubectl
--重置
kubeadm reset
--准备
  --关闭系统交换分区
  swapoff -a
--初始化 Master
kubeadm init --apiserver-advertise-address 192.168.10.105 --pod-network-cidr=10.244.0.0/16 --kubernetes-version=v1.9.4
	--保存有用的过程信息--
	To start using your cluster, you need to run the following as a regular user:

	  mkdir -p $HOME/.kube
	  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
	  sudo chown $(id -u):$(id -g) $HOME/.kube/config

	You should now deploy a pod network to the cluster.
	Run "kubectl apply -f [podnetwork].yaml" with one of the options listed at:
	  https://kubernetes.io/docs/concepts/cluster-administration/addons/
	  eg: Installing a pod network
	  sysctl net.bridge.bridge-nf-call-iptables=1
	  kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/v0.9.1/Documentation/kube-flannel.yml

	You can now join any number of machines by running the following on each node
	as root:
	  kubeadm reset
	  kubeadm join --token 744948.593d033107b82123 192.168.10.105:6443 --discovery-token-ca-cert-hash sha256:e58483e7d06f22ec7633c93455f6fd84625911516093763d1d45301ab1f46455

kubeadm init --apiserver-advertise-address 192.168.10.145 --pod-network-cidr=10.244.0.0/16  --kubernetes-version=v1.9.4
To start using your cluster, you need to run the following as a regular user:

  mkdir -p $HOME/.kube
  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  sudo chown $(id -u):$(id -g) $HOME/.kube/config

You should now deploy a pod network to the cluster.
Run "kubectl apply -f [podnetwork].yaml" with one of the options listed at:
  https://kubernetes.io/docs/concepts/cluster-administration/addons/

You can now join any number of machines by running the following on each node
as root:
  kubeadm reset
  kubeadm join --token 3a0980.d1f8f6c4cfc64ae4 192.168.10.145:6443 --discovery-token-ca-cert-hash sha256:fbaf80fc26a69cc511a52f05bc66ae86c9e7f45c20f5a0ec6eb88c333319dea5

kubeadm init --apiserver-advertise-address 192.168.10.145 --pod-network-cidr=10.244.0.0/16  --kubernetes-version=v1.9.4
To start using your cluster, you need to run the following as a regular user:

  mkdir -p $HOME/.kube
  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  sudo chown $(id -u):$(id -g) $HOME/.kube/config

You should now deploy a pod network to the cluster.
Run "kubectl apply -f [podnetwork].yaml" with one of the options listed at:
  https://kubernetes.io/docs/concepts/cluster-administration/addons/

You can now join any number of machines by running the following on each node
as root:
  kubeadm reset
  kubeadm join --token 9890f9.6dff2525b35b0907 192.168.10.145:6443 --discovery-token-ca-cert-hash sha256:71101db4afbb793c305c15b5f458e93c1f96bc0b13ef8579053bc9f93dead5d3

--腾讯云
sed -i "s/cgroup-driver=cgroupfs/cgroup-driver=systemd/g" /etc/systemd/system/kubelet.service.d/10-kubeadm.conf

systemctl daemon-reload && systemctl enable kubelet && systemctl restart kubelet 

kubeadm init 
--apiserver-advertise-address 150.109.39.33 \
--pod-network-cidr=192.168.0.0/16 \
version=v1.10.0

To start using your cluster, you need to run the following as a regular user:

  mkdir -p $HOME/.kube
  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  sudo chown $(id -u):$(id -g) $HOME/.kube/config

You should now deploy a pod network to the cluster.
Run "kubectl apply -f [podnetwork].yaml" with one of the options listed at:
  https://kubernetes.io/docs/concepts/cluster-administration/addons/

You can now join any number of machines by running the following on each node
as root:

  kubeadm join 10.214.70.185:6443 --token h3gwyu.m47mru3xbij5at38 --discovery-token-ca-cert-hash sha256:b9f94beb388438927f9ad27fcd566cf9c10e02037e3307584aae4fb8542ba69c

