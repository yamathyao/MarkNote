# MarkNote
some notes

### Mysql 创建库和用户

创建 database<br>
<code>CREATE database if NOT EXISTS &#96;database&#96; default character set utf8 collate utf8_general_ci;</code>

创建 user<br>
<code>CREATE USER 'user'@'IP_ADDRESS' identified by 'password';</code>

赋予 user 权限<br>
<code>GRANT all privileges ON &#96;database&#96;.&#96;tables&#96; TO 'user'@'IP_ADDRESS' identified by 'password';</code>

应用授权<br>
<code>flush privileges;</code>

回收权限<br>
<code>revoke insert on &#96;database&#96;.&#96;tables&#96; from 'user'@'IP_ADDRESS';</code>

### 零碎

ssh default Temp fix<br>
<code>sudo mkdir /sys/fs/cgroup/systemd</code>

<code>sudo mount -t cgroup -o none,name=systemd cgroup /sys/fs/cgroup/systemd</code>

##### RSA密钥生成命令（openssl命令）
生成RSA私钥<br>
<code>openssl > genrsa -out rsa_private_key.pem 1024</code>

生成RSA公钥<br>
<code>openssl > rsa -in rsa_private_key.pem -pubout -out rsa_public_key.pem</code>

将RSA私钥转换成PKCS8格式<br>
<code>openssl > pkcs8 -topk8 -inform PEM -in rsa_private_key.pem -outform PEM -nocrypt -out private_key_pkcs8.pem</code>

远程 scp（scp 文件 到 IP_ADDRESS 的 /opt，目录下）<br>
<code>scp file root@IP_ADDRESS:/opt</code>

打包压缩<br>
<code>tar -czvf target.tar.gz source/</code>

解压缩<br>
<code>tar -xzvf source.tar.gz -C target/</code>

maven install 所选(-pl) module 以及依赖(-am)<br>
<code>mvn clean install -pl module -am</code>

大容量文件夹<br>
<code>du -s /* | sort -nr</code>

删除 Exited container<br>
<code>docker ps -a | grep "Exited" | awk '{print $1 }'|xargs docker rm</code>

删除 <none> images<br>
<code>docker images|grep none|awk '{print $3 }'|xargs docker rmi</code>
  
<code>docker rmi $(docker images | grep "none" | awk '{print $3}')</code>

删除悬空的镜像<br>
<code>docker image prune -a -f</code>

删除悬空的容器<br>
<code>docker container prune -f</code>

yaml 形式显示 configmap(cm)<br>
<code>kubectl get cm $pod -n kube-system -o yaml</code>

