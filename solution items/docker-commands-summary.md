--��֤�����������У�������������������������ʱִ�е����ֻҪ���������������Ҳ�Ͳ����˳�
docker run --name healthchecksapi -d -p 8000:8000 justmine/healthchecksapi:v1.0 /bin/bash -c "while true; do sleep 1; done"
--���������ݹ���
docker run --name web1 -d -p 80 -v ~/htdocs:/usr/local/apache2/htdocs httpd
docker run --name web2 -d -p 80 -v ~/htdocs:/usr/local/apache2/htdocs httpd
docker run --name web3 -d -p 80 -v ~/htdocs:/usr/local/apache2/htdocs httpd
# volume container �������� ֻ���ṩ���ݣ�������Ҫ��������״̬
>docker create --name vc_data \
>-v ~/htdocs:/usr/local/apache2/htdocs \
>-v /other/useful/tools \
busybox
## ������������ͨ�� --volumes-from ʹ�� vc_data ��� volume container
>docker run --name web4 -d -p 80 -volumes-from vc_data httpd
