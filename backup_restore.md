MySQL Backup Restore Process:

Step 1: Enter 'backup' user mode
sudo su - backup

Step 2: Identify the backup version to restore
duplicity collection-status rsync://Cheburara@backup.{{ startup_name }}/mysql

Step 3: Copy the SQL file using rsync
duplicity restore --no-encryption rsync Cheburara@backup.{{ startup_name }}/path/to/agama.sql /home/backup/restore/agama.sql

Step 4: Restore MySQL Data
mysql agama < /home/backup/restore/agama.sql

Step 5: Verify the Restoration
mysql -e "SELECT * FROM agama.item"



InfluxDB Restore Process:

Step 1: Enter 'backup' user mode
sudo su - backup

Step 2: Identify the backup version to restore
duplicity collection-status rsync://Cheburara@backup.{{ startup_name }}/influxdb

Step 3: Copy the Influxdb file using rsync
rsync -v Cheburara@backup.{{ startup_name }}/path/to/influxdb /home/backup/restore/influxdb

Step 4: Restore InfluxDB Data
duplicity restore --no-encryption /home/backup/restore/influxdb

Step 5: Import Restored InfluxDB Data
influxd restore -portable -db telegraf /home/backup/restore/influxdb

Step 6: Verify the InfluxDB Restoration
influx
SHOW DATABASES;


P.S. to connect to backup server use: sudo -u backup ssh Cheburara@backup.{{ startup_name }}

