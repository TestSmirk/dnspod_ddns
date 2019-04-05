

* 下载
       * 
       
       `wget https://raw.githubusercontent.com/TestSmirk/dnspod_ddns/master/dnspod.conf --no-check-certificate`
       
       `wget https://raw.githubusercontent.com/TestSmirk/dnspod_ddns/master/dnspod.sh --no-check-certificate`
       
       * 或者
       
       `git clone https://github.com/TestSmirk/dnspod_ddns.git`
       
* 编辑`dnspod.conf`
  TOKEN和ID在[dnspod](https://www.dnspod.cn/console/user/security)获取
  
  ![console](https://github.com/TestSmirk/dnspod_ddns/blob/master/images/console.png)
  `vim dnspod.conf` 
  ```
  TOKEN=""
  ID=""
  DOMAIN="sub.yourdoamin.org"
  RECORD_LINE="默认"
  ```
* 运行测试
  没有权限的话`chomd +x dnspod.sh`
  * 脚本需要curl支持 
    * CentOS `yum install curl` 
    * Ubuntu `apt install curl`
    * OpenWrt `opkg install curl`
  `./dnspod.sh dnspod.conf`
  
* 加入定时任务
  ```
  /etc/init.d/cron enable
  crontab -e
  ```
  Insert
  
  `*/3 * * * * /root/ddns/dnspod.sh /root/ddns/dnspod.conf >> /root/ddns/dnspod.log`
  
  `:wq`
