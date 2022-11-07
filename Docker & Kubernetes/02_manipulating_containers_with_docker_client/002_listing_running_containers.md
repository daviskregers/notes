# Listing running containers

You can list running containers using a command

```
docker ps
```

```
✘ davis@davis-arch  ~  docker ps
CONTAINER ID        IMAGE                          COMMAND                  CREATED             STATUS                          PORTS                     NAMES
3d2bac4adcd0        x-frontend   "sh -c /var/www/dock…"   7 days ago          Up Less than a second           80/tcp                    x-a
7ef2e25bde57        x-api        "sh -c /var/www/dock…"   7 days ago          Up Less than a second           80/tcp                    x-api_run_706c3e49d578
a39d737fc13f        x-frontend   "sh -c /var/www/dock…"   7 days ago          Up Less than a second           80/tcp                    x-frontend_run_6e04a848228d
60fd1cceaf76        redis:alpine                   "docker-entrypoint.s…"   7 days ago          Up Less than a second           0.0.0.0:6379->6379/tcp    redis
d1aafec6bbdb        jwilder/nginx-proxy            "/app/docker-entrypo…"   7 days ago          Up Less than a second           0.0.0.0:80->80/tcp        nginx-proxy
dc9f43f8754f        redis                          "docker-entrypoint.s…"   2 weeks ago         Up Less than a second           0.0.0.0:63791->6379/tcp   y_redis_1
e6615103591f        mariadb:latest                 "docker-entrypoint.s…"   3 weeks ago         Restarting (1) 57 seconds ago                             mysql
```

As we can see, currently we have 7 docker containers running.

You can also command `docker ps --all` to view a list of containers that we have started up at some time.

