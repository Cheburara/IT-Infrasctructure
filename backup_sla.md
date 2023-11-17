Backup SLA (Service Level Agreement)

Database Servers (MySQL)
Backup Coverage:

    What is backed up: MySQL database named "agama"
    What is not backed up: Other databases on the MySQL server.

RPO (Recovery Point Objective):

    The goal is to have a maximum data loss of 24 hours.

Versioning and Retention:

    Full Backups: Once daily at 16:00.
    Incremental Backups: Every weekday (Monday to Saturday) at 16:00.
    Retention: Retain full backups for 7 days and incremental backups for 6 days.

Usability Checks:

    Verify the usability of backups by ensuring that the backup process completes without errors.

Restoration Criteria:

    Restore the backup if data loss exceeds 24 hours or in the event of a critical failure.

RTO (Recovery Time Objective):

    The goal is to restore the MySQL database within 4 hours of identifying the need for recovery.

InfluxDB
Backup Coverage:

    What is backed up: InfluxDB database named "telegraf."
    What is not backed up: Other databases in InfluxDB.

RPO (Recovery Point Objective):

    The goal is to have a maximum data loss of 24 hours.

Versioning and Retention:

    Full Backups: Once daily at 13:00.
    Incremental Backups: Every weekday (Monday to Saturday) at 13:00.
    Retention: Retain full backups for 7 days and incremental backups for 6 days.

Usability Checks:

    Verify the usability of backups by ensuring that the backup process completes without errors.

Restoration Criteria:

    Restore the backup if data loss exceeds 24 hours or in the event of a critical failure.

RTO (Recovery Time Objective):

    The goal is to restore the InfluxDB database within 4 hours of identifying the need for recovery.
