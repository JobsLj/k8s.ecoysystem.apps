ע��Dockerfile ֧���ԡ�#����ͷ��ע�͡�
# FROM 
>ָ�� base ���� 
>eg: FROM busybox
# MAINTAINER
>���þ�������ߣ������������ַ�����
>eg: MAINTAINER justmine@qq.com
# WORKDIR
>Ϊ����� RUN, CMD, ENTRYPOINT, ADD �� COPY ָ�����þ����еĵ�ǰ����Ŀ¼��
>eg: WORKDIR /testDir
# RUN
>������������ָ�������
>eg: RUN touch tmpfile1
# COPY
>���ļ��� build context ���Ƶ�����
>COPY ֧��������ʽ��ע�⣺src ֻ��ָ�� build context �е��ļ���Ŀ¼��
>1��COPY src dest
>2��COPY ["src", "dest"]
>eg: COPY ["tmpfile2","."]
# ADD
>�� COPY ���ƣ��� build context �����ļ������񡣲�ͬ���ǣ���� src �ǹ鵵�ļ���tar, zip, tgz, xz �ȣ����ļ��ᱻ�Զ���ѹ�� dest��
>eg: ADD ["bunch.tar.gz","."]
# ENV WELCOME "welcome you!"
>���û������������������ɱ������ָ��ʹ�á�
>eg: 
# EXPOSE
>ָ�������еĽ��̼���ĳ���˿ڣ�Ȼ��Docker���ö˿ڱ�¶������
>eg: 
# VOLUME
>���ļ���Ŀ¼����Ϊ volume��
>eg: 
# CMD
>��������ʱ����ָ�������
>Dockerfile �п����ж�� CMD ָ���ֻ�����һ����Ч��CMD ���Ա� docker run ֮��Ĳ����滻��
>eg: 
# ENTRYPOINT
>������������ʱ���е����
>Dockerfile �п����ж�� ENTRYPOINT ָ���ֻ�����һ����Ч��CMD �� docker run ֮��Ĳ����ᱻ�����������ݸ� ENTRYPOINT��
>eg: 