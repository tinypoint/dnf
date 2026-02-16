账号 adminlocal
密码 adminlocal
qq 123456
超级密码 adminlocal


步骤1
运行 docker run -d -e PUBLIC_IP=127.0.0.1 -e WEB_USER=root -e WEB_PASS=123456 -e DNF_DB_ROOT_PASSWORD=88888888 -e GM_ACCOUNT=gmuser -e GM_PASSWORD=gmpass -e CLIENT_POOL_SIZE=10 -v /data/log:/home/neople/game/log -v /data/mysql:/var/lib/mysql -v /data/data:/data -p 2000:180 -p 3000:3306/tcp -p 7600:7600/tcp -p 881:881/tcp -p 7001:7001/tcp -p 7001:7001/udp -p 30011:30011/tcp -p 31011:31011/udp -p 30052:30052/tcp -p 31052:31052/udp -p 7300:7300/tcp -p 7300:7300/udp -p 2311-2313:2311-2313/udp --cap-add=NET_ADMIN --hostname=dnf --cpus=1 --memory=1g --memory-swap=-1 --shm-size=8g --name=dnf 1995chen/dnf:centos7-2.1.9.fix1

步骤2
下载客户端并解压 链接：https://pan.baidu.com/s/10RgXFtpEhvRUm-hA98Am4A?pwd=fybn 提取码：fybn

步骤3
下载登陆器生成器 链接：https://pan.baidu.com/s/1Ea80rBlPQ4tY5P18ikucfw?pwd=bbd0 提取码：bbd0

步骤4
下载Dof7补丁下载 链接：https://pan.baidu.com/s/1rxlGfkfHTeGwzMKUNAbSlQ?pwd=ier2 提取码：ier2

步骤5
逐个解压

步骤6
打开DO补丁大合集V7.6 该文件夹中的DNF.toml文件，修改服务器地址为部署服务端时候填写PUBLIC_IP的值，并保存文件。
将该文件夹中的三个文件(DNF.toml, DNF.exe, 使用说明（必看）.txt) 复制到游戏客户端根目录中(即客户端压缩包中解压出来的游戏根目录，地下城与勇士文件夹下)

步骤7
设置统一网关
打开统一网关压缩包解压后的文件夹中的统一网关在线管理工具v6.4.exe
点击上方网关设置标签页，其中：
网关地址 为部署服务端时候填写 PUBLIC_IP 的值
网关端口 881 （设置到此处后点击连接，用于验证是否能正常连接上网关）
登陆账号 gmuser
登陆密码 gmpass
通信密钥 763WXRBW3PFTC3IXPFWH
登录器端口 7600
如上设置完成后，点击最下方 参数设置内容立刻生效 按钮
如上设置完成后，点击上方 登陆器设置 页面
服务器名称 可以随意填写
登陆器版本 20180307
线路名称 可以随意填写
游戏地址 为部署服务端时候填写 PUBLIC_IP 的值
登陆器端口 7600
网关地址 为部署服务端时候填写 PUBLIC_IP 的值 设置完成后一定要点击 增加 按钮
通信密钥 763WXRBW3PFTC3IXPFWH
最后点击 生成登陆器 按钮（可能会有卡顿，请耐心等待）


步骤8
将第三步生产的登陆器以及Config.ini文件，复制到游戏根目录中打开即可进入游戏，登陆游戏记得先去创建账号


步骤9
services:
  dnf:
    image: 1995chen/dnf:centos7-2.1.9.fix1
    container_name: dnf
    hostname: dnf
    cap_add:
      - NET_ADMIN
    environment:
      SERVER_GROUP: "3"
      SERVER_GROUP_DB: "cain"
      OPEN_CHANNEL: "11,52"
      PUBLIC_IP: "127.0.0.1"
      WEB_USER: "root"
      WEB_PASS: "123456"
      DNF_DB_ROOT_PASSWORD: "88888888"
      GM_ACCOUNT: "gmuser"
      GM_PASSWORD: "gmpass"
      CLIENT_POOL_SIZE: "1"
    volumes:
      - D:/ws/trade-agent/dnf/data/log:/home/neople/game/log
      - D:/ws/trade-agent/dnf/data/mysql:/var/lib/mysql
      - D:/ws/trade-agent/dnf/data/data:/data
    ports:
      - "2000:180"
      - "3000:3306"
      - "7600:7600"
      - "881:881"
      - "7001:7001/tcp"
      - "7001:7001/udp"
      - "30011:30011"
      - "31011:31011/udp"
      - "30052:30052"
      - "31052:31052/udp"
      - "7300:7300"
      - "2311-2313:2311-2313/udp"
    cpus: 2.0
    mem_limit: 8g
    memswap_limit: -1
    shm_size: "8g"
    restart: unless-stopped








