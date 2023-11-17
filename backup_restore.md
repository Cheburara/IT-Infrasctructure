MySQL Backup Restore Process
Prerequisites:

    Ensure that the necessary backup files are available.
    Have root access to the managed host.

Restore Process:

    Navigate to the Backup Directory:

    bash

cd /home/backup/mysql/

Identify the Backup Version to Restore:

    List available backup versions:

    bash

    duplicity collection-status rsync://Cheburara@backup.{{ startup_name }}/mysql

Choose the Version to Restore:

    Identify the desired backup version, typically the latest one.

Restore MySQL Data:

bash

sudo -u backup duplicity restore --no-encryption rsync://Cheburara@backup.{{ startup_name }}/mysql/<backup-version> /tmp/mysql-restore/

    Replace <backup-version> with the chosen backup version.

Import Restored Data to MySQL:

bash

mysql -u root -p agama < /tmp/mysql-restore/agama.sql

    You will be prompted for the MySQL root password.

Verify the Restoration:

    Access the MySQL command line:

    bash

mysql -u root -p

Select the database:

sql

    USE agama;

    Check if the necessary tables and data are present.

Clean Up Temporary Files:

bash

    rm -r /tmp/mysql-restore/

Result Verification:

To ensure the successful restoration of MySQL data, perform the following checks:

    Check Database Content:
        Connect to the MySQL command line and verify that the necessary tables and data exist in the "agama" database.

    Verify Recent Data:
        Check if the recently added or modified data is present in the restored database.

    Monitor MySQL Error Log:
        Examine the MySQL error log (/var/log/mysql/error.log) for any errors related to the restoration process.

    Application Testing:
        If applicable, conduct tests on the application to confirm that it functions correctly with the restored data.


InfluxDB Restore Process:

    Navigate to the InfluxDB Backup Directory:

    bash

cd /home/backup/influxdb/

Identify the InfluxDB Backup Version to Restore:

    List available backup versions:

    bash

    duplicity collection-status rsync://Cheburara@backup.{{ startup_name }}/influxdb

Choose the InfluxDB Backup Version to Restore:

    Identify the desired InfluxDB backup version, typically the latest one.

Restore InfluxDB Data:

bash

sudo -u backup duplicity restore --no-encryption rsync://Cheburara@backup.{{ startup_name }}/influxdb/<influxdb-backup-version> /tmp/influxdb-restore/

    Replace <influxdb-backup-version> with the chosen InfluxDB backup version.

Import Restored InfluxDB Data:

bash

influxd restore -portable -db telegraf /tmp/influxdb-restore/

Verify the InfluxDB Restoration:

    Access the InfluxDB command line:

    bash

influx

Check if the necessary databases and measurements are present:

sql

    SHOW DATABASES;

Clean Up Temporary InfluxDB Files:

bash

    rm -r /tmp/influxdb-restore/

Result Verification:

To ensure the successful restoration of MySQL and InfluxDB data, perform the following checks:

    Check MySQL Database Content:
        Connect to the MySQL command line and verify that the necessary tables and data exist in the "agama" database.

    Check InfluxDB Database Content:
        Connect to the InfluxDB command line and verify that the necessary databases and measurements exist.

    Verify Recent Data:
        Check if the recently added or modified data is present in both MySQL and InfluxDB.

    Monitor Logs:
        Examine the MySQL and InfluxDB logs for any errors related to the restoration process.

    Application Testing:
        If applicable, conduct tests on the respective applications to confirm that they function correctly with the restored data.
