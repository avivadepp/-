镜像：centos:7
启动：docker run -it -p 1313:1313 centos:7
打开/etc/yum.repos.d/hugo.repo添加
```
[copr:copr.fedorainfracloud.org:daftaupe:hugo]
name=Copr repo for hugo owned by daftaupe
baseurl=https://copr-be.cloud.fedoraproject.org/results/daftaupe/hugo/epel-7-$basearch/
type=rpm-md
skip_if_unavailable=True
gpgcheck=1
gpgkey=https://copr-be.cloud.fedoraproject.org/results/daftaupe/hugo/pubkey.gpg
repo_gpgcheck=0
enabled=1
enabled_metadata=1
```
执行yum -y install hugo
yum install git 
git clone https://github.com/avivadepp/hugo-doc.git
cd hugo-doc
hugo server --bind 0.0.0.0 -b http://0.0.0.0:1313
记住必须绑定到0.0.0.0，绑定到localhost外部访问不到

Dockerfile
```
FROM centos:7
COPY hugo.repo /etc/yum.repos.d/
RUN yum -y install hugo && yum -y install git
RUN git clone https://avivadepp:xxxxxx@github.com/avivadepp/hugo-doc.git
CMD cd hugo-doc && hugo                  
```
CMD只能写一行，否则只能运行最后一行
docker system prune清理docker
docker build -t ctyun/hugo .
docker save > ctyun.tar ctyun/hugo:latest
运行，注意镜像名称要放在最后否则要报错
docker run  -v $PWD/docs:/hugo-doc/content/docs -v $PWD/out:/hugo-doc/public ctyun/hugo:latest
