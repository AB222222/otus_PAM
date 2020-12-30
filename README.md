# otus_PAM

Проверялось в среду заменой 5 на 2 в скрипте.

```
me@me-HP-260-G3-DM:~/otus-linux/DZ_PAM$ ssh -p 2222 test_user@localhost
The authenticity of host '[localhost]:2222 ([127.0.0.1]:2222)' can't be established.
ECDSA key fingerprint is SHA256:HEKq8XJA8Os5lGjfiCOGrXz3MfBRIUMrOOkA6B8Nd6A.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[localhost]:2222' (ECDSA) to the list of known hosts.
test_user@localhost's password: 
[test_user@localhost ~]$ exit
logout
Connection to localhost closed.
me@me-HP-260-G3-DM:~/otus-linux/DZ_PAM$ ssh -p 2222 test_user_no_wk@localhost
test_user_no_wk@localhost's password: 
Permission denied, please try again.
test_user_no_wk@localhost's password: 
```
