## **Challenge 1 - Gain Access to a Remote**

After installing the VM on machine, I started on with 
```Step 1 > Information Gathering```
![ipaddr](https://github.com/user-attachments/assets/587f0da2-ec17-44b5-9020-b137ad3593dc)

Being a guest user, had limited access to overall system. did not have access to commands like curl+ using of nmap, sqlmap had no chance.
tried finding open ports using ```ss -tunl``` tried running mysql which is past my access. then found the version of kernel running to exploit any vulnerabilites.

Having the kernel version, did find listed vulnerabilities on exploit-db.com and apache itself.

![vuln](https://github.com/user-attachments/assets/9f7057b1-5b77-4e0f-a03e-40c70a388b84)

with finding vuln, started running exploits on files like pt_chown, which did fail.
![pt_chown-vuln](https://github.com/user-attachments/assets/1b898ac7-936f-4d7f-911c-677029d61572)

![Screenshot 2025-01-28 112557](https://github.com/user-attachments/assets/4ca05170-8e8e-4eb4-8fee-20c97e6a07b3))

with losing all hope on finding vulnerabilities, i surfed through the code files which we're not accessible from the browser like 'admin.php' which redirected to / if role wasn't admin.

![admin php](https://github.com/user-attachments/assets/c3502b4a-e57c-420b-889f-40657cf4d74a)

Checked ebery folder and file, but only had read access. tried injecting a php exploit which did fail.![exploit_run](https://github.com/user-attachments/assets/0e6a70ac-5696-491f-aae1-1b908d252809)

did find this ```seed.sql``` which am sure isn't the database but a one-time run sql file. realised that the password was hashed using ```md5 ENCRYPTION```. so dropped on decoding it.
![image](https://github.com/user-attachments/assets/2aab3972-7ef9-4483-aa00-6a7b8626d2ca)

THEN STARTED on running SQL Injection:
![image](https://github.com/user-attachments/assets/ffa76ba4-fc13-4505-bfe6-4ff86c64c367)

which did end up on giving nothing.
tried gaining root access in other means which also failed.

