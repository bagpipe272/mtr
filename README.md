# mtr.py，使用mtr测试网络质量

一个Python程序，使用mtr来测试、记录网络丢包、延时，并且进行分析。

原理是，每隔60秒记录每个主机的mtr报告，也就是每个主机的丢包、延时以及途径的路由器的丢包和延时。

这个程序原来是自用的，用来测试江苏到各省的网络情况，现在公开出来。

## 安装说明

    git clone https://github.com/pubyun/mtr.git
    yum -y install mtr tmux
    setcap cap_net_raw+ep /usr/sbin/mtr
    getcap /usr/sbin/mtr

## 使用方法

### 监测主机

修改 hosts.txt 文件。注意IP地址和说明之间要用空格分开。

### 监测记录

    python mtr.py

### 分析日志

#### 生成网络丢包的报告

    python mtr.py log > report.txt

这个报告，将所有主机的丢包记录帅选出来，形成报告。

#### 对检测主机的丢包情况排序

    grep timeout report.txt |sort -n -k 4

将主机按照丢包情况，进行排序。

## 一些记录

### 2016.5.16 江苏到各省的情况

丢包严重的省份：
广州、江西、沈阳、山东、湖南、云南

人口少的省份:
海口、兰州、贵州、西宁、太原

    112.67.252.202 - 海口电信: 0 timeout
    115.236.73.179 - 杭州电信: 0 timeout
    117.34.17.60 - 西安电信: 0 timeout
    1.192.125.180 - 郑州电信: 0 timeout
    123.58.191.105 - 杭州网易: 0 timeout
    125.64.34.155 - 四川成都电信: 0 timeout
    219.148.38.26 - 石家庄电信: 0 timeout
    219.153.15.15 - 重庆电信: 0 timeout
    220.162.247.170 - 福州电信: 0 timeout
    223.220.250.110 - 西宁电信: 0 timeout
    59.46.13.57 - 沈阳电信: 0 timeout
    59.49.46.141 - 太原电信: 0 timeout
    60.190.249.9 - 杭州电信: 0 timeout
    60.191.221.23 - 温州电信: 0 timeout
    115.182.105.140 - 北京电信通: 1 timeout
    119.97.137.62 - 湖北武汉电信: 1 timeout
    125.77.22.251 - 福州电信: 1 timeout
    202.100.85.45 - 兰州电信: 1 timeout
    219.142.106.139 - 北京电信: 1 timeout
    36.49.31.162 - 长春电信: 1 timeout
    61.155.6.21 - 南京电信: 1 timeout
    59.63.158.181 - 江西电信: 3 timeout
    222.87.128.4 - 贵州电信: 4 timeout
    222.85.126.17 - 河南郑州电信: 5 timeout
    222.216.28.58 - 广西电信: 6 timeout
    175.6.7.12 - 湖南长沙电信: 7 timeout
    219.153.49.183 - 重庆电信: 7 timeout
    61.147.75.88 - 扬州电信: 7 timeout
    220.165.13.182 - 昆明电信: 10 timeout
    183.57.73.118 - 广州电信: 15 timeout
    113.12.80.114 - 南宁电信: 18 timeout
    219.148.7.17 - 河北石家庄电信: 25 timeout
    124.232.137.185 - 长沙电信: 26 timeout
    222.68.185.189 - 上海电信: 33 timeout
    58.56.66.58 - 济南电信: 49 timeout
    220.165.8.156 - 云南昆明电信: 91 timeout
    14.29.84.52 - 广州电信: 144 timeout
    117.41.229.242 - 南昌电信: 194 timeout
