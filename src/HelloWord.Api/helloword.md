
docker tag hellowordapi:dev justmine/hellowordapi:v1.1
docker push justmine/hellowordapi:v1.1

# ��master�ϴ���yml�ļ�
rm hello-world-pod.yml && cat << eof>hello-world-pod.yml

# ��master�ϴ���pod
kubectl create -f hello-world-pod.yml
kubectl apply -f hello-world-pod.yml
kubectl delete -f hello-world-pod.yml

# �鿴pod״̬
kubectl get pod
kubectl describe pod hello-world-api
kubectl delete pod hello-world-api

#�������
rm hello-world-pod.yml && cat << eof>hello-world-service.yml
kubectl apply -f hello-world-service.yml
kubectl get service hello-world-api-svc



