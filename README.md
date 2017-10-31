# MariaDB bash backup script.

Local or remote MariaDB backup script written in bash.

This script is a wrapper arround mysqldump

## Requirements

Those package MUST be installed on your system:

* bash ( >= 4 )
* mariadb-client ( >= 10.1 )

Version not in that range MAY work but are not tested.

My home made logger: f_notify

## To Do

- [x] New feature: remote backup
- [x] New feature: configuration file
- [ ] Add github project link to f_notify (bash_common)
- [ ] Add an option to bypass usage of f_notify

## Getting started

Checkout this repository or copy mariabackup in an appropiate folder.

Ex. /usr/local/bin

It is RECOMMENDED to deploy it where your DBA can execute it.

## Usage

User SHOULD execute `mariabackup -h` to see all the available options.

Regarding remote backup, user SHOULD create a dedicated MariaDB backup user.

Here is mine:

    CREATE USER 'backup'@'backup_server' IDENTIFIED BY 'password';
    GRANT SELECT, SHOW VIEW, RELOAD, REPLICATION CLIENT, EVENT, TRIGGER ON *.* TO 'backup'@'backup_server';

## Configuration file

The configuration file MUST be in a `key=value` format (bash readable)

An example is available in this repository, in conf.d/mariabackup.conf.sample.

Feel free to use it. `cp conf.d/mariabackup.conf.sample etc/mariabackup.conf`

User SHOULD take a look at this file to make the MariaDB backup suit his needs.

## Examples

Backup all local databases:

`mariabackup -a`

Backup a local database named testdb:

`mariabackup -b testdb`

Backup all remote databases:

`mariabackup -a -r ~/.backup.cnf`

Backup a remote database named testdb:

`pgbackup -b testdb -r ~/.backup.cnf`

## Contribute

If you find a bug, please report it here: https://github.com/JGroselle/mariabackup/issues

If you want add some feature, feel free to make a PR. ;)

## Note

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL

NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED",  "MAY", and

"OPTIONAL" in this document are to be interpreted as described in

RFC 2119.
