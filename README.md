![Logo](https://i.imgur.com/PyKLAe7.png)

[![License](https://img.shields.io/badge/license-The_Unlicense-red.svg)](https://unlicense.org/)

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
apt -qq install iptables ipset
ipset -q flush ipsum
ipset -q create ipsum hash:net
for ip in $(curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1); do ipset add ipsum $ip; done
iptables -I INPUT -m set --match-set ipsum src -j DROP
```

In directory [levels](levels) you can find preprocessed raw IP lists based on number of blacklist occurrences (e.g. [levels/3.txt](levels/3.txt) holds IP addresses that can be found on 3 or more blacklists).

Wall of Shame (2021-02-17)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
171.25.193.77|tor-exit1-readme.dfri.se|10
171.25.193.78|tor-exit4-readme.dfri.se|10
171.25.193.20|tor-exit0-readme.dfri.se|10
62.210.105.116|62-210-105-116.rev.poneytelecom.eu|9
185.220.102.244|185-220-102-244.torservers.net|9
192.42.116.13|this-is-a-tor-exit-node-hviv113.hviv.nl|9
51.77.135.89|ns31066279.ip-51-77-135.eu|9
185.165.168.229|-|9
185.220.102.8|185-220-102-8.torservers.net|9
162.247.72.199|jaffer.tor-exit.calyxinstitute.org|9
185.220.101.207|-|9
80.67.172.162|algrothendieck.nos-oignons.net|9
23.129.64.223|-|8
185.213.155.169|-|8
185.220.102.245|185-220-102-245.torservers.net|8
185.220.102.247|185-220-102-247.torservers.net|8
185.220.102.241|185-220-102-241.torservers.net|8
185.220.102.243|185-220-102-243.torservers.net|8
185.220.102.248|tor-exit-relay-2.anonymizing-proxy.digitalcourage.de|8
185.220.102.249|tor-exit-relay-3.anonymizing-proxy.digitalcourage.de|8
162.247.74.74|wiebe.tor-exit.calyxinstitute.org|8
217.182.192.217|ns3073700.ip-217-182-192.eu|8
178.20.55.18|marcuse-2.nos-oignons.net|8
217.170.205.14|tor-exit-5014.nortor.no|8
192.42.116.16|tor-exit.hartvoorinternetvrijheid.nl|8
192.42.116.19|this-is-a-tor-exit-node-hviv119.hviv.nl|8
185.220.101.215|-|8
144.168.164.26|-|8
178.165.72.177|178-165-72-177-kh.maxnet.ua|8
23.129.64.227|-|8
62.102.148.68|-|8
185.220.102.246|185-220-102-246.torservers.net|8
185.220.101.15|-|8
192.42.116.20|this-is-a-tor-exit-node-hviv120.hviv.nl|8
192.42.116.24|this-is-a-tor-exit-node-hviv124.hviv.nl|8
185.191.124.151|-|8
89.234.157.254|marylou.nos-oignons.net|8
91.192.103.11|-|8
185.174.43.9|-|8
185.220.101.8|-|8
185.220.102.4|communityexit.torservers.net|8
185.220.103.7|anatkamm.tor-exit.calyxinstitute.org|8
107.189.10.246|-|8
171.25.193.25|tor-exit5-readme.dfri.se|8
185.220.102.253|tor-exit-relay-7.anonymizing-proxy.digitalcourage.de|8
185.220.102.251|tor-exit-relay-5.anonymizing-proxy.digitalcourage.de|8
185.220.101.194|-|8
95.128.43.164|exit-1.fr.tor.aquaray.com|8
185.220.101.146|-|8
185.220.102.250|tor-exit-relay-4.anonymizing-proxy.digitalcourage.de|8
185.220.101.205|-|8
185.220.101.204|-|8
198.98.49.134|-|7
185.220.102.240|185-220-102-240.torservers.net|7
185.220.102.242|185-220-102-242.torservers.net|7
54.39.50.28|ns558474.ip-54-39-50.net|7
200.119.112.204|static-200-119-112-204.static.etb.net.co|7
23.129.64.232|-|7
91.192.103.34|-|7
91.192.103.35|-|7
54.39.16.73|ns555166.ip-54-39-16.net|7
45.154.255.147|cust-147.keff.org|7
178.20.55.16|marcuse-1.nos-oignons.net|7
209.127.17.242|-|7
185.220.100.253|tor-exit-2.zbau.f3netze.de|7
46.59.65.88|h-65-88.A785.priv.bahnhof.se|7
91.192.103.25|-|7
192.42.116.17|this-is-a-tor-exit-node-hviv117.hviv.nl|7
192.42.116.14|this-is-a-tor-exit-node-hviv114.hviv.nl|7
192.42.116.15|this-is-a-tor-exit-node-hviv115.hviv.nl|7
192.42.116.18|this-is-a-tor-exit-node-hviv118.hviv.nl|7
195.254.135.76|-|7
104.244.73.13|LuxembourgTorExit1|7
193.218.118.135|135.118.218.193.urdn.com.ua|7
46.101.143.148|-|7
185.220.101.218|-|7
185.220.101.216|-|7
185.220.101.213|-|7
185.220.101.133|-|7
141.98.80.69|-|7
162.247.74.27|turing.tor-exit.calyxinstitute.org|7
162.247.74.217|perry.fellwock.tor-exit.calyxinstitute.org|7
207.244.70.35|-|7
161.35.40.167|-|7
162.247.74.7|korematsu.tor-exit.calyxinstitute.org|7
45.148.10.54|edc75.howacc.pro|7
23.129.64.224|-|7
51.75.144.43|ns3129517.ip-51-75-144.eu|7
193.169.255.236|-|7
185.56.80.65|onion.xor.sc|7
167.99.217.61|-|7
78.36.197.146|146-197-36-78.baltnet.ru|7
144.217.60.239|ip239.ip-144-217-60.net|7
185.220.101.212|-|7
62.102.148.69|-|7
185.220.100.247|tor-exit-8.zbau.f3netze.de|7
192.42.116.23|this-is-a-tor-exit-node-hviv123.hviv.nl|7
192.42.116.27|this-is-a-tor-exit-node-hviv127.hviv.nl|7
192.42.116.26|this-is-a-tor-exit-node-hviv126.hviv.nl|7
192.42.116.25|this-is-a-tor-exit-node-hviv125.hviv.nl|7
192.42.116.28|this-is-a-tor-exit-node-hviv128.hviv.nl|7
104.244.79.196|LuxembourgTor11.lu|7
68.183.4.205|-|7
23.129.64.235|-|7
107.189.10.251|-|7
217.170.206.146|-|7
195.206.105.217|zrh-exit.privateinternetaccess.com|7
167.71.96.148|-|7
119.45.234.112|-|7
91.192.103.16|-|7
185.247.224.66|-|7
185.220.102.7|185-220-102-7.torservers.net|7
188.166.2.155|-|7
195.54.160.250|-|7
162.247.74.201|kunstler.tor-exit.calyxinstitute.org|7
162.247.74.200|kiriakou.tor-exit.calyxinstitute.org|7
162.247.74.206|rosaluxemburg.tor-exit.calyxinstitute.org|7
5.196.29.8|exit-node.kagaminesama.xyz|7
185.117.215.9|tor3.digineo.de|7
151.80.41.64|ns398062.ip-151-80-41.eu|7
91.250.242.12|-|7
116.196.69.144|-|7
185.191.124.153|-|7
185.191.124.152|-|7
185.191.124.150|-|7
185.174.43.4|-|7
185.174.43.6|-|7
185.174.43.3|-|7
185.174.43.2|-|7
185.220.101.9|-|7
185.220.101.1|-|7
23.129.64.213|-|7
62.210.37.82|62-210-37-82.rev.poneytelecom.eu|7
185.220.101.22|-|7
185.220.102.6|185-220-102-6.torservers.net|7
198.144.121.93|-|7
31.42.177.43|dedicated.sollutium.com|7
77.247.181.165|politkovskaja.torservers.net|7
77.247.181.163|lumumba.torservers.net|7
104.244.74.28|tor-exit.a9.wtf|7
185.220.103.8|mariellefranco.tor-exit.calyxinstitute.org|7
185.220.103.5|chelseamanning.tor-exit.calyxinstitute.org|7
45.93.201.193|-|7
176.10.99.200|accessnow.org|7
198.144.120.177|-|7
185.191.124.143|-|7
185.220.102.254|tor-exit-relay-8.anonymizing-proxy.digitalcourage.de|7
185.220.102.252|tor-exit-relay-6.anonymizing-proxy.digitalcourage.de|7
64.113.32.29|tor.t-3.net|7
46.101.220.225|-|7
23.129.64.202|-|7
23.129.64.200|-|7
23.129.64.207|-|7
23.129.64.204|-|7
91.192.103.26|-|7
45.129.56.200|-|7
188.127.251.245|ip-245-251-127-188.chaouen.co.uk|7
185.220.101.199|-|7
185.220.101.198|-|7
185.32.222.171|-|7
185.32.222.172|-|7
193.239.232.101|-|7
158.69.63.54|torex2.fissionrelays.net|7
51.79.69.241|vps-16fb7987.vps.ovh.ca|7
104.244.72.36|LuxembourgTor10.lu|7
162.247.73.192|-|7
206.189.101.245|-|7
185.220.101.208|-|7
185.220.101.203|-|7
185.220.101.201|-|7
185.220.101.200|-|7
115.135.154.232|-|7
185.100.87.207|freki.enn.lu|7
