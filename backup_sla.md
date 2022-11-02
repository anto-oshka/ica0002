## BACKUP COVERAGE

- **MySQL** - agama database
- **InfluxDB** - telegraf datase
- **Ansible** - Git repo, history

## RPO

Since we creating backups once a day every day, RPO is around 24 hours.

## VERSIONING AND RETENTION

- **Full backup** - Every Monday @ 00:52 AM UTC (02:52 AM EET), Stored for 3 weeks
- **Incremental backup** - Every day (except Monday) @ 00:52 AM UTC (02:52 AM EET), Stored as long as related full baskup exists

## USABILITY CHECKS

Duty of a system administrator assistant to check every day @ 08:00 AM that the latest backup is usable.

## RESTORATION CRITERIA

In case of unexpected data loss or ransomware attack.

## RTO

5-6 hrs after the incident has been detected.
