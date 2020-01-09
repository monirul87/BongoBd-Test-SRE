# Q. Certain web pages are loading slow in user’s browser for our live web application. What steps will you take to resolve the issue?

Website page load speed depends on a variety of factors such as unoptimized images, videos, a high number of HTTP requests, bulky codes, and JavaScript issues to name a few.
It can be a difficult task to figure out what exactly is causing the website to slow down. To find out the root cause, I actually check the web server status first like CPU Usage, Disk usage, Memory usage. Then I check the web server log is there any exception or not. Another cause, If the process list is high and locked it to the  database table.

Possible steps to resolve: 

1.	we can use CloudFront for delivering website’s dynamic content. This will reduce the load on our servers and reduce load times for our end-users.
2.	With Load Balancer: We can distribute load among available web instance & With Auto Scaling: We can launch new instance if the page not load within the set request time period
3.	Immediate action needs to be taken on the basis of web log analysis.
