## Install and configure infrastructure with Ansible

    ansible-playbook infra.yaml

## Restore MySQL data from the backup

Run on the DB server (anto-oshka-2 in this case) as root

    sudo -u backup duplicity --no-encryption restore rsync://anto-oshka@backup.arcticoak.io//home/anto-oshka/mysql/ /home/backup/restore/
    mysql agama < /home/backup/restore/agama.sql

You might get an error after executing the first command, just don't pay attention, backup will be restored anyways.

Example of error:
    Error '[Errno 1] Operation not permitted: b'/home/backup/restore'' processing .


## Restore InfluxDB data from the backup

Run on the logging server (anto-oshka-1 in this case) as root

    sudo -u backup duplicity --no-encryption restore rsync://anto-oshka@backup.arcticoak.io//home/anto-oshka/influxdb/ /home/backup/restore
    service telegraf stop
    influx -execute 'DROP DATABASE telegraf'
    influxd restore -portable -database telegraf /home/backup/restore

After that run ansible-playbook one more time.
