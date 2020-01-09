# Q. Certain web pages are loading slow in user’s browser for our live web application. What steps will you take to resolve the issue?

Website page load speed depends on a variety of factors such as unoptimized images, videos, a high number of HTTP requests, bulky codes, and JavaScript issues to name a few.
It can be a difficult task to figure out what exactly is causing the website to slow down. To find out the root cause, I actually check the web server status first like CPU Usage, Disk usage, Memory usage. Then I check the web server log is there any exception or not. Another cause, If the process list is high and locked it to the  database table.

Answer: Possible steps to resolve: 

1.	e can use CloudFront for delivering website’s dynamic content. This will reduce the load on our servers and reduce load times for our end-users.
2.	With Load Balancer: We can distribute load among available web instance & With Auto Scaling: We can launch new instance if the page not load within the set request time period
3.	Immediate action needs to be taken on the basis of web log analysis.


# Q. Imagine a scenario where a web application is serving from a single web server to the internet. What are the problems in this scenario? Design and architect a solution that will mitigate these problems? Or How would you design a scalable architecture with resiliency in mind for the following situations:

# a. if a service is resource intensive
# b. a service needs to be low latency
# c. if parts of a service need to be restricted to certain geographical boundaries

Answer: In that case service will be down if web server down. 
Please find the secure, scalable & resilient web architecture on AWS platform:


# Q. Currently there’s no monitoring in place for the above single web server. How and what application will you use to monitor the resources/process in your new design?

Answer: Amazon CloudWatch for AWS server & we can use zabbix or nagios for the on premises server.

---
# Q. In our server we want to create a user who can only view logs using `less` from this path /var/log. Please explain how to achieve this.

Answer:
1.	We need to create a user (Command: useradd monirul)
2.	Set password for the user monirul (Command: passwd monirul)
3.	Apply acl on /var/log for that user (Command: setfacl -m u:monirul:r-- /var/log/)
4.	Login to the server with the user monirul
5.	Check the log by using less command (Command: less -f /var/log)


# Q. Explain how you can ssh into a private server from the internet.
Answer:
Here are few options to login a private server from the internet. 
1.	By using VPN connectivity (Private server should be accessible after establishing VPN client)
2.	Via an intermediate host where private IP is reachable from that that server 


# Q. Write a bash function that will find all occurrences of an IPv4 from a given file.

monirul-bongobd-exam.sh

#!/bin/bash

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

export DISPLAY=:0.0

SRE_BONGOBD="/root/file.txt"

while IFS= read -r line

do
   ip="$(grep -oE '[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}' <<< "$line")"
   
  echo "$ip"
  
done < "$SRE_BONGOBD"



File Name: file.txt 

p3p1      Link encap:Ethernet  HWaddr 90:E2:BA:15:A7:B8  

          inet addr:202.53.169.178  Bcast:202.53.169.183  Mask:255.255.255.248
          
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          
          RX packets:357467393 errors:0 dropped:0 overruns:0 frame:0
          
          TX packets:307798115 errors:0 dropped:0 overruns:0 carrier:0
          
          collisions:0 txqueuelen:1000 
          
          RX bytes:48838056406 (45.4 GiB)  TX bytes:208213637734 (193.9 GiB)
          
          Memory:f9fa0000-f9fc0000

