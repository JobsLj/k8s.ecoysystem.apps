# ע�� secrete �ļ��е��������ݱ�����ͨ�� base64 ���롣
--base64������������
echo -n admin | base64
echo -n 123456 | base64

--base64��������������
echo -n YWRtaW4= | base64 --decode
echo -n MTIzNDU2 | base64 --decode

# ����secret
rm mysecrete.yml && cat << eof>mysecrete.yaml

kubectl create secret generic mysecret --from-literal=username=admin --from-literal=password=123456
kubectl create secret generic mysecret --from-file=./username --from-file=./password
kubectl create secret generic mysecret --from-env-file=env.txt
kubectl apply -f mysecrete.yaml

kubectl get secret 
kubectl decribe secret <key>
kubectl edit secret <key>

# pod with secret in volume
cat << eof>pod-with-secret-in-volume.yml
kubectl apply -f pod-with-secret-in-volume.yml
kubectl -n default exec -it podwithsecrete sh

cat << eof>pod-with-secret-in-env.yml
kubectl apply -f pod-with-secret-in-env.yml
kubectl -n default exec -it podwithsecreteinenv sh