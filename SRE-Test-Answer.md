# Q. Certain web pages are loading slow in user’s browser for our live web application. What steps will you take to resolve the issue?

Website page load speed depends on a variety of factors such as unoptimized images, videos, a high number of HTTP requests, bulky codes, and JavaScript issues to name a few.
It can be a difficult task to figure out what exactly is causing the website to slow down. To find out the root cause, I actually check the web server status first like CPU Usage, Disk usage, Memory usage. Then I check the web server log is there any exception or not. Another cause, If the process list is high and locked it to the  database table.

# Answer: Possible steps to resolve: 

1.	e can use CloudFront for delivering website’s dynamic content. This will reduce the load on our servers and reduce load times for our end-users.
2.	With Load Balancer: We can distribute load among available web instance & With Auto Scaling: We can launch new instance if the page not load within the set request time period
3.	Immediate action needs to be taken on the basis of web log analysis.


# Q. Imagine a scenario where a web application is serving from a single web server to the internet. What are the problems in this scenario? Design and architect a solution that will mitigate these problems? Or How would you design a scalable architecture with resiliency in mind for the following situations:

# a. if a service is resource intensive
# b. a service needs to be low latency
# c. if parts of a service need to be restricted to certain geographical boundaries

# Answer: In that case service will be down if web server down. 
Please find the secure, scalable & resilient web architecture on AWS platform:


# Q. Currently there’s no monitoring in place for the above single web server. How and what application will you use to monitor the resources/process in your new design?

# Answer: Amazon CloudWatch for AWS server & we can use zabbix or nagios for the on premises server.





