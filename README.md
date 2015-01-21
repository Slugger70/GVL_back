# GVL_back
A shell script to add to cron to backup a GVL image.

At this stage it only backs up a postgres database to a file and copies it to the object store on a rotational basis

## At the moment the following variables in the shell script need to be edited to suit the machine and NeCTAR tenancy.


## The backup directory , DO NOT END THE DIRECTORY WITH BACKSLASH! Set this variable to the location where you want the local copies of the backups to go.
BACKUP_DIR=<path to backup directory>

e.g. BACKUP_DIR=/mnt/galaxy/export


##SWIFT Stuff! Swift is the client used to access the NeCTAR cloud object store.

SWIFT_AUTH='<path to open-rc.sh file for your tenancy>'

Note: You must add your user details including API password to this file.

SWIFT_TARGET_DIR='The name of the object store directory'


##PSQL Stuff

PSQL_USER='postgres'
PSQL_DB='<database name>' - the name of the individual database to be backed up.


##Backup config Stuff


MONTHLY_BACKUP_DATE=1 #The day of the month to run the monthly backup on.
WEEKLY_BACKUP_DAY=6 #The day of the week to run the weekly backup. 1=Monday, 2=Tuesday etc.
MAIL="<your email address>"
RETENTION_DAY=2 #How many old daily backups to keep. (Files older than this are automatically deleted locally and remotely.)
RETENTION_WEEK=14 #How many weekly backups to keep (in days). i.e. 14 days ~= 2 weeks worth.
RETENTION_MONTH=60 #How many monthly backups to keep (in days). i.e. 60 days ~= 2 months worth.

## Other things to consider.

The script is fairly generic whereby changing the pg-dump line to include tars of sql and directories together could easily backup and entire GVL image.

TO DO:

 - Genericify everything.
 - Allow the passing of variables in to the script by commandline parameter.
 
 

