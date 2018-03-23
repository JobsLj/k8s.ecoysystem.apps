# ���;���˽�вֿ�(registry.geekbuy.cn)
docker tag healthchecksapi:dev registry.geekbuy.cn/justmine/healthchecksapi:v1.3
docker tag healthchecksapi:v1.5 justmine/healthchecksapi:v1.5
http: docker push registry.geekbuy.cn:5000/justmine/healthchecksapi:v1.1
https: docker push justmine/healthchecksapi:v1.5

# ��˽�вֿ�(registry.geekbuy.cn)��ȡ����master
http: docker pull registry.geekbuy.cn:5000/justmine/healthchecksapi:v1.1 
https: docker push registry.geekbuy.cn/justmine/healthchecksapi:v1.1
docker tag registry.geekbuy.cn:5000/justmine/healthchecksapi:v1.1 justmine/healthchecksapi:v1.1

# ��master�ϴ���yml�ļ�
rm health-checks-pod.yml && cat << eof>health-checks-pod.yml

# ��master�ϴ���pod
kubectl create -f health-checks-pod.yml
kubectl apply -f health-checks-pod.yml
kubectl delete -f health-checks-pod.yml

# �鿴pod״̬
kubectl get pod -n k8s-ecoysystem-apps
kubectl describe pod healthchecks-api-5d8984699f -n k8s-ecoysystem-apps
kubectl delete pod health-checks-api -n k8s-ecoysystem-apps

# deployment
cat << eof>health-checks-deployment.yml
kubectl apply -f health-checks-deployment.yml
kubectl delete -f health-checks-deployment.yml
kubectl rollout status deployment/healthchecks-api -n k8s-ecoysystem-apps