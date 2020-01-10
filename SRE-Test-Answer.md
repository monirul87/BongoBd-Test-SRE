# Q. Certain web pages are loading slow in user’s browser for our live web application. What steps will you take to resolve the issue?

The speed of website page loads depends on various factors, such as unoptimized images, videos, high HTTP requests, bulk code and JavaScript to name a few.

Determining exactly what is happening can be a daunting task as the website slows down. To identify the root cause, I actually first check the status of the web server like CPU usage, disk usage, memory usage. Then I check the web server log to see if there are any exceptions. Another reason, if the process list is high and it is locked in the database table.

Answer: Possible steps to resolve from my point of view considering the AWS platform: 

1.	We may use CloudFront to deliver dynamic content to the Website. This will reduce the load on our server and reduce the load time for our end users.
2.	With Load Balancer: We can distribute load among available web instance & With Auto Scaling: We can launch new instance if the page not load within the set request time period
3.	Immediate action needs to be taken on the basis of web log analysis.


# Q. Imagine a scenario where a web application is serving from a single web server to the internet. What are the problems in this scenario? Design and architect a solution that will mitigate these problems? Or How would you design a scalable architecture with resiliency in mind for the following situations:

# a. if a service is resource intensive
# b. a service needs to be low latency
# c. if parts of a service need to be restricted to certain geographical boundaries

Answer: In that case service will be down if web server down. 
Please find the secure, scalable & resilient web architecture on AWS platform:

![alt tag](https://github.com/monirul87/BongoBd-Test-SRE/blob/master/Secure-scalable-resilient-architecture.png)

Now, let’s assume our website has been extremely successful and that due to the increase in traffic, the volume of reads to the database is becoming a problem. In this case, there are three approaches we can use:

Scaling up: this means running db servers on larger, more powerful EC2 instances. 
This approach requires no changes to our application. However there is a limit to how big instances can be and much network throughput each instance can handle. We can use this approach as a quick fix, while we come up with a more long-term solution.

Scaling out: this means adding read replicas to our databases. Even though RDS synchronously replicates our database to secondary instances in different AZs, our application cannot connect directly to any of these replicas. If we want to offload the read operations of the primary db, we need to tell RDS to create specialized read replicas.

Caching db results: we can use an in-memory data store for caching db queries. Amazon Elasticache supports Memcached and Redis, and it’s the ideal solution for this use case.

Summary:
Let’s go over the features of design that contribute to the overall resiliency and availability of website:

Web servers: we have multiple EC2 instances running on multiple AZs. They are also part of an autoscaling group, which will ensure that  always have a minimum preset of servers running.

Database: the database EC2 instances are also running on multiple AZs. If the primary server goes down, RDS will automatically switch-over to a secondary replica.

Caching: the website is being served via CloudFront, which will reduce the load on web and database servers

Failover DNS routing: Route53 will also monitor main website. In case it goes down, users will be redirected to an alternative static version of the site

Caching db queries: this not only reduces request times for our users, but it also protects database in case of sudden spikes in traffic

# Q. Currently there’s no monitoring in place for the above single web server. How and what application will you use to monitor the resources/process in your new design?

Answer: Amazon CloudWatch for AWS instance but I can also use zabbix or nagios for the server monitoring. Server side configuration required for those applications. 

----
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
2.	Via an intermediate host where private IP is reachable from that real server 


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

