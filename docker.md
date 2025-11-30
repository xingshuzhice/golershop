```bash

# Add Docker's official GPG key:
sudo apt update
sudo apt install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
Types: deb
URIs: https://download.docker.com/linux/ubuntu
Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
Components: stable
Signed-By: /etc/apt/keyrings/docker.asc
EOF

sudo apt update


sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

 sudo systemctl enable docker

sudo systemctl status docker

```

## 

```bash

docker run -p 3306:3306 --name mysql8 -v /data/docker/mysql/conf:/etc/mysql/conf.d -v /data/docker/mysql/logs:/logs -v /data/docker/mysql/data:/var/lib/mysql -v /etc/localtime:/etc/localtime -e MYSQL_ROOT_PASSWORD=123456 -d --restart unless-stopped mysql:8.0.23


zerone@gg:/data/docker/mysql$ cd conf/
zerone@gg:/data/docker/mysql/conf$ ll
total 12
drwxr-xr-x 2 root root 4096 Nov  7 15:22 ./
drwxr-xr-x 5 root root 4096 Nov  7 14:58 ../
-rw-r--r-- 1 root root   95 Nov  7 15:22 my.cnf
zerone@gg:/data/docker/mysql/conf$ cat my.cnf 
[mysqld]
sql-mode="NO_ENGINE_SUBSTITUTION"
default_authentication_plugin=mysql_native_password


sudo docker run -d --name redis -p 6379:6379 \
  --restart=unless-stopped \
  -v /data/docker/redis/conf/redis.conf:/redis.conf \
  -v /data/docker/redis/data:/data \
  redis:5.0 \
  redis-server --appendonly yes


```


```bash

1. 申请 SSL 证书
# 使用 Let's Encrypt 申请免费证书
sudo certbot --nginx -d www.springlandy.com
2. 部署配置文件到服务器
# 复制配置文件到 nginx 配置目录
sudo cp springlandy.com.conf /etc/nginx/sites-available/
sudo ln -s /etc/nginx/sites-available/springlandy.com.conf /etc/nginx/sites-enabled/
3. 测试并重启 nginx
# 测试配置语法
sudo nginx -t

# 重启 nginx
sudo systemctl reload nginx
4. 确保 H5 文件已构建
# 在 shopsuite-mobile 项目中构建 H5
npm run build:h5

```