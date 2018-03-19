# �ο� 
>https://docs.docker.com/registry/deploying/
>https://docs.docker.com/registry/insecure/#deploy-a-plain-http-registry
>repository ��������ʽΪ��[registry-host]:[port]/[username]/xxx
# ����[registry-host]
>��ÿһ̨��Ҫʹ��˽�вֿ�Ļ����Ͻ� registry.geekbuy.cn д�뵽/etc/hosts
# ��������http
## 1��http��ʽ,�޸������ļ�
repeat this steps on every engine host that wants to access your registry.
Edit the daemon.json file, whose default location is /etc/docker/daemon.json on Linux or C:\ProgramData\docker\config\daemon.json on Windows Server. 
If the daemon.json file does not exist, create it. Assuming there are no other settings in the file, it should have the following contents:
{
  "insecure-registries" : ["registry.geekbuy.cn:5000"]
}
## 2������docker����
>systemctl daemon-reload
>systemctl restart docker
# ��������
> http: docker run --restart=always --name registry.geekbuy.cn -d -p 5000:5000 -v /geekbuy/registry registry:2
> https: docker run -d \
  --restart=always \
  --name registry \
  -v `pwd`/certs:/certs \
  -e REGISTRY_HTTP_ADDR=0.0.0.0:443 \
  -e REGISTRY_HTTP_TLS_CERTIFICATE=/certs/domain.crt \
  -e REGISTRY_HTTP_TLS_KEY=/certs/domain.key \
  -p 443:443 \
  registry:2
# ������image
>docker tag [image-name] registry.geekbuy.cn/[username]/[image-name]
# ���͵�˽�вֿ�
>docker push registry.geekbuy.cn/[username]/[image-name]
# ��˽�вֿ���ȡ
>docker pull registry.geekbuy.cn/[username]/[image-name]
# �鿴˽�òֿ��еľ���
>curl -XGET registry.geekbuy.cn:5000/v2/_catalog
>��
>��������Ϸ��� http://registry.geekbuy.cn:5000/v2/_catalog
# stop and remove local registry  
>docker container stop registry.geekbuy.cn && docker container rm -v registry.geekbuy.cn
>��
>docker stop registry.geekbuy.cn && docker rm -v registry.geekbuy.cn



