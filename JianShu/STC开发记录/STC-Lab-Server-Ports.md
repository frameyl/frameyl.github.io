```
root@rune-0042e5540400:/home/admin# netstat -tl
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 *:40006                 *:*                     LISTEN
tcp        0      0 localhost:2375          *:*                     LISTEN
tcp        0      0 rune-0042e5540400:9199  *:*                     LISTEN
tcp        0      0 *:http                  *:*                     LISTEN
tcp        0      0 *:ssh                   *:*                     LISTEN
tcp        0      0 localhost:postgresql    *:*                     LISTEN
tcp6       0      0 [::]:40007              [::]:*                  LISTEN
tcp6       0      0 [::]:9100               [::]:*                  LISTEN
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN
tcp6       0      0 localhost:postgresql    [::]:*                  LISTEN
```
