# �鿴�Ѱ�װ��chart
helm search <chartname>

# �ֿ�
helm repo list
helm repo add

# Tiller �������������Ȩ��
kubectl create serviceaccount --namespace kube-system tiller
kubectl create clusterrolebinding tiller-cluster-rule --clusterrole=cluster-admin --serviceaccount=kube-system:tiller
kubectl patch deploy --namespace kube-system tiller-deploy -p '{"spec":{"template":{"spec":{"serviceAccount":"tiller"}}}}'

# �鿴�ѷ������б�
helm ls

# �����汾
helm install <chart path>