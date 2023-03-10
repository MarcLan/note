## Wordpress脚本快速安装

- 登录一台linux ECS，要有EIP

- 任意目录创建.sh文件

  ```
  touch wordpress-install.sh
  ```

- 编辑.sh文件

  ```
  vim wordpress-install.sh
  按i进入编辑模式
  ```

- 复制以下内容至.sh文件

  ```
  #!/bin/bash
  # Install Terraform
  sudo yum install -y yum-utils &&
  sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/RHEL/hashicorp.repo &&
  sudo yum -y install terraform &&
  
  # Install nginx
  yum install -y nginx &&
  systemctl start nginx && systemctl enable nginx &&
  
  # Change nginx configuration
  sed -i '39i location / \n{index index.php index.html index.htm;}\nlocation ~ \\.php$ {\nroot             html;\nfastcgi_pass     127.0.0.1:9000;\nfastcgi_index    index.php;\nfastcgi_param   SCRIPT_FILENAME /usr/share/nginx/html$fastcgi_script_name;\ninclude          fastcgi_params;\n} ' /etc/nginx/nginx.conf &&
  
  # Restart nginx
  systemctl restart nginx &&
  
  # Install php
  rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm &&
  yum -y install php72w-tidy php72w-common php72w-devel php72w-pdo php72w-mysql php72w-gd php72w-ldap php72w-mbstring php72w-mcrypt php72w-fpm &&
  systemctl start php-fpm && systemctl enable php-fpm &&
  
  #Install Redis
  yum install -y gcc-c++ &&
  yum install -y gcc automake autoconf libtool make &&
  
  wget https://hciecloud.obs.cn-north-4.myhuaweicloud.com/phpredis-5.0.2.tar.gz &&
  tar -zxvf phpredis-5.0.2.tar.gz &&
  cd /root/phpredis-5.0.2 &&
  phpize &&
  ./configure --with-php-config=/usr/bin/php-config &&
  make && make install &&
  touch /etc/php.d/redis.ini &&
  echo extension=redis.so >>/etc/php.d/reds.ini &&
  cat /etc/php.d/redis.ini &&
  php -m |grep redis &&
  systemctl restart nginx && systemctl restart php-fpm
  
  # Install wordpress
  cd /usr/share/nginx/html &&
  wget https://hciecloud.obs.cn-north-4.myhuaweicloud.com/wordpress-5.3.1.tar.gz &&
  tar -zxvf wordpress-5.3.1.tar.gz &&
  chown -R nginx:nginx /usr/share/nginx/html/wordpress &&
  chmod -R 777 /usr/share/nginx/html/wordpress
  
  ```

- 保存.sh文件

  ```   
  # 按ECS退出编辑模式
  # 保存更改
  :wq
  ```

- 执行wordpress安装，确保执行命令时在wordpress-install.sh文件

  ```
  chmod +x wordpress-install.sh
  sh wordpress-install.sh
  ```

- 完成后测试 http://ECS EIP/wordpress，若出现wordpress连接数据库配置界面，表示安装成功

  