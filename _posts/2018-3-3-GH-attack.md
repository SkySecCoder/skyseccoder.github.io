--- 

layout: post 

title: GitHub survives the biggest DDoS attack ever

description: Attacks 

image: assets/images/pic24.jpg 

--- 

On Feb 28th, GitHub was a victim to one the largest DDoS amplification attack ever recorded. This attack was so great that it was able to take a company like GitHub offline for approximately 10 minutes during which it was completely offline between 17:21 and 17:26 UTC, and had intermittent connectivity between 17:26 and 17:30 UTC [1].
<br  /><br  />The company servers were barraged with 1.35 terabits per second of traffic, but thankfully GitHub contacted Akamain Prolexic in time which took over as an intermediary, and routed all ingress and egress traffic through it’s scrubbing centres to block malicious traffic. [2] Below we can see the network traffic when the attack was taking place. The sudden spike in network traffic is extremely remarkable and scary at the same time.
<p style="text-align:center;"><img src="https://skyseccoder.github.io/assets/images/postAssets/sc1.png" style="width:500px;height:250px;" align="middle"></p>
So how did a company like GitHub get attacked by such an amplification attack. Let us first define a few things before we proceed any further.
<br  /><br  /><b>What is a DDoS attack?</b><br  /><br  />
A Distributed Denial of Service (DDoS) attack is an attack that can bring a website/server/service offline by flooding the victim with traffic from multiple sources. This can be done by using several infected system, who generate traffic to the victim website/server/service, or simply be legitimate traffic that the victim is not prepared to handle. [4]
<br  /><br  /><b>What is Memcached?</b><br  /><br  />
Memcached is basically a free, open source, high-performance, distributed memory object caching system that can be used to speed up dynamic web applications. Dynamic database-driven websites usually generate small chunks of string data due to database calls, API calls or page rendering. Memcache caches these data and objects to RAM in order to reduce the number of times an external data source must be read.[3]
<br  /><br  />In order to carry out the attack, the attacker first implanted a large payload on an exposed memcached server. Then the attacker spoofed his/her IP address, with the victim’s IP address, and generated several “get” request message. Below we can see exactly how the attack was conducted. The servers are sending the request response to the victim because the attacker has spoofed his/her IP so that it appears that the victim had requested a response.[5]
<p style="text-align:center;"><img src="https://skyseccoder.github.io/images/postAssets/sc2.png" style="width:500px;height:250px;" align="middle"></p>
 The protocol being used was UDP which coupled with Memcached can provide the best protocols to use for an amplification attack. There are no checks (cause of UDP), the data will be delivered to the victim extremely quickly and a tiny request can generate a huge response as can be seen below.[5]
<pre><code>
$ sudo tcpdump -ni eth0 port 11211 -t
<br  />IP 172.16.170.135.39396 > 192.168.2.1.11211: UDP, length 15
<br  />IP 192.168.2.1.11211 > 172.16.170.135.39396: UDP, length 1400
<br  />IP 192.168.2.1.11211 > 172.16.170.135.39396: UDP, length 1400
<br  />...(repeated hundreds times)...
</code></pre>
<b>How to Fix this?</b><br  /><br  />
If your servers are using Memcached then you should make sure that you have disabled UDP support. By default memcached listens on INADDR_ANY and the UDP support is ENABLED. You can check if your server is vulnerable if you run the command below and you receive non-empty responses, as seen below.
<pre><code>
$ echo -en "\x00\x00\x00\x00\x00\x01\x00\x00stats\r\n" | nc -q1 -u 127.0.0.1 11211
STAT pid 21357
STAT uptime 41557034
STAT time 1519734962
...
</code></pre>

<br  /><b>Reference</b>
<br  />[1] Jon Russell. "The world’s largest DDoS attack took GitHub offline for fewer than 10 minutes";retrieved from https://techcrunch.com/2018/03/02/the-worlds-largest-ddos-attack-took-github-offline-for-less-than-tens-minutes/
<br  />[2] Lily Hay Newman. "GITHUB SURVIVED THE BIGGEST DDOS ATTACK EVER RECORDED"; retrieved from https://www.wired.com/story/github-ddos-memcached/
<br  />[3] What is Memcached; retrieved from https://www.memcached.org
<br  />[4] Digital Attack Map. "Digital Attack Map”; retrieved from https://www.digitalattackmap.com/understanding-ddos/
<br  />[5] Marek Majkowski. "Memcrashed - Major amplification attacks from UDP port 11211";retrieved from https://blog.cloudflare.com/memcrashed-major-amplification-attacks-from-port-11211/