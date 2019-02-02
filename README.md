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

Wall of shame (2019-02-02)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
197.231.221.211|exit1.ipredator.se|11
155.94.181.2|155.94.181.2.static.quadranet.com|11
80.82.77.33|sky.census.shodan.io|10
80.82.77.139|dojo.census.shodan.io|10
122.2.223.242|122.2.223.242.static.pldt.net|10
185.244.25.167|-|10
125.64.94.200|-|9
76.72.169.18|egh4.com|9
60.12.215.85|-|9
45.119.212.105|-|9
94.41.0.140|94.41.0.140.static.ufanet.ru|9
35.0.127.52|tor-exit.eecs.umich.edu|9
125.64.94.201|-|9
211.43.127.239|-|9
192.173.146.4|-|9
219.135.194.73|73.194.135.219.broad.gz.gd.dynamic.163data.com.cn|9
182.79.223.194|-|9
185.244.25.111|-|8
211.184.37.117|-|8
198.98.58.235|huil5.fitarmonit.club|8
91.236.116.214|-|8
58.42.228.170|-|8
5.188.160.242|-|8
185.244.25.124|-|8
111.7.177.239|-|8
119.177.58.163|-|8
178.73.215.171|178-73-215-171-static.glesys.net|8
171.25.193.20|tor-exit0-readme.dfri.se|8
176.10.104.240|tor1e1.digitale-gesellschaft.ch|8
221.210.237.5|-|8
65.19.167.131|-|8
71.229.24.115|c-71-229-24-115.hsd1.fl.comcast.net|8
183.131.3.147|-|8
139.59.43.104|primesurvey.org|8
80.82.70.118|host.group-ib.ru|8
209.141.50.166|ride.a.slut.and.make.sound.like.mooo.com|8
80.67.172.162|algrothendieck.nos-oignons.net|8
64.113.32.29|tor.t-3.net|8
42.61.24.202|-|8
171.25.193.77|tor-exit1-readme.dfri.se|8
89.31.57.5|dreamatorium.badexample.net|8
73.70.165.134|c-73-70-165-134.hsd1.ca.comcast.net|8
124.197.72.234|234.72.197.124.unknown.m1.com.sg|8
102.132.155.17|-|8
185.244.25.200|-|8
115.238.245.14|-|8
89.248.172.16|house.census.shodan.io|8
101.226.241.113|-|8
122.114.223.55|-|8
73.20.107.242|c-73-20-107-242.hsd1.ut.comcast.net|8
14.137.82.140|140.82.137.14.sta.dodo.net.au|8
199.87.154.255|tor.les.net|8
188.187.116.203|188x187x116x203.dynamic.spb.ertelecom.ru|8
121.165.33.239|-|8
166.70.207.2|this.is.a.tor.node.xmission.com|8
185.142.236.34|-|8
204.85.191.30|tor00.telenet.unc.edu|8
122.228.19.80|-|8
