# PAM
### Заблокировать вход по выходным всем кроме `admin'ов`  
конкретный случай вход по `ssh`
1) проверить аутентификацию `ssh` по паролю в файле `/etc/ssh/sshd_config`  
`PasswordAuthentication yes`
2) прописать в `/etc/security/time.conf`  
`*;*;!admin1|admin2;!Wd0000-2400`   
  расшифровка   
  service-`*`;tty-`*`;`!`-все кроме `admin1|`- или `admin2`;все дни кроме выходных по времени-`!Wd0000-2400`
3) чтобы расписание сработало прописать модули в `/etc/pam.d/sshd`   
`account required pam_nologin.so`    
`account required pam_time.so`
