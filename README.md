![Logo](https://i.imgur.com/PyKLAe7.png)

[![License](https://img.shields.io/badge/license-Public_domain-red.svg)](https://wiki.creativecommons.org/wiki/Public_domain)

About
----

**IPsum** is a threat intelligence feed based on 30+ different publicly available [lists](https://github.com/stamparm/maltrail) of suspicious and/or malicious IP addresses. All lists are automatically retrieved and parsed on a daily (24h) basis and the final result is pushed to this repository. List is made of IP addresses together with a total number of (black)list occurrence (for each). Greater the number, lesser the chance of false positive detection and/or dropping in (inbound) monitored traffic. Also, list is sorted from most (problematic) to least occurent IP addresses.

As an example, to get a fresh and ready-to-deploy auto-ban list of "bad IPs" that appear on at least 3 (black)lists you can run:

```
curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1
```

If you want to try it with `ipset`, you can do the following:

```
sudo su
apt-get -qq install iptables ipset
ipset -q flush ipsum
ipset -q create ipsum hash:net
for ip in $(curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1); do ipset add ipsum $ip; done
iptables -I INPUT -m set --match-set ipsum src -j DROP
```

In directory [levels](levels) you can find preprocessed raw IP lists based on number of blacklist occurrences (e.g. [levels/3.txt](levels/3.txt) holds IP addresses that can be found on 3 or more blacklists).

**Important:** If you are planning to use `git` to get the content of this repository do it like `git clone --depth 1 https://github.com/stamparm/ipsum.git`

Wall of shame (2018-11-27)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
178.73.215.171|178-73-215-171-static.glesys.net|10
171.25.193.25|tor-exit5-readme.dfri.se|10
117.36.157.226|-|10
119.97.170.34|34.170.97.119.broad.wh.hb.dynamic.163data.com.cn|9
222.184.72.66|-|9
171.25.193.20|tor-exit0-readme.dfri.se|9
116.31.116.2|-|9
5.188.10.76|-|9
80.67.172.162|algrothendieck.nos-oignons.net|9
171.25.193.78|tor-exit4-readme.dfri.se|9
80.82.77.139|dojo.census.shodan.io|9
111.7.177.239|-|9
219.135.194.73|73.194.135.219.broad.gz.gd.dynamic.163data.com.cn|9
185.220.101.28|-|9
185.244.25.152|AWS-Panel|9
211.226.176.47|-|9
104.131.146.73|-|9
66.70.217.179|tor.cusse.org|9
51.255.202.66|tor1.asmer.com.ua|9
111.74.239.115|-|9
122.2.223.242|122.2.223.242.static.pldt.net|9
80.82.77.33|sky.census.shodan.io|8
209.141.53.94|earth.rickparrish.ca|8
93.174.95.106|battery.census.shodan.io|8
51.254.47.198|ns3016508.ip-51-254-47.eu|8
199.19.226.226|-|8
91.236.116.214|-|8
195.154.53.30|195-154-53-30.rev.poneytelecom.eu|8
89.234.157.254|marylou.nos-oignons.net|8
171.25.193.235|tor-exit3-readme.dfri.se|8
197.231.221.211|exit1.ipredator.se|8
31.185.104.19|-|8
65.19.167.131|-|8
193.171.202.150|-|8
128.199.140.214|exchangercoin.com|8
54.36.189.105|105.ip-54-36-189.eu|8
209.141.50.57|voxility-filtered|8
94.177.190.19|host19-190-177-94.serverdedicati.aruba.it|8
35.0.127.52|tor-exit.eecs.umich.edu|8
185.100.84.82|-|8
209.141.33.72|-|8
64.113.32.29|tor.t-3.net|8
178.33.169.152|mobicite.dnsroute.fr|8
171.25.193.77|tor-exit1-readme.dfri.se|8
89.31.57.5|dreamatorium.badexample.net|8
199.87.154.255|tor.les.net|8
216.218.222.14|-|8
45.119.83.195|-|8
125.64.94.200|-|8
212.21.66.6|tor-exit-4.all.de|8
185.220.101.46|-|8
205.185.120.192|-|8
209.141.62.36|mx26.yongqianggd.com|8
69.60.21.172|staging.codeandtheory.com|8
192.160.102.166|chaucer.relay.coldhak.com|8
192.160.102.164|snowfall.relay.coldhak.com|8
192.160.102.169|manipogo.relay.coldhak.com|8
178.17.170.194|178-17-170-194.static.as43289.net|8
192.160.102.170|ogopogo.relay.coldhak.com|8
185.220.101.27|-|8
185.220.101.33|-|8
198.96.155.3|exit.tor.uwaterloo.ca|8
209.141.51.29|-|8
185.165.168.229|-|8
186.207.162.26|bacfa21a.virtua.com.br|8
119.192.239.192|-|8
209.141.49.123|-|8
62.210.105.116|62-210-105-116.rev.poneytelecom.eu|8
221.7.13.54|-|8
5.101.40.81|-|8
37.187.129.166|ns316491.ip-37-187-129.eu|8
115.248.207.78|-|8
5.196.1.129|tor.thd.ninja|8
198.98.53.194|clientvps.com|8
37.187.94.86|ns3035851.ip-37-187-94.eu|8
117.21.173.189|-|8
