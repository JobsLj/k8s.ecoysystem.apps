# ���;���˽�вֿ�(registry.geekbuy.cn)
docker tag healthchecksapi:dev registry.geekbuy.cn/justmine/healthchecksapi:v1.1
docker tag healthchecksapi:dev justmine/healthchecksapi:v1.1
http: docker push registry.geekbuy.cn:5000/justmine/healthchecksapi:v1.1
https: docker push registry.geekbuy.cn/justmine/healthchecksapi:v1.1

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
kubectl get pod
kubectl describe pod health-checks-api
kubectl delete pod health-checks-api

