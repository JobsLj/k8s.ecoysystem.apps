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

# Ŀ¼
/root/.helm/cache/archive

# �����汾
helm install https://github.com/justmine66/k8s.ecoysystem.apps/tree/master/k8s/helm/charts/light
helm --dry-run --debug install https://github.com/justmine66/k8s.ecoysystem.apps/tree/master/k8s/helm/charts/light
