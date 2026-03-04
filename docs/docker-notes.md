# Docker Notes — Day 9

## Docker Version

Client:
 Version:           29.2.1  
 API version:       1.53    
 Go version:        go1.25.6
 Git commit:        a5c7197 
 Built:             Mon Feb  2 17:20:16 2026
 OS/Arch:           windows/amd64
 Context:           desktop-linux

Server: Docker Desktop 4.63.0 (220185)
 Engine:
  Version:          29.2.1
  API version:      1.53 (minimum version 1.44)
  Go version:       go1.25.6
  Git commit:       6bc6209
  Built:            Mon Feb  2 17:17:24 2026
  OS/Arch:          linux/amd64
 containerd:
  Version:          v2.2.1
  GitCommit:        dea7da592f5d1d2b7755e3a161be07f43fad8f75
 runc:
  Version:          1.3.4
  GitCommit:        v1.3.4-0-gd6d73eb8
 docker-init:
  Version:          0.19.0
  GitCommit:        de40ad0


## Hello World Test

This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:


## Postgres Container

Command used:
```bash
docker run -d \
  --name pg-prework \
  -e POSTGRES_PASSWORD=prework \
  -p 5432:5432 \
  postgres:15-alpine






    ## docker logs pg-prework
The files belonging to this database system will be owned by user "postgres".
This user must also own the server process.

The database cluster will be initialized with locale "en_US.utf8".
The default database encoding has accordingly been set to "UTF8".
The default text search configuration will be set to "english".

Data page checksums are disabled.

fixing permissions on existing directory /var/lib/postgresql/data ... ok
creating subdirectories ... ok
selecting dynamic shared memory implementation ... posix
selecting default max_connections ... 100
selecting default shared_buffers ... 128MB
selecting default time zone ... UTC
creating configuration files ... ok
running bootstrap script ... ok
sh: locale: not found
2026-03-04 19:04:38.028 UTC [35] WARNING:  no usable system locales were found
performing post-bootstrap initialization ... ok
initdb: warning: enabling "trust" authentication for local connections
initdb: hint: You can change this by editing pg_hba.conf or using the option -A, or --auth-local and --auth-host, the next time you run initdb.
syncing data to disk ... ok


Success. You can now start the database server using:

    pg_ctl -D /var/lib/postgresql/data -l logfile start

waiting for server to start....2026-03-04 19:04:43.327 UTC [41] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 19:04:43.337 UTC [41] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-04 19:04:43.366 UTC [44] LOG:  database system was shut down at 2026-03-04 19:04:41 UTC
2026-03-04 19:04:43.381 UTC [41] LOG:  database system is ready to accept connections
 done
server started

/usr/local/bin/docker-entrypoint.sh: ignoring /docker-entrypoint-initdb.d/*

waiting for server to shut down....2026-03-04 19:04:43.447 UTC [41] LOG:  received fast shutdown request
2026-03-04 19:04:43.461 UTC [41] LOG:  aborting any active transactions
2026-03-04 19:04:43.466 UTC [41] LOG:  background worker "logical replication launcher" (PID 47) exited with exit code 
1
2026-03-04 19:04:43.475 UTC [42] LOG:  shutting down
2026-03-04 19:04:43.482 UTC [42] LOG:  checkpoint starting: shutdown immediate
2026-03-04 19:04:43.532 UTC [42] LOG:  checkpoint complete: wrote 3 buffers (0.0%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.012 s, sync=0.004 s, total=0.057 s; sync files=2, longest=0.003 s, average=0.002 s; distance=0 kB, estimate=0 kB
2026-03-04 19:04:43.542 UTC [41] LOG:  database system is shut down
 done
server stopped

PostgreSQL init process complete; ready for start up.

2026-03-04 19:04:43.603 UTC [1] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 19:04:43.604 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
2026-03-04 19:04:43.604 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2026-03-04 19:04:43.616 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-04 19:04:43.643 UTC [55] LOG:  database system was shut down at 2026-03-04 19:04:43 UTC
2026-03-04 19:04:43.658 UTC [1] LOG:  database system is ready to accept connections
2026-03-04 19:07:12.290 UTC [1] LOG:  received fast shutdown request
2026-03-04 19:07:12.300 UTC [1] LOG:  aborting any active transactions
2026-03-04 19:07:12.314 UTC [1] LOG:  background worker "logical replication launcher" (PID 58) exited with exit code 12026-03-04 19:07:12.314 UTC [53] LOG:  shutting down
2026-03-04 19:07:12.319 UTC [53] LOG:  checkpoint starting: shutdown immediate
2026-03-04 19:07:12.359 UTC [53] LOG:  checkpoint complete: wrote 21 buffers (0.1%); 0 WAL file(s) added, 0 removed, 0 
recycled; write=0.012 s, sync=0.012 s, total=0.046 s; sync files=10, longest=0.007 s, average=0.002 s; distance=36 kB, 
estimate=36 kB
2026-03-04 19:07:12.369 UTC [1] LOG:  database system is shut down

PostgreSQL Database directory appears to contain a database; Skipping initialization

2026-03-04 19:07:13.658 UTC [1] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 19:07:13.659 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
2026-03-04 19:07:13.659 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2026-03-04 19:07:13.710 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-04 19:07:13.740 UTC [30] LOG:  database system was shut down at 2026-03-04 19:07:12 UTC
2026-03-04 19:07:13.773 UTC [1] LOG:  database system is ready to accept connections
2026-03-04 19:12:13.099 UTC [28] LOG:  checkpoint starting: time
2026-03-04 19:12:13.130 UTC [28] LOG:  checkpoint complete: wrote 3 buffers (0.0%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.007 s, sync=0.004 s, total=0.032 s; sync files=2, longest=0.003 s, average=0.002 s; distance=0 kB, estimate=0 kB






[pg-prework]
[pg-prework]
[The files belonging to this database system will be owned by user "postgres".
This user must also own the server process.

The database cluster will be initialized with locale "en_US.utf8".
The default database encoding has accordingly been set to "UTF8".
The default text search configuration will be set to "english".

Data page checksums are disabled.

fixing permissions on existing directory /var/lib/postgresql/data ... ok
creating subdirectories ... ok
selecting dynamic shared memory implementation ... posix
selecting default max_connections ... 100
selecting default shared_buffers ... 128MB
selecting default time zone ... UTC
creating configuration files ... ok
running bootstrap script ... ok
sh: locale: not found
2026-03-04 19:04:38.028 UTC [35] WARNING:  no usable system locales were found
performing post-bootstrap initialization ... ok
initdb: warning: enabling "trust" authentication for local connections
initdb: hint: You can change this by editing pg_hba.conf or using the option -A, or --auth-local and --auth-host, the next time you run initdb.
syncing data to disk ... ok


Success. You can now start the database server using:

    pg_ctl -D /var/lib/postgresql/data -l logfile start

waiting for server to start....2026-03-04 19:04:43.327 UTC [41] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 19:04:43.337 UTC [41] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-04 19:04:43.366 UTC [44] LOG:  database system was shut down at 2026-03-04 19:04:41 UTC
2026-03-04 19:04:43.381 UTC [41] LOG:  database system is ready to accept connections
 done
server started

/usr/local/bin/docker-entrypoint.sh: ignoring /docker-entrypoint-initdb.d/*

waiting for server to shut down....2026-03-04 19:04:43.447 UTC [41] LOG:  received fast shutdown request
2026-03-04 19:04:43.461 UTC [41] LOG:  aborting any active transactions
2026-03-04 19:04:43.466 UTC [41] LOG:  background worker "logical replication launcher" (PID 47) exited with exit code 
1
2026-03-04 19:04:43.475 UTC [42] LOG:  shutting down
2026-03-04 19:04:43.482 UTC [42] LOG:  checkpoint starting: shutdown immediate
2026-03-04 19:04:43.532 UTC [42] LOG:  checkpoint complete: wrote 3 buffers (0.0%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.012 s, sync=0.004 s, total=0.057 s; sync files=2, longest=0.003 s, average=0.002 s; distance=0 kB, estimate=0 kB
2026-03-04 19:04:43.542 UTC [41] LOG:  database system is shut down
 done
server stopped

PostgreSQL init process complete; ready for start up.

2026-03-04 19:04:43.603 UTC [1] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 19:04:43.604 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
2026-03-04 19:04:43.604 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2026-03-04 19:04:43.616 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-04 19:04:43.643 UTC [55] LOG:  database system was shut down at 2026-03-04 19:04:43 UTC
2026-03-04 19:04:43.658 UTC [1] LOG:  database system is ready to accept connections
2026-03-04 19:07:12.290 UTC [1] LOG:  received fast shutdown request
2026-03-04 19:07:12.300 UTC [1] LOG:  aborting any active transactions
2026-03-04 19:07:12.314 UTC [1] LOG:  background worker "logical replication launcher" (PID 58) exited with exit code 12026-03-04 19:07:12.314 UTC [53] LOG:  shutting down
2026-03-04 19:07:12.319 UTC [53] LOG:  checkpoint starting: shutdown immediate
2026-03-04 19:07:12.359 UTC [53] LOG:  checkpoint complete: wrote 21 buffers (0.1%); 0 WAL file(s) added, 0 removed, 0 
recycled; write=0.012 s, sync=0.012 s, total=0.046 s; sync files=10, longest=0.007 s, average=0.002 s; distance=36 kB, 
estimate=36 kB
2026-03-04 19:07:12.369 UTC [1] LOG:  database system is shut down

PostgreSQL Database directory appears to contain a database; Skipping initialization

2026-03-04 19:07:13.658 UTC [1] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 19:07:13.659 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
2026-03-04 19:07:13.659 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2026-03-04 19:07:13.710 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-04 19:07:13.740 UTC [30] LOG:  database system was shut down at 2026-03-04 19:07:12 UTC
2026-03-04 19:07:13.773 UTC [1] LOG:  database system is ready to accept connections
2026-03-04 19:12:13.099 UTC [28] LOG:  checkpoint starting: time
2026-03-04 19:12:13.130 UTC [28] LOG:  checkpoint complete: wrote 3 buffers (0.0%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.007 s, sync=0.004 s, total=0.032 s; sync files=2, longest=0.003 s, average=0.002 s; distance=0 kB, estimate=0 kB
2026-03-04 19:15:12.754 UTC [1] LOG:  received fast shutdown request
2026-03-04 19:15:12.762 UTC [1] LOG:  aborting any active transactions
2026-03-04 19:15:12.771 UTC [1] LOG:  background worker "logical replication launcher" (PID 33) exited with exit code 12026-03-04 19:15:12.774 UTC [28] LOG:  shutting down
2026-03-04 19:15:12.779 UTC [28] LOG:  checkpoint starting: shutdown immediate
2026-03-04 19:15:12.805 UTC [28] LOG:  checkpoint complete: wrote 0 buffers (0.0%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.001 s, sync=0.001 s, total=0.031 s; sync files=0, longest=0.000 s, average=0.000 s; distance=0 kB, estimate=0 kB
2026-03-04 19:15:12.813 UTC [1] LOG:  database system is shut down

PostgreSQL Database directory appears to contain a database; Skipping initialization

2026-03-04 19:15:49.005 UTC [1] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 19:15:49.006 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
2026-03-04 19:15:49.006 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2026-03-04 19:15:49.042 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-04 19:15:49.090 UTC [29] LOG:  database system was shut down at 2026-03-04 19:15:12 UTC
2026-03-04 19:15:49.125 UTC [1] LOG:  database system is ready to accept connections
2026-03-04 19:20:49.296 UTC [27] LOG:  checkpoint starting: time
2026-03-04 19:20:49.356 UTC [27] LOG:  checkpoint complete: wrote 3 buffers (0.0%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.017 s, sync=0.006 s, total=0.061 s; sync files=2, longest=0.004 s, average=0.003 s; distance=0 kB, estimate=0 kB
2026-03-04 19:29:05.547 UTC [1] LOG:  received fast shutdown request
2026-03-04 19:29:05.558 UTC [1] LOG:  aborting any active transactions
2026-03-04 19:29:05.565 UTC [1] LOG:  background worker "logical replication launcher" (PID 32) exited with exit code 12026-03-04 19:29:05.570 UTC [27] LOG:  shutting down
2026-03-04 19:29:05.575 UTC [27] LOG:  checkpoint starting: shutdown immediate
2026-03-04 19:29:05.601 UTC [27] LOG:  checkpoint complete: wrote 0 buffers (0.0%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.001 s, sync=0.001 s, total=0.031 s; sync files=0, longest=0.000 s, average=0.000 s; distance=0 kB, estimate=0 kB
2026-03-04 19:29:05.610 UTC [1] LOG:  database system is shut down

PostgreSQL Database directory appears to contain a database; Skipping initialization

2026-03-04 19:29:16.764 UTC [1] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 19:29:16.765 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
2026-03-04 19:29:16.765 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2026-03-04 19:29:16.790 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-04 19:29:16.820 UTC [29] LOG:  database system was shut down at 2026-03-04 19:29:05 UTC
2026-03-04 19:29:16.855 UTC [1] LOG:  database system is ready to accept connections
(.venv) ]

[the terminal did not run the command:
(docker run -d \
  --name pg-prework \
  -e POSTGRES_PASSWORD=prework \
  -p 5432:5432 \
  postgres:15-alpine)
  
  and sfter that i tried to run the command in git bash and it worked]


## Restarting the Container
To apply changes or restart the database, I used the following command:
`docker restart pg-prework`