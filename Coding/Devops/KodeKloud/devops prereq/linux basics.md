## a few basic commands

```bash
cat /etc/*release* # check os

uname -m # check architecture, x86_64 or arm64

mkdir -p /tmp/a/b/c # creates all intermediary folders

echo "hello world" > app.js

cat app.js # view content

cat > app.js # then type in what you want to add to the file, ctrl D to finish

# > for replace, >> for append

whoami # prints current user

id # prints id of current user

su new_user # switch to new_user

curl http://example.com/text.txt -O # download file

ps -ef | grep gunicorn | grep -v grep # find gunicorn processes excluding grep command itself 

pkill process_name

kill pid
```

## vim 

Starts in *normal mode*, from normal you can enter *last line* or *insert mode*. To exit out of last line or insert mode simply press `esc`

- `i` to enter  *insert mode* 
- `esc` to enter *command/normal mode*
- `:` to enter *last line mode*

### command mode

- `x` to delete one char, `dd` to delete whole line
- `yy` to copy line, `p` to paste
- `ctrl d` to move down ~ 10 lines, `ctrl u` to move up ~ 10 lines
- `:w` to save, `:q` to quit, `:wq` to save then quit
- `/of` to find instances of the word of, `n` to move to next one, `N` to move to previous one

## package managers (centos)

```bash
rpm -i telnet.rpm # install
rpm -e telnet # uninstall
rpm -q telent # query

# yum is a high level package manager that uses rpm under the hood, it takes care of dependencies
yum install ansible

/etc/yum.repos.d # add more files to this directory to add more repos for yum to search from
yum repolist # to find remote repos where yum searches for packages

yum list 
yum list ansible # to list package info

yum remove ansible

yum --showduplicates list ansible # show all versions of installed package
```

## services

```bash
systemctl start httpd
systemctl stop httpd
systemctl status httpd
systemctl enable httpd # configure httpd to start at startup
systemctl disable httpd 
```

A *service on Linux is a background process* (daemon) that provides specific functionality and can be managed by the system's init system. In modern Linux distributions, systemd is the most common init system that manages services.

### example of a custom service
Assuming you have a app.js that can be run as `node app.js`
1. go to /etc/systemd/system dir
2. create file myapp.service
```
[Unit]
Description=My node web app

[Service]
ExecStart=/usr/bin/node /path/to/your/app/app.js
ExecStartPre=configure_db.sh
ExecStartPost=email_status.sh
Restart=always

[Install]
WantedBy=multi-user.target 
```
1. `systemctl daemon-reload`
2. `systemctl start myapp`, `systemctl enable myapp`
3. `ExecStartPre` & `ExecStartPost` are optional commands you may want to run before and after `ExecStart`