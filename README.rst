Postgresql Backup Scripts
------------------------------
This buildout is based on https://wiki.postgresql.org/wiki/Automated_Backup_on_Linux
Altered slightly.

MUST be run as the postgres user to work properly now.

place the scripts in the /usr/local/sbin/ directory
make them executeable

INSTALL
-----------
Run all the following as the postgres user
::

    sudo su - postgres
    git clone collective.postgresql_backup_scripts
    virtualenv venv
    . venv/bin/activate
    wget https://bootstrap.pypa.io/bootstrap-buildout.py -O bootstrap.py
    python bootstrap.py
    bin/buildout

Edit `pg_backup.config`
And set the BACKUP_DIR location, make sure the location is writeable by the postgres user

The script installs a cronjob, you may want to customize the time it runs by editing
the  [backups] and [backuprotates] sections of the buildout.cfg. Remember to re-run buildout if you make changes

USAGE
----------
If you want to manually run a backup use the command::

  bin/pg_backup

A rotate can be done using::

  bin/pg_backup_rotated