```
 davis@davis-arch  ~  docker ps --all
CONTAINER ID        IMAGE                          COMMAND                  CREATED             STATUS                         PORTS                     NAMES
28cade9f5e6b        hello-world                    "echo hello"             6 minutes ago       Created                                                  xenodochial_johnson
ceae74bbdb51        busybox                        "ls"                     7 minutes ago       Exited (0) 7 minutes ago                                 sad_yonath
2b7ca645d6b8        busybox                        "echo hi there"          8 minutes ago       Exited (0) 7 minutes ago                                 nervous_meitner
190cd14fbf74        hello-world                    "/hello"                 32 minutes ago      Exited (0) 31 minutes ago                                sharp_banzai
49ca4be6189a        hello-world                    "/hello"                 35 minutes ago      Exited (0) 35 minutes ago                                keen_kapitsa
3d2bac4adcd0        x-frontend   "sh -c /var/www/dock…"   7 days ago          Up Less than a second          80/tcp                    x-a
7ef2e25bde57        x-api        "sh -c /var/www/dock…"   7 days ago          Up Less than a second          80/tcp                    x-api_run_706c3e49d578
a39d737fc13f        x-frontend   "sh -c /var/www/dock…"   7 days ago          Up Less than a second          80/tcp                    x-frontend_run_6e04a848228d
60fd1cceaf76        redis:alpine                   "docker-entrypoint.s…"   7 days ago          Up Less than a second          0.0.0.0:6379->6379/tcp    redis
d1aafec6bbdb        jwilder/nginx-proxy            "/app/docker-entrypo…"   7 days ago          Up Less than a second          0.0.0.0:80->80/tcp        nginx-proxy
08147054eeaa        deacb673141f                   "/bin/sh -c 'npm ins…"   7 days ago          Exited (236) 7 days ago                                  cocky_kepler
2395ab3de097        y_web                     "nginx -g 'daemon of…"   12 days ago         Exited (0) 4 days ago                                    y_web_1
2fa3f86edaf8        y_app                     "docker-php-entrypoi…"   12 days ago         Exited (0) 4 days ago                                    y_app_1
f4dffbeae0e7        78642a9cde3f                   "/bin/sh -c 'curl -s…"   12 days ago         Exited (127) 12 days ago                                 elastic_stonebraker
6a303e43c1b7        78642a9cde3f                   "/bin/sh -c '/var/ww…"   12 days ago         Exited (126) 12 days ago                                 eager_albattani
93ea0762aa3a        a9afbaec4424                   "/bin/sh -c 'apt-get…"   12 days ago         Exited (1) 12 days ago                                   modest_noether
b793b6f25878        a9afbaec4424                   "/bin/sh -c 'apt-get…"   12 days ago         Exited (1) 12 days ago                                   suspicious_buck
f4942e7b3e01        a9afbaec4424                   "/bin/sh -c 'curl -s…"   12 days ago         Exited (1) 12 days ago                                   hardcore_brahmagupta
af4db85b936a        b46c28d848cb                   "/bin/sh -c 'cd /tmp…"   12 days ago         Exited (100) 12 days ago                                 zen_bhabha
fcb1457e7c30        e87b84d8efbc                   "/bin/sh -c 'cd /var…"   12 days ago         Exited (1) 12 days ago                                   xenodochial_chatelet
54ceb98bd98c        b46c28d848cb                   "/bin/sh -c 'cd /tmp…"   12 days ago         Exited (1) 12 days ago                                   heuristic_merkle
dc8c3b08ce48        b46c28d848cb                   "/bin/sh -c 'apt-get…"   12 days ago         Exited (100) 12 days ago                                 brave_tu
58c1f8a72006        b46c28d848cb                   "/bin/sh -c 'apt-get…"   12 days ago         Exited (100) 12 days ago                                 silly_mahavira
f63168bcbdf9        b46c28d848cb                   "/bin/sh -c 'apt-get…"   12 days ago         Exited (100) 12 days ago                                 upbeat_mcclintock
ed37a5766b29        b46c28d848cb                   "/bin/sh -c 'apt-get…"   12 days ago         Exited (100) 12 days ago                                 tender_benz
f16303633ef4        ba0874383a79                   "/bin/sh -c 'ARCH= &…"   12 days ago         Exited (127) 12 days ago                                 blissful_shaw
9c763d1b4ecf        04e56a5beebd                   "/bin/sh -c 'addgrou…"   12 days ago         Exited (1) 12 days ago                                   amazing_perlman
dc9f43f8754f        redis                          "docker-entrypoint.s…"   2 weeks ago         Up Less than a second          0.0.0.0:63791->6379/tcp   y_redis_1
e6615103591f        mariadb:latest                 "docker-entrypoint.s…"   3 weeks ago         Restarting (1) 4 seconds ago                             mysql
b0e8d001f5f6        7034018bfc7e                   "/bin/sh -c 'groupad…"   5 weeks ago         Exited (9) 5 weeks ago                                   epic_williamson
d07618584116        7034018bfc7e                   "/bin/sh -c 'groupad…"   5 weeks ago         Exited (2) 5 weeks ago                                   blissful_allen
005fd53362b2        7034018bfc7e                   "/bin/sh -c 'addgrou…"   5 weeks ago         Exited (1) 5 weeks ago                                   brave_brahmagupta
a4750034f8e0        phpmyadmin/phpmyadmin          "/run.sh supervisord…"   5 weeks ago         Exited (0) 4 days ago                                    y_pma_1
6ee3bb3c083b        mailhog/mailhog                "MailHog"                5 weeks ago         Exited (2) 4 days ago                                    y_mailhog_1
1c004de38bca        mariadb:10.3.8                 "docker-entrypoint.s…"   5 weeks ago         Exited (0) 4 days ago                                    y_database_1
01d58a13538b        b0dcecc1dacc                   "/bin/sh -c 'chown -…"   5 weeks ago         Exited (1) 5 weeks ago                                   stupefied_edison
95e6b16726e3        6ea050069ccb                   "/bin/sh -c 'npm ins…"   5 weeks ago         Exited (236) 5 weeks ago                                 objective_kalam
70fbf741a2eb        8ca6f9294c50                   "/bin/sh -c 'npm ins…"   5 weeks ago         Exited (236) 5 weeks ago                                 amazing_rubin
f649899d4a7c        c6532dc6b4d1                   "/bin/sh -c 'npm ins…"   5 weeks ago         Exited (236) 5 weeks ago                                 relaxed_pike
```