### Personal use, do not spread

- This is only for version 2.0 ( December 2022 ) , some parts have been changed.
- After the exam, memorize the questions, and then write the questions.
- 100% (It's changed to 3.0 recently, this is for lab 2.0) real questions, non-simulation questions
- The code is in the exam text, no need to memorize, copy it.

---

### 0 Exam Description

####  0.0 Exam is five parts

- Intra-city DR on the cloud (30 points)
- Service deployment on the cloud (26 points)
- Application deployment on the cloud (12 points)
- Cloud O&M management (12 points)
- Topics (20 points)

#### 0.1 Exam Precautions

- The lab environment is HUAWEI CLOUD official website: http://www.huaweicloud.com/

- Specify a HUAWEI CLOUD account and complete the exam under this account.

  >The account has logged in before the exam starts.

- Select default for the enterprise project.

  >No other enterprise projects

- After the exam, do not close cloud resources. Otherwise, the examiner will not be able to complete the marking.

- If the resource specifications are sold out, contact the examiner.

  >did not encounter this situation

- All passwords in the exam are: P@ssw0rdHCIE0lab999

  >All resources use secondary passwords.

- Screenshots are required during the exam. All screenshots are saved to the HCIE-cloud folder and named as required.

- Screen recording throughout the exam process. After the exam, compress and upload the video.

  >Reserve at least 20 minutes for compressed video upload. The upload may fail due to poor network conditions.

- All steps are scored 6 separately. Please arrange the exam time properly.

#### 0.2 Resource Requirements

- Exam resources must be selected as **On-demand and By-traffic**.
- Cost is 500 yuan / 12 hours

---

### 1 On-Cloud Intra-City DR

#### 1.0 Background

The headquarter of Company A is Beijing, with 500 employees. To better promote employee culture and increase communication channels, the HR department of Company A decides to build an internal employee communication website. The requirements are as follows:

- Resource: Select the nearest region of the company.

  > Beijing 4

- Considering the importance of data, the website must have the intra-city high-reliability disaster recovery capability.

  > Two AZs

- DR drills can be completed in the DR architecture.

  >DRS drill

#### 1.1 Topology

![image-20230407143931089](https://raw.githubusercontent.com/MarcLan/pic/main/image-20230407143931089.png)

> Real Topology![image-20230407153907255](https://raw.githubusercontent.com/MarcLan/pic/main/image-20230407153907255.png)

#### 1.2 Resource Description

- Set up the instance based on the architecture. The instance name must be the same as that in the architecture. Do not delete the service at will.
- Name resources that do not have naming requirements,
- Screenshots as required by the topic
- Cost-optimal allocation of resources

#### 1.3 Lab Requirement

##### 1.3.0 Network Resource Configuration Requirements

- Create a VPC, VPC network segment, and subnet network segment based on the architecture diagram and resource requirements.

  >| Site      | VPC Name   | VPC Segment    | Subnet Name | Subnet Segment | Security Group |
  >| --------- | ---------- | -------------- | ----------- | -------------- | -------------- |
  >| Beijing 4 | web-active | 192.168.0.0/16 | subnet-web  | 192.168.1.0/24 | sg-web         |
  >| Beijing 4 | db-active  | 192.168.0.0/16 | subnet-db   | 192.168.2.0/24 | sg-db          |

- Ensure network connectivity works.

  >- VPC Peering
  >- Create an ECS in each subnet and perform a ping test.

- Resources in the same subnet belong to the same security group. The names are user-defined. Record the VPC network segment, subnet network segment, and security group name in the information.xlsx file.

  ![image-20230425170939562](https://raw.githubusercontent.com/MarcLan/pic/main/image-20230425170939562.png)

- All security groups allow only service traffic in the inbound direction. Do not enable all ports or 0.0.0.0/0.

  >Allow 0.0.0.0/0 to pass through, and then adjust the security group.

##### 1.3.1 Computing Resource Configuration Requirements

- Beijing 4 ECS (ecs-beijing) as the website, S series, CentOS 7.6, and at least two vCPUs

  >Note that it's the S series.

- ECSs are deployed in AZ1 or AZ2.

  > Preferentially select AZ1 when purchasing ECSs.

##### 1.3.2 Database Resource Configuration Requirements

- Use RDS.

  - Database type: database software whose storage engine is InnoDB

    >It's MySQL.

  - The database port is 3310.

    >Write 3310 when creating an RDS DB instance.

  - Active/standby in the region where the HQ is located and AZ-level HA

    >Active/standby different AZs

  - rds-wordpress Create a database named wordpress, log in to rds-wordpress, and save the screenshot of the created wordpress database interface as **1.1-db**.

    >Log in to the RDS DB instance using DAS and create WordPress. The HCIE-cloud folder exists in the screenshot.
    >
    >![image-20230425171348251](https://raw.githubusercontent.com/MarcLan/pic/main/image-20230425171348251.png)

- DCS is used as the enterprise website cache service. The area corresponding to the active/standby DCS instance domain database instance is used.

  >Create a DCS instance as required.

##### 1.3.3 Software Configuration Requirements

- Log in to the corresponding ECS in VNC mode to complete software installation.

  >No other login mode is available. Cloudshell cannot be used.

- ECS software and plug-ins have been configured and web page verification has been completed.

  >After WordPress is installed, you can use the web page to access the ECS EIP for verification.

- Prepare the LNMP environment for the website

  >The following commands are given, but hand-knock exercises are recommended.

##### 1.3.4 Software Configuration Requirements

- Log in to the corresponding ECS in VNC mode and install the software.

- Complete the ECS software and plug-in configuration and web page verification.

- Prepare the LNMP environment for the website

- Install Nginx.

  ```
  yum install -y nginx
  ```

- Sets the Nginx to Start upon System Startup

  ```
  systemctl start nginx && systemctl enable nginx
  ```

- Install php:

  - Upgrade the RPM software package.

    ```
    rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm
    ```

  - Find the webtatic.repo file and change baseurl to the new software package address.


  - yum install php7.2

    ```
    yum -y install php72w-tidy php72w-common php72w-devel php72w-pdo php72w-mysql php72w-gd php72w-ldap php72w-mbstring php72w-mcrypt php72w-fpm
    ```


- Launch php-fpm and set boot

  ```
  systemctl start php-fpm && systemctl enable php-fpm
  ```

- Modify the Nginx configuration file to support PHP and add content to nginx.conf.

  - Add the name of the home page index file to the server field.

  - Add the php invoking method before the end of the server field

    ```
    vi /etc/nginx/nginx.conf
    
    location / {
    	index index.php index.html index.htm;
    }
    
    location ~ \.php$ {
    	root       html;
    	fastcgi_pass   127.0.0.1:9000;
    	fastcgi_index  index.php;
    	fastcgi_param  SCRIPT_FILENAME /usr/share/nginx/html$fastcgi_script_name;
    	include     fastcgi_params;
    }
    ```


- Save and reload the Nginx configuration file.

  ```
  systemctl restart nginx
  ```

- Website construction

  >This section of the command is not given in the title, to memorize.
  
  - In the /usr/share/nginx/html directory, download and decompress the wordpress software. The link is as follows:
    https://hciecloud.obs.cn-north-4.myhuaweicloud.com/wordpress-5.3.1.tar.gz

    >```
    >cd /usr/share/nginx/html
    >wget https://hciecloud.obs.cn-north-4.myhuaweicloud.com/wordpress-5.3.1.tar.gz
    >```
    
  - Set the highest permissions (read, write, and execute) for the decompressed wordpress file.
  
    >```
    >chmod 777 wordpress
    >```
  
  - Open the WordPress website at https://EIP/wordpress through the authentication terminal.
  
  - After WordPress is deployed, take a screenshot of the installation page and name it **1.2-wordpress-web**.
  
    > - Before Wordpress installation
    >
    >   ![image-20230425171531054](https://raw.githubusercontent.com/MarcLan/pic/main/image-20230425171531054.png)
    >
    > - After installation
    >
    >   ![image-20230425171604016](https://raw.githubusercontent.com/MarcLan/pic/main/image-20230425171604016.png)
    >
    > - Setting page
    >
    >   ![image-20230425171644805](https://raw.githubusercontent.com/MarcLan/pic/main/image-20230425171644805.png)
    >
    >   
  
  - Install and configure the Redis plug-in and connect to DCS to provide cache services.
  
    - Yum Install gcc-c++ and make compilation components.
  
    - Install the Redis plug-in.
  
      1. Download and decompress the phpredis extension package: https://hciecloud.obs.cn-north-4.myhuaweicloud.com/phpredis-5.0.2.tar.gz
  
      2. Decompress the package, go to the folder directory, and run the following command
  
         ```
         phpize
         ```
  
      3. Run the following command to generate the makefile file:
  
         ```
         ./configure --with-php-config=/usr/bin/php-config
         ```


- Compile and install the phpredis client:

  > Memorize this

  ```
  make && make install
  ```

- Search for the php.d folder and add the following information to php.d/redis.ini:

  ```
  extension=redis.so
  ```

- Restart related services, which may be restarted in subsequent configurations.

- Check whether the installation is successful.

  ```
  php -m|grep redis
  ```

  > If red "redis" is displayed, the operation is successful.

- Redis plug-in configuration:

  1. Open the wp-config.php configuration file and add the following code:

     ```
     define("FS_METHOD", "direct");
     define("FS_CHMOD_DIR", 0777);
     define("FS_CHMOD_FILE", 0777);
     ```

  2. Add DCS configuration information to wp-config.php.

    ```
    define("WP_REDIS_HOST", "X.X.X.X");
    define("WP_REDIS_PORT", 6379);
    define("WP_REDIS_PASSWORD", P@ssw0rdHCIE0lab999);
    define("WP_REDIS_TIMEOUT", 1);
    define("WP_REDIS_READ_TIMEOUT", 1);
    define("WP_REDIS_DATABASE", P@ssw0rdHCIE0lab999);
    ```

  3. Activate the Redis Object Cache plug-in on the WordPress page.

     > - On the Plug-in page, locate the plug-in or activate the Redis, as shown in the following figure.
     >
     >   ![image-20230425171753273](https://raw.githubusercontent.com/MarcLan/pic/main/image-20230425171753273.png)
     >
     > - Enable Redis Object Cache to connect to the phpredis client.
     >
     >   ![image-20230425171822037](https://raw.githubusercontent.com/MarcLan/pic/main/image-20230425171822037.png)
  
  4. Enable Redis Object Cache to connect to the phpredis client.


  5. In the wp-content/object-cache.php file, modify or add the redis configuration as a parameter as follows:

     ```
     protected function build_parameters() {
             $parameters = [
             'scheme' => 'tcp',
             'host' => 'DCS internal IP', # Add internal IP
             'port' => 6379,
             'password' => 'P@ssw0rdHCIE0lab999', # Add password
             'database' => 0,
             'timeout' => 1,
             'read_timeout' => 1,
             'retry_interval' => null,
     ```

  6. On the WordPress page, check whether the Redis is successfully installed on the plug-in page. Three check marks indicate that the Redis is successfully installed, as shown in **1.3-redis**.

     > ![image-20230425171855742](https://raw.githubusercontent.com/MarcLan/pic/main/image-20230425171855742.png)


##### 1.3.5 Storage DR + DR drill

- Intra-city storage DR configuration
  - Create a protection group named Protection-Group-wordpress at the production site ecs-beijing.

  - Create a protected instance protected-instance-wordpres for ecs-beijing.

  - Enable protection for the protection group.

    >Create as required and enable protection
  
- As shown in the preceding figure, the web-layer service uses SDRS to create a drill instance ecs-beijing-drill, and the data layer uses rds-wordpress to back up and restore the data to the new instance backup-rds.

  >You can manually create a backup and assign it to a new RDS DB instance named backup-rds.

- Modify the DR WordPress configuration file so that ecs-beijing-drill can connect to the database instance backup-rds. If an error is reported, modify the configuration information of the wordprss database and name it as **"1.4-mysql"**

  > ![image-20230425172029113](https://raw.githubusercontent.com/MarcLan/pic/main/image-20230425172029113.png)

- Bind DNAT to the DR drill instance, verify the DR drill instance through the terminal, and save the screenshot of the website corresponding to the DR drill using DNAT. Name the screenshot as **"1.5-dnat"**

  > ![image-20230425172205014](https://raw.githubusercontent.com/MarcLan/pic/main/image-20230425172205014.png)

---

### 2 Cloud service deployment

#### 2.0 Background Introduction

Deploy the DR environment in Shanghai based on module 1

- To promote employee well-being, the company organizes the following activities
- Irregular raffle
- Gifts are given out every Friday night from 19:00 to 20:00 for the coming year
- Websites require remote disaster recovery capabilities

#### 2.1 Lab Topology

![image-20230407143909583](https://raw.githubusercontent.com/MarcLan/pic/main/image-20230407143909583.png)

#### 2.2 Resource Description

Tip: Arrange the experiment sequence to avoid screenshots.

- The instance name is consistent with the environment in the architecture diagram.
- Naming reflects purpose
- Screenshots as required
- Purchase resources based on the cost-optimal solution.
- The resources that have been completed in Lab 1 can be used directly.

#### 2.3 Experiment Requirements

##### 2.3.0 Network Resource Requirements

- Create a VPC based on the architecture diagram and plan subnet segments.

- Two zones use secure encrypted channels.

  > VPN

- The same subnet resources are placed in the same security group. The VPC name, subnet name, and security group name are recorded in the information.xlsx file.

- The ELB uses the minimum connection.

  >Change the polling mode to the minimum connection mode.

- Create a public DNS (no filing required). 80% of the traffic is transmitted through Beijing 4.

  >Configuring the DNS Weight

##### 2.3.1  Requirements for various services

- Images are all from esc-beijing images.

  >- IMS cross-region replication - not easy to use
  >- OBS cross-region replication: The progress is not displayed, and the completion time is unknown.
  >- I was redeploying wordpress in Shanghai.

- Select computing instances with high stability.

  >enhanced type

- System disk size: 50 GB; maximum IOPS: 2000; maximum throughput: 120 MB/s

  >EVS Specifications

- Ensure that VMs running the same service are available at the physical server level.

  >Add to the same anti-affinity group

- The automatically created instance name starts with ecs-auto.

  >Set in the AS.

- Select any AZ for the Beijing 4 and Shanghai 2 scaling groups and ensure load balancing at the data center level.

- Maximum instance 3, minimum instance 1, and expected instance 1 in the AS group

  >Set in the AS.

- Proper scaling policies

  >Configure the policy based on the question requirements.

- The cross-region image replication function is not available. You can transfer images in other modes.

  > OBS

##### 2.3.2 Database Resource Configuration Requirements

- Use the DR database instance to ensure that the database in the DR center is synchronized with the primary database.

  > DRS

- Create a DR site for rds-wordpress and synchronize data from the public network.

  > DRS + EIP

---

### 3 Cloud-based application deployment

#### 3.0 Background

Online store, rolling update, gray release, and container deployment

- CCE cluster, version 1.21

- Module introduction:

  >

  - ui-service: responsible for user UI demonstration

  - api-gateway: exposes resources to ui-service.

  - products-service: product management

  - user-service: user management

  - dao-service: persistent service management

  - shoppingmalldb: database

- Only ui-service provides external services, and other services are internal services.

  >Load balancing service

- Select the corresponding workload type.

  >For other services, select intra-cluster access.

- ELB is recommended for ui-service.

#### 3.1 Lab Topology

![image-20230407144508032](https://raw.githubusercontent.com/MarcLan/pic/main/image-20230407144508032.png)

#### 3.2 Resource Description

| Resource Type | Resource Name    | Resource Specification                                       | Resource Description               |
| ------------- | ---------------- | ------------------------------------------------------------ | ---------------------------------- |
| VPC           | vpc-shoppingmall | Self-planned                                                 | Beijing 4                          |
| EIP           | Customized       | 5 Mbit/s                                                     | On-demand                          |
| ELB           | private-elb      | Private network                                              | Access private network domain name |
| ECS           | cce-terminal     | s6.large.2, 2c4g, Windows Server 2012R2 Standard Edition, EIP 5 Mbit/s | Under vpc-shoppingmall             |
| CCE           | shoppingmall     | on-demand                                                    | Beijing 4                          |

#### 3.3 Experiment Requirements

##### 3.3.0 Network Resource Configuration Requirements

Plan VPCs and subnets and write them into the information.xlsx file.

##### 3.3.1 Cloud Container Cluster Configuration Requirements

- Ensure that ECSs are deployed on different physical servers and CCE clusters support automatic scaling.

  >  When creating an AS node pool, ensure that the node pool is large enough. Otherwise, you need to create a node pool again, which is a waste of time.

  - The total number of CPUs is 40 cores at most.

  - Up to 8 GB of total memory

  - Automatic capacity expansion when the average CPU usage exceeds 75%

  - Automatic capacity expansion when the average memory usage exceeds 85%

  - Nodes in the CCE cluster are automatically scaled in when no tenant container is running for more than 15 minutes.


  - The image has been uploaded to the account. The workload configuration is as follows:


  - Number of instances: stateless 3 and stateful 1


  - Instance specifications:

  - Stateless CPU (1, 1.5), memory (1, 2)

  - Stateful CPU (1, 1.5), memory (2, 3)


- Container cluster network configuration ui-service access based on node EIPs

  - ui-service can be accessed through the ingress. The domain name is www.shoppingmall-current time.com.

    >The ingress must be configured correctly. You are advised to practice more.

  - The rest of the workload is visible internally, and the ports are referenced to the architecture diagram.

  - Log in to the cce-terminal terminal, save the website opened using the intranet domain name, and **take a screenshot of 3.1-cce-web**.

    >Create a Windows ECS in the VPC of the CCE.

##### 3.3.2 Migrating ShoppingmallDB to RDS

- Externally exposed ports of the ShoppingmallDB workload

  >Create a load balancer or a node to access a service and remember the exposed ports.

- Log in to the container where ShoppingmallDB is located and create the MySQL user name and password.

  >Log in to the container. Run the Mysql command to log in to the container and create a user name and password.
  >
  >```
  >mysql
  >create user 'username' identified by 'password'
  >grant all privileges on *.* to ‘username’ identified by ‘password’
  >```

- Log in to the database of the container where ShoppingmallDB is located through the DAS. - **Screenshot**

- DRS tests the connectivity between the source and destination ends.

- Parameters at the opposite end of the DRS. If any problem occurs, modify the parameters as prompted.

  > ![image-20230425172255167](https://raw.githubusercontent.com/MarcLan/pic/main/image-20230425172255167.png)

  > - This takes time. You can click View Details to view how to modify the configuration. Some configurations need to be modified in the container, and some can be modified on the RDS page.

  > - Go to the container and manually modify the mismatched parameters.
  >
  >   ```
  >   docker ps #remember the container_id
  >   docker exec –it CONTAINER ID /bin/bash #go to container
  >   cd /etc/mysql/mysql.conf.d/ #go to mysql configuration file
  >   
  >   # Note that the container does not have the vim command. Therefore, the configuration file cannot be edited. You need to use echo to insert content to the configuration file.
  >   # echo Back up the mysqld.cnf file before inserting data.
  >   
  >   echo “server_id = 3 ” >> /etc/mysql/mysql.conf.d/mysqld.cnf
  >   echo “log-bin = /var/lib/mysql/mysql-bin” >> /etc/mysql/mysql.conf.d/mysqld.cnf
  >   
  >   #Check the configuration
  >   cat /etc/mysql/mysql.conf.d/mysqld.cnf
  >   
  >   #RestartMysql
  >   service mysql restart
  >   ```
  >
  > - When the migration status changes to incremental migration, the migration is complete.
  >
  >   ![image-20230425172912648](C:\Users\l84233197\AppData\Roaming\Typora\typora-user-images\image-20230425172912648.png)
  >
  > - Three migration results** Screenshots**
  >
  >   ![image-20230425172959241](https://raw.githubusercontent.com/MarcLan/pic/main/image-20230425172959241.png)

---

### 4 Cloud Application O&M

#### 4.0 Background

Complete O&M management operations based on experiment 1 and experiment 2.

#### 4.1 Experiment Requirements

##### 4.1.0 CCE+APM

- Configure the APM based on the preceding CCE environment.

  > Click Upgrade > Advanced Configuration > Performance Management Configuration > APM1.0 Probe > Monitoring Group Name > Select the latest version.

- The full link topology of all workloads can be realized on the APM page. - * * Screenshot**

  >If the CCE test is successful, the APM automatically provides the full-link topology, as shown in the following figure.
  >
  >![image-20230425173538340](https://raw.githubusercontent.com/MarcLan/pic/main/image-20230425173538340.png)

- View the api-gateway topology--**Screenshot**

  > Right-click the circle in the figure to expand
  >
  > ![image-20230425173557456](https://raw.githubusercontent.com/MarcLan/pic/main/image-20230425173557456.png)

- Changing the Apdex Value of api-gateway--**Screenshot**

  > ![image-20230425173615109](https://raw.githubusercontent.com/MarcLan/pic/main/image-20230425173615109.png)

##### 4.1.1 Rights Management

> Create as required. All operations are performed on the console.

- Use IAM to create different user groups and grant permissions to them.
- O&M management group: om-group Beijing 4 and all resource management permissions of Shanghai 2
- O&M monitoring group: monitor-group Beijing 4, read-only permission on all resources in Shanghai 2
- Database O&M group: db-group has the administrator rights of database cloud services such as RDS and DCS.

##### 4.1.2 Monitoring and Alarming

- Beijing 4 Configuring Cloud Eye Alarms
- Name: Alarm-web-Error
- Rule: If a website user receives more than 200 404 error codes within 5 minutes, an alarm is generated.
- Frequency: 30 minutes
- Level: Major
- Range: existing ELB instances
- Monitor type: custom event
- Name: Alarm-web-Connection
- Rule: An alarm is generated when the website receives more than 1000 concurrent connection requests within 20 minutes.
- Frequency: 1 hour
- Level: Minor
- Range: existing ELB listener instances
- Type: Custom Event

##### 4.1.3 Cloud Log Management

- In Beijing 4, user access logs are stored in OBS.
- Log group: its-group-weblog
- Log stream: its-topic-elb
- Storage to bucket: elb-log-Current time
- The log format is JSON.
- Perform log dump every 5 minutes
- Beijing 4: Collecting ecs-beijing Logs of the Server
- Log group: its-group-ecs
- Log stream: its-topic-ecs
- Install the ICAgent.
- Set the log collection path to /var/logs/.
- The log format is the default system time.

##### 4.1.4 Backup Policy

- RDS backup policy: The primary RDS database in Beijing 4 is backed up once a day from 01:00 to 02:00. The backup is retained for three days.
- The Beijing DCS is backed up once a day from 01:00 to 02:00. The backup is retained for three days.

---

### 5 Discussion Questions

#### Topic I

Answer the questions according to the following figure

![image-20230407145848322](https://raw.githubusercontent.com/MarcLan/pic/main/image-20230407145848322.png)

- In high-concurrency service scenarios, what are the performance bottlenecks of the architecture and how to optimize the performance bottlenecks?

- Provide specific optimization solutions based on optimization ideas.

  > Based on experience, try to use HUAWEI CLOUD products, such as bandwidth increase, access policy optimization, data access sharding, active/standby database + read-only, and multi-AZ infrastructure.

#### Topic 2

Before moving to the cloud, enterprises need to conduct surveys and answer the following questions based on HUAWEI CLOUD features:

- HUAWEI CLOUD provides different computing resources, such as ECS, BMS, DEH, FunctionGraph, and CCE. Briefly describe the reasons for selecting the preceding services based on scenarios.

  >- ECS scenario: website, e-commerce, graphics, data analysis, and high-performance computing
  >
  >- DEH scenario: For industries that require compliance and security, customers require physical resource isolation, and high performance stability, customers can customize specifications to deploy servers and require flexible server management.
  >
  >- BMS scenario: high security and reliability, no virtualization and performance loss, and high agile deployment efficiency,
  >
  >- Functiongraph:
  >
  >  Advantages: No need to manage servers, automatic code running, enabling customers to focus on services, automatic scaling, no need to pay attention to management, event triggering mechanism, and efficient development. High availability: The system automatically starts a new instance when an exception occurs.
  >
  >  Application scenarios: event-driven applications, web applications, and AI.
  >
  >- CCE: easy-to-use, three master nodes, high reliability, high-performance K8S cluster, and one-stop automatic O&M
  >
  >Scenario: containerized applications, fast elastic scaling, continuous delivery of DevOps, and high-performance scheduling

- Enterprises choose BMS to migrate core databases to the cloud. Briefly describe the advantages of using BMS to deploy Oracle RAC pairs.

  >- Security: Customers can configure virtual networks to improve security and simplify network deployment.
  >
  >- High performance: Dedicated physical servers have high performance, meeting Oracle's requirements.
  >
  >- High IOPS: Ultra-high I/O to 33000 and 1 ms latency
  >
  >- Secure and efficient: Exclusive physical servers provide ultra-high computing performance without virtualization performance loss. In addition, three-copy backup is provided, and data durability reaches 99.99%, ensuring data security and reliability.
  >
  >- Quick provisioning: You can apply for a physical server on the management console and obtain a physical server within 5 minutes without manual intervention. Automatic image installation, network configuration, and EVS disk mounting
  >
  >- Flexible deployment: ECSs are interconnected. Physical servers communicate with external resources through VPCs. They are deployed together with ECSs. Flexible networking is supported. Elastic IP addresses are supported to meet networking requirements in various complex scenarios.
  >
  >- RAC mode: Shared EVS disks are automatically mounted to solve the problem that traditional physical servers are limited by the local disk capacity and meet the requirements of deploying Oracle RAC in enterprise core system clusters.

- Briefly describe the high availability of ECSs at the VM level, physical server level, and data center level based on ECSs.

  >- Virtual layer
  >- Multiple specifications to meet different scenarios.
  >- Multiple images to meet service requirements.
  >- Multiple disk types are available.
  >Reliable data, distributed architecture, and elastic block storage
  >- Security protection, including virus and Trojan horses, DDoS traffic cleaning, network layer isolation, security group protection, and web firewall protection
  >- Automatic backup mechanism, enabling ECSs to be recovered in a timely manner when faults occur.
  >- Auto scaling, automatic capacity expansion based on service volume
  >Monitoring system: Cloud Eye monitors ECSs in real time and sends alarms in real time.
  >
  >- Physical layer:
  >- Professional hardware devices and optimized virtualization technology, eliminating the need for customers to build equipment rooms
  >- Resources can be obtained from physical hardware at any time for elastic scaling.
  >Anti-affinity can be configured to allocate different ECSs to different physical machines, ensuring high reliability.
  >
  >- Data center layer:
  >- For large regional data centers, HUAWEI CLOUD has multiple regional data centers. Customers can choose nearby data centers to reduce network latency and improve access speed.
  >- If an AZ is used, that is, a physical equipment room, the fault of one AZ does not affect other regions. The access speed between AZs is very fast through the intranet.

#### Topic 3

- A customer plans to deploy the enterprise official website on HUAWEI CLOUD. The offline deployment architecture is web-application-database classic three-layer architecture, with about 1000 visits per day. How to design the network architecture?

- Before the system goes online on HUAWEI CLOUD, you need to plan the cloud network architecture. What factors should be considered during the planning?

  >- The VPC network segments and subnet network segments on the cloud and offline cannot conflict,
  >
  >- The number of machines must be planned in advance and the number of machines to be reserved for each subnet.
  >
  >- Security protection policy. In the inbound direction of a security group, the off-cloud migration pipe network must be allowed.
  >
  >- Check whether services need to be provisioned between VPCs and configure VPC peering.

- HUAWEI CLOUD provides two security control mechanisms: security group and network ACL. Please describe the differences in principles, Zones, policies, priorities, and packet groups.

  >- Principle.
  >
  >- A security group is a logical group and provides access policies for the same VPC. ACLs are subnet-level. The two groups can be used together to obtain fine-grained policies.
  >
  >- Security groups protect ECSs and ACLs protect subnets.
  >- Both permit and deny policies are supported.
  >
  >- Priority
  >
  >- Security group: If a rule conflict occurs, the rule takes effect based on the sequence in which the security group is bound, and then the rule priority in the security group takes effect.
  >
  >- ACL: The ACL with a higher priority takes effect, and the ACL with a lower priority does not take effect.
  >
  >- Packet group:
  >
  >- Security group: Only triplets of packets are supported.
  >
  >- Acl: supports the 5-tuple.

#### Topic 4

An e-commerce company's existing service systems are deployed on the Huawei private cloud platform, including:

- Services are running on hundreds of VMs and dozens of physical machines.
- The original service is deployed using the HUAWEI CLOUD virtual solution.
- Logical functional areas are divided into left and right IT units, and the units are highly dependent on each other.


The customer plans to migrate all e-commerce services to HUAWEI CLOUD and has developed the following migration solution:

- Back up the original data.
- Prepare target resources.
- Migrate services.
- Switch services.
- Rollback mechanism

According to the e-commerce business architecture, what resources and tools need to be prepared and what basic configurations need to be made in the second part of resource preparation?

What are the possible migration risks and countermeasures in the third step of service migration and the fourth step of service switchover?

>Prepare resources:
>
>On-cloud and off-cloud networks: Direct Connect, VPN, or public networks must be connected.
>
>- Account resources on the cloud, such as user names and passwords, IAM sub-users, federated users, and AK/SKs, must be prepared.
>
>- Computing resources: ECSs or containers. The SMS tool must be configured to migrate VMs.
>
>- Network: VPCs, subnets, host bit planning, VPC peering (if required), or enterprise routers must be connected.
>
>- Storage: Check whether object storage is available. Prepare OMS and OBS buckets and migrate data from off-cloud to buckets.
>
>- Database: Prepare the DRS to migrate the database and test the connection between the cloud and the cloud.
>
>- What are the possible migration risks in the third step and fourth step of service switchover? What are the countermeasures?
