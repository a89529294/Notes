1. on remote server, `cd /var/www/app`
2. `touch github.sh`, this is the script that the cron job will run
```
#! /usr/bin/bash

cd /var/www/app
git pull origin main --ff-only
```
3. `crontab -e` choose 2. vim, then paste `*/2 * * * * sh /var/www/app/github.sh 2>&1 | logger -t github.sh` at the end
4. verify the cron job is working `sudo tail -f /var/log/syslog`

## notes
- go to https://crontab.guru/ to verify cron syntax
- `*/2 * * * *` means every 2 minutes