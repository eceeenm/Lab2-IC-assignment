# Lab 2: Answers

Name: ECE NUR MUSLU
Student ID: 20241701083

> For each question write **the command you used** and **its output**.
> Use code blocks like this:
>
> ```
> $ pwd
> /home/student/lab2/techcorp
> ```

## Part A: Navigation and inspection

**A1.**

```
$ pwd
/home/codespace/lab2/techcorp
```

**A2.**

```
$ mkdir -p projects/2026/{alpha,beta,gamma}
$ ls projects/2026
alpha  beta  gamma
```

**A3.**

```
$ touch projects/2026/alpha/README.md
ls -l projects/2026/alpha/README.md
-rw-r--r-- 1 codespace codespace 0 Oct 20 08:12 projects/2026/alpha/README.md
```

**A4.**

```
$ cp -r hr/policies projects/2026/beta/
ls -l projects/2026/beta/policies
total 8
-rw-r--r-- 1 codespace codespace 13 Oct 20 08:13 leave.txt
-rw-r--r-- 1 codespace codespace 14 Oct 20 08:13 remote.txt
```

**A5.**

```
$ mv projects/2026/gamma projects/2026/delta
ls projects/2026
alpha  beta  delta
```

**A6.**

```
$ cd shared
ln -s ../engineering/docs/api.md api_link
ls -l api_link
cd ..
lrwxrwxrwx 1 codespace codespace 26 Oct 20 08:19 api_link -> ../engineering/docs/api.md
```

**A7.**

```
$ cat shared/api_link
api reference
A link is not the target file itself, but rather a small file that points to its path. When read, the operation is automatically directed to the target, so the content is identical to that of api.md.
```

## Part B: Creating and organising

**B1.**

```
$ whoami
id
codespace
uid=1000(codespace) gid=1000(codespace) groups=1000(codespace),986(pipx),987(python),988(oryx),989(golang),990(docker),991(sdkman),992(ruby),993(php),994(conda),995(nvm),996(hugo),1001(ssh)
```

**B2.**

```
$ sudo groupadd engineering
sudo groupadd finance
```

**B3.**

```
$ sudo useradd -m alice
sudo useradd -m bob
ls -d /home/alice /home/bob
/home/alice  /home/bob
```

**B4.**

```
$ sudo usermod -aG engineering alice
sudo usermod -aG finance bob
sudo usermod -aG finance alice
```

**B5.**

```
$ id alice
id bob
uid=1001(alice) gid=1004(alice) groups=1004(alice),1002(engineering),1003(finance)
uid=1002(bob) gid=1005(bob) groups=1005(bob),1003(finance)
```

**B6.**

```

```

## Part C — Users and groups

**C1.**

```
$ ls -l engineering/src/build.sh
./engineering/src/build.sh
-rw-r--r-- 1 codespace codespace 26 Oct 20 08:01 engineering/src/build.sh
bash: ./engineering/src/build.sh: Permission denied

Error: bash: ./engineering/src/build.sh: Permission denied
Reason: The file lacks execute (x) permission. In the output of `ls -l`, it appears as something like `-rw-r--r--`.

chmod u+x engineering/src/build.sh
ls -l engineering/src/build.sh
./engineering/src/build.sh
-rwxr--r-- 1 codespace codespace 26 Oct 20 08:01 engineering/src/build.sh
building
```

**C2.**

```
$ find . -type f -perm -o+w
./hr/records/anna.txt
./finance/invoices/inv_103.csv
find: ‘./engineering/locked/flag.txt’: Permission denied
./engineering/src/mod_7.c
```

**C3.**

```
$ find . -type f -perm -o+w -exec chmod o-w {} +
find . -type f -perm -o+w
find: ‘./engineering/locked/flag.txt’: Permission denied
find: ‘./engineering/locked/flag.txt’: Permission denied
```

**C4.**

```
$ touch shared/team.txt
sudo chgrp engineering shared/team.txt
ls -l shared/team.txt
-rw-r--r-- 1 codespace engineering 0 Oct 20 08:30 shared/team.txt
```
