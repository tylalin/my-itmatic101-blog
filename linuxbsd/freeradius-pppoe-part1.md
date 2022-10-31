# FreeRADIUS နဲ့ PPPoE Authentication အပိုင်း \(၁\)

RADIUS ဆိုတာကတော့ Remote Authentication Dial-In User Service ရဲ့ အတိုကောက်ဖြစ်ပြီးတော့၊ တော်တော်လေးလည်း ရှေးကျတဲ့ authentication service လည်းဖြစ်ပါတယ်။ သူ့နာမည်မှာကိုက dail-in ဆိုတာပါနေတာကိုကြည့်ခြင်းအားဖြင့် သူရှိနေခဲ့တာဘယ်လောက်ကြာပြီလဲဆိုတာကို မှန်းကြည့်လို့ရပါတယ်။ စာရေးသူ RADIUS နဲ့ ပတ်သတ်ပြီးတော့ open-source solution မှာရှာကြည့်သလောက်တော့ FreeRADIUS ကိုလူပြောများတာနဲ့ လုပ်ငန်းခွင်မှာ အသုံးများတဲ့ PPPoE အတွက် authentication ကိုဘယ်လို လုပ်သလဲဆိုတာ စပြီးတော့ စမ်းသပ်ဖို့ရာဖြစ်လာပါတော့တယ်။ ဒီ post မှာတော့ စာရေးသူရဲ့ အကြိုက်ဆုံးဖြစ်တဲ့ CentOS7 ကိုအသုံးပြုထားပြီးတော့ FreeRADIUS install လုပ်ပုံအဆင့်ဆင့် ကိုရှင်းပြသွားပါ့မယ်။ ‌ပြီးတော့ local flat configuration file အစား MySQL database ကိုအသုံးပြုမှာဖြစ်ပြီးတော့ Dalo RADIUS ဆိုတဲ့ WebUI နဲ့ manage လုပ်တဲ့ပုံစံကို အဆင့်ဆင့်ဖော်ပြပေးသွားပါ့မယ်။ ပထမဆုံးအနေနဲ့ CentOS7 ကို အရင်ဆုံး install လုပ်ရပါ့မယ်။ CentOS7 installation process ကိုတော့ ဒီ post မှာ မရှင်းတော့ပါဘူး။ ‌CentOS7 မှာအသုံးပြုထားတဲ့ Anaconda installer က ရိုးရှင်းပြီးတော့ install လုပ်ရတာလည်း လွယ်ပါတယ်။ Linux မှာ ကိုယ်က အခုမှစတင်လေ့လာနေတယ်ဆိုရင်တော့ YouTube မှာ CentOS 7 ကို ဘယ်လို install လုပ်သလဲဆိုတာ ကိုယ်တိုင်ရှာကြည့်လို့ရပါတယ်။ CentOS7 ကို install လုပ်ပြီးလို့ အဆင်သင့်ဖြစ်ပြီဆိုရင်တော့ အောက်ကအတိုင်း FreeRADIUS ကို စတင် install လုပ်လို့ရပါပြီ။

## FreeRADIUS ကို CentOS7 ပေါ်တွင် install လုပ်ပုံ

```text
[tyla@rpm-dev01 ~]$ sudo -i
[sudo] password for tyla:

# update system and package with YUM
[root@rpm-dev01  ~]# yum update -y

# install required freeRADIUS package with YUM
[root@rpm-dev01  ~]# sudo yum -y install freeradius freeradius-utils freeradius-mysql freeradius-perl

# start and enable the freeRADIUS daemon radiusd as below
[root@rpm-dev01  ~]# systemctl start radiusd
[root@rpm-dev01  ~]# systemctl enable radiusd

# verify the status of radiusd
[root@rpm-dev01  ~]# systemctl status radiusd
● radiusd.service - FreeRADIUS high performance RADIUS server.
   Loaded: loaded (/usr/lib/systemd/system/radiusd.service; enabled; vendor preset: disabled)
   Active: active (running) since Thu 2019-10-31 15:55:13 UTC; 1 day 20h ago
  Process: 11626 ExecReload=/bin/kill -HUP $MAINPID (code=exited, status=0/SUCCESS)
  Process: 11622 ExecReload=/usr/sbin/radiusd -C (code=exited, status=0/SUCCESS)
  Process: 2095 ExecStart=/usr/sbin/radiusd -d /etc/raddb (code=exited, status=0/SUCCESS)
  Process: 2090 ExecStartPre=/usr/sbin/radiusd -C (code=exited, status=0/SUCCESS)
  Process: 2088 ExecStartPre=/bin/chown -R radiusd.radiusd /var/run/radiusd (code=exited, status=0/SUCCESS)
 Main PID: 2098 (radiusd)
   CGroup: /system.slice/radiusd.service
           └─2098 /usr/sbin/radiusd -d /etc/raddb

Oct 31 15:55:13 rpm-dev01 systemd[1]: Starting FreeRADIUS high performan....
Oct 31 15:55:13 rpm-dev01 systemd[1]: Started FreeRADIUS high performanc....
Nov 01 03:47:01 rpm-dev01 systemd[1]: Reloading FreeRADIUS high performa....
Nov 01 03:47:01 rpm-dev01 systemd[1]: Reloaded FreeRADIUS high performan....
Hint: Some lines were ellipsized, use -l to show in full.
```

## CentOS7 ရဲ့ Firewall ကို freeRADIUS အတွက်ပြင်ဆင်ရပုံ

```text
# start and enable firewalld on CentOS7
[root@rpm-dev01  ~]# systemctl enable firewalld
[root@rpm-dev01  ~]# systemctl start firewalld

# verify the status of firewalld
[root@rpm-dev01  ~]# systemctl status firewalld
● firewalld.service - firewalld - dynamic firewall daemon
   Loaded: loaded (/usr/lib/systemd/system/firewalld.service; enabled; vendor preset: enabled)
   Active: active (running) since Fri 2019-10-11 18:11:21 UTC; 3 weeks 0 days ago
     Docs: man:firewalld(1)
 Main PID: 958 (firewalld)
   CGroup: /system.slice/firewalld.service
           └─958 /usr/bin/python2 -Es /usr/sbin/firewalld --nofork --nopid

Oct 11 18:11:20 rpm-dev01 systemd[1]: Starting firewalld - dynamic firew....
Oct 11 18:11:21 rpm-dev01 systemd[1]: Started firewalld - dynamic firewa....
Hint: Some lines were ellipsized, use -l to show in full.

# add http, https, radius services to be allowed through the firewalld permanently
[root@rpm-dev01  ~]# firewall-cmd --add-service={http,https,radius} --permanent

# reload the firewalld
[root@rpm-dev01  ~]# firewall-cmd --reload

# check the default zone on firewalld
[root@rpm-dev01  ~]# firewall-cmd --get-default-zone
public

# list the allowed services in public zone on firewalld 
[root@rpm-dev01  ~]# firewall-cmd --list-services --zone=public
dhcpv6-client http https radius ssh

# test freeRADIUS server in debug mode
[root@rpm-dev01  ~]# pkill radius
[root@rpm-dev01  ~]# radiusd -X
.....
Listening on auth address * port 1812 bound to server default
Listening on acct address * port 1813 bound to server default
Listening on auth address :: port 1812 bound to server default
Listening on acct address :: port 1813 bound to server default
Listening on auth address 127.0.0.1 port 18120 bound to server inner-tunnel
Listening on proxy address * port 47495
Listening on proxy address :: port 52337
Ready to process requests
```

ဒီအဆင့်မှာတော့ freeRADIUS ရဲ့ installation process ကပြီးသွားပါပြီ။ ကိုယ်က basic ပုံစံမျိုး flat config file ထဲမှာပဲ configure လုပ်ချင်တယ်ဆိုရင်တော့ /etc/raddb အောက်မှာတစ်ခုချင်းစီ ကိုယ်ကြိုက်သလို စတင်ပြီးတော့ configure လုပ်လို့ရပါပြီ။ သို့သော်လည်း အစကပြောခဲ့သလိုမျိုး စာရေးသူက flat file အစား MySQL db ကိုအသုံးပြုပြီးတော့ data တွေကို store လုပ်ချင်လို့ mariadb ကိုအသုံးပြုပါ့မယ်။ နောက်ပြီးတော့ Dalo RADIUS ဆိုတဲ့ WebUI အသုံးပြုပြီးတော့ MySQL database ကို manage လုပ်ချင်တဲ့အတွက် Apache နဲ့ daloradius တို့ကို install ထက်လုပ်ရပါ့မယ်။ အောက်မှာတော့ mariadb၊ Apache နဲ့ daloradius တို့ကို install ဘယ်လိုလုပ်သလဲဆိုတာကို ဖော်ပြသွားပါ့မယ်။

```text
# mariadb 10 is not the default on CentOS7 thus add the repo to yum repos
[root@rpm-dev01  ~]# vi /etc/yum.repos.d/MariaDB.repo

[mariadb]
name = MariaDB
baseurl = http://yum.mariadb.org/10.1/centos7-amd64
gpgkey=https://yum.mariadb.org/RPM-GPG-KEY-MariaDB
gpgcheck=1

# update the package index
[root@rpm-dev01  ~]# yum -y update

# install mariadb
[root@rpm-dev01  ~]# yum install -y mariadb-server mariadb

# start and enable mariadb
[root@rpm-dev01  ~]# systemctl start mariadb
[root@rpm-dev01  ~]# systemctl enable mariadb

# verify the mariadb status
[root@rpm-dev01  ~]# systemctl status mariadb
● mariadb.service - MariaDB 10.1.41 database server
   Loaded: loaded (/usr/lib/systemd/system/mariadb.service; enabled; vendor preset: disabled)
  Drop-In: /etc/systemd/system/mariadb.service.d
           └─migrated-from-my.cnf-settings.conf
   Active: active (running) since Fri 2019-10-11 18:11:23 UTC; 3 weeks 0 days ago
     Docs: man:mysqld(8)
           https://mariadb.com/kb/en/library/systemd/
  Process: 1669 ExecStartPost=/bin/sh -c systemctl unset-environment _WSREP_START_POSITION (code=exited, status=0/SUCCESS)
  Process: 1300 ExecStartPre=/bin/sh -c [ ! -e /usr/bin/galera_recovery ] && VAR= ||   VAR=`/usr/bin/galera_recovery`; [ $? -eq 0 ]   && systemctl set-environment _WSREP_START_POSITION=$VAR || exit 1 (code=exited, status=0/SUCCESS)
  Process: 1292 ExecStartPre=/bin/sh -c systemctl unset-environment _WSREP_START_POSITION (code=exited, status=0/SUCCESS)
 Main PID: 1399 (mysqld)
   Status: "Taking your SQL requests now..."
   CGroup: /system.slice/mariadb.service
           └─1399 /usr/sbin/mysqld

Oct 11 18:11:23 rpm-dev01 mysqld[1399]: 2019-10-11 18:11:23 140521942583552 [Note] InnoDB: Highest supported file format is Barracuda.
Oct 11 18:11:23 rpm-dev01 mysqld[1399]: 2019-10-11 18:11:23 140521942583552 [Note] InnoDB: 128 rollback segment(s) are active.
Oct 11 18:11:23 rpm-dev01 mysqld[1399]: 2019-10-11 18:11:23 140521942583552 [Note] InnoDB: Waiting for purge to start
Oct 11 18:11:23 rpm-dev01 mysqld[1399]: 2019-10-11 18:11:23 140521942583552 [Note] InnoDB:  Percona XtraDB (http://www.percona.com) 5.6.44-86.0 started; log sequence number 1784971
Oct 11 18:11:23 rpm-dev01 mysqld[1399]: 2019-10-11 18:11:23 140521146152704 [Note] InnoDB: Dumping buffer pool(s) not yet started
Oct 11 18:11:23 rpm-dev01 mysqld[1399]: 2019-10-11 18:11:23 140521942583552 [Note] Plugin 'FEEDBACK' is disabled.
Oct 11 18:11:23 rpm-dev01 mysqld[1399]: 2019-10-11 18:11:23 140521942583552 [Note] Server socket created on IP: '::'.
Oct 11 18:11:23 rpm-dev01 mysqld[1399]: 2019-10-11 18:11:23 140521942583552 [Note] /usr/sbin/mysqld: ready for connections.
Oct 11 18:11:23 rpm-dev01 mysqld[1399]: Version: '10.1.41-MariaDB'  socket: '/var/lib/mysql/mysql.sock'  port: 3306  MariaDB Server
Oct 11 18:11:23 rpm-dev01 systemd[1]: Started MariaDB 10.1.41 database server.

#  check if it is enabled to survive the reboot
[root@rpm-dev01  ~]# systemctl is-enabled mariadb.service
enabled
```

## MySQL server အား initial setup နဲ့ db root password ထည့်သွင်းပုံ

```text
[root@rpm-dev01  ~]# mysql_secure_installation
Enter current password for root (enter for none): ENTER
Set root password? [Y/n] y
New password: Enter password
Re-enter new password: Repeat password
Remove anonymous users? [Y/n]: Y
Disallow root login remotely? [Y/n]: Y
Remove test database and access to it? [Y/n]: Y
Reload privilege tables now? [Y/n]: Y
```

မှတ်ချက် – အထက်တွင်ထည့်သွင်းသော root password သည် system root password မဟုတ်ပါ။ MySQL db အတွက် အသုံးပြုသော root password ဖြစ်သည်။ သို့ပါ၍ ထို password အား တစ်နေရာတွင် မှတ်ထားပါ။ နောက်ပိုင်းတွင် ၄င်း password ကို အသုံးပြု၍ MySQL db အား ချိတ်ဆက်ရန် တဖန်လိုလိမ့်မည်။

## PHP 7 အား CentOS7 ပေါ်တွင်ထည့်သွင်းအသုံးပြုပုံ

```text
# add remi and epel repos
[root@rpm-dev01  ~]# yum install epel-release yum-utils
[root@rpm-dev01  ~]# yum install http://rpms.remirepo.net/enterprise/remi-release-7.rpm

# enable the PHP 7.3 remi repo
[root@rpm-dev01  ~]# yum-config-manager --enable remi-php73

# install PHP 7.3 packages
[root@rpm-dev01  ~]# yum install php php-common php-opcache php-mcrypt php-cli php-gd php-curl php-mysqlnd

# verify the version of installed PHP
[root@rpm-dev01  ~]# php -v
PHP 7.3.10 (cli) (built: Sep 24 2019 09:20:18) ( NTS )
Copyright (c) 1997-2018 The PHP Group
Zend Engine v3.3.10, Copyright (c) 1998-2018 Zend Technologies
    with Zend OPcache v7.3.10, Copyright (c) 1999-2018, by Zend Technologies
```

## Mariadb ပေါ်တွင် freeradius အတွက် database တစ်ခုတည်ဆောက်ပုံ

```text
[root@rpm-dev01  ~]# mysql -u root -p
Enter password:     # enter the db root password previously set
Welcome to the MariaDB monitor.  Commands end with ; or g.
Your MariaDB connection id is 498
Server version: 10.1.41-MariaDB MariaDB Server

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or 'h' for help. Type 'c' to clear the current input statement.

MariaDB [(none)]> CREATE DATABASE frad;
MariaDB [(none)]> GRANT ALL ON frad.* TO frad@localhost IDENTIFIED BY "fradpass!23";
MariaDB [(none)]> FLUSH PRIVILEGES;
MariaDB [(none)]> quit;

# import radius db scheme to populate frad database
[root@rpm-dev01  ~]# mysql -uroot -pDB_ROOT_PASSWORD frad < /etc/raddb/mods-config/sql/main/mysql/schema.sql
```

## freeRADIUS တွင် sql module အား activate ပြုလုပ်ပုံ

```text
# create a soft link to activate the sql module
[root@rpm-dev01  ~]# ln -s /etc/raddb/mods-available/sql /etc/raddb/mods-enabled/

# configure the sql module as required
[root@rpm-dev01  ~]# vi /etc/raddb/mods-available/sql
# -*- text -*-
##
## sql.conf -- SQL modules
##
##	$Id: 4a59483c35c77f573fb177919e19ba4434cc3da1 $

######################################################################
#
#  Configuration for the SQL module
#
#  The database schemas and queries are located in subdirectories:
#
#	sql//main/schema.sql	Schema
#	sql//main/queries.conf	Authorisation and Accounting queries
#
#  Where "DB" is mysql, mssql, oracle, or postgresql.
#
#

sql {
	# The sub-module to use to execute queries. This should match
	# the database you're attempting to connect to.
	#
	#    * rlm_sql_mysql
	#    * rlm_sql_mssql
	#    * rlm_sql_oracle
	#    * rlm_sql_postgresql
	#    * rlm_sql_sqlite
	#    * rlm_sql_null (log queries to disk)
	#
	driver = "rlm_sql_mysql"

#
#	Several drivers accept specific options, to set them, a
#	config section with the the name as the driver should be added
#	to the sql instance.
#
#	Driver specific options are:
#
#	sqlite {
#		# Path to the sqlite database
#		filename = "/tmp/freeradius.db"
#
#		# How long to wait for write locks on the database to be
#		# released (in ms) before giving up.
#		busy_timeout = 200
#
#		# If the file above does not exist and bootstrap is set
#		# a new database file will be created, and the SQL statements
#		# contained within the bootstrap file will be executed.
#		bootstrap = "${modconfdir}/${..:name}/main/sqlite/schema.sql"
# 	}
#
#	mysql {
#		# If any of the files below are set, TLS encryption is enabled
#		tls {
#			ca_file = "/etc/ssl/certs/my_ca.crt"
#			ca_path = "/etc/ssl/certs/"
#			certificate_file = "/etc/ssl/certs/private/client.crt"
#			private_key_file = "/etc/ssl/certs/private/client.key"
#			cipher = "DHE-RSA-AES256-SHA:AES128-SHA"
#		}
#
#		# If yes, (or auto and libmysqlclient reports warnings are
#		# available), will retrieve and log additional warnings from
#		# the server if an error has occured. Defaults to 'auto'
#		warnings = auto
#	}
#
#	postgresql {
#
#		# unlike MySQL, which has a tls{} connection configuration, postgresql
#		# uses its connection parameters - see the radius_db option below in
#		# this file
#
#		# Send application_name to the postgres server
#		# Only supported in PG 9.0 and greater. Defaults to no.
#		send_application_name = yes
#	}
#

	# The dialect of SQL you want to use, this should usually match
	# the driver you selected above.
	#
	# If you're using rlm_sql_null, then it should be the type of
	# database the logged queries are going to be executed against.
	dialect = "mysql"

	# Connection info:
	#
	server = "localhost"
	port = 3306
	login = "frad"
	password = "fradpass!23"

	# Database table configuration for everything except Oracle
	radius_db = "frad"

	# If you are using Oracle then use this instead
#	radius_db = "(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=localhost)(PORT=1521))(CONNECT_DATA=(SID=your_sid)))"

	# If you're using postgresql this can also be used instead of the connection info parameters
#	radius_db = "dbname=radius host=localhost user=radius password=raddpass"

        # Postgreql doesn't take tls{} options in its module config like mysql does - if you want to
        # use SSL connections then use this form of connection info parameter
#	radius_db = "host=localhost port=5432 dbname=radius user=radius password=raddpass sslmode=verify-full sslcert=/etc/ssl/client.crt sslkey=/etc/ssl/client.key sslrootcert=/etc/ssl/ca.crt" 

	# If you want both stop and start records logged to the
	# same SQL table, leave this as is.  If you want them in
	# different tables, put the start table in acct_table1
	# and stop table in acct_table2
	acct_table1 = "radacct"
	acct_table2 = "radacct"

	# Allow for storing data after authentication
	postauth_table = "radpostauth"

	# Tables containing 'check' items
	authcheck_table = "radcheck"
	groupcheck_table = "radgroupcheck"

	# Tables containing 'reply' items
	authreply_table = "radreply"
	groupreply_table = "radgroupreply"

	# Table to keep group info
	usergroup_table = "radusergroup"

	# If set to 'yes' (default) we read the group tables unless Fall-Through = no in the reply table.
	# If set to 'no' we do not read the group tables unless Fall-Through = yes in the reply table.
#	read_groups = yes

	# If set to 'yes' (default) we read profiles unless Fall-Through = no in the groupreply table.
	# If set to 'no' we do not read profiles unless Fall-Through = yes in the groupreply table.
#	read_profiles = yes

	# Remove stale session if checkrad does not see a double login
	delete_stale_sessions = yes

	# Write SQL queries to a logfile. This is potentially useful for tracing
	# issues with authorization queries.  See also "logfile" directives in
	# mods-config/sql/main/*/queries.conf.  You can enable per-section logging
	# by enabling "logfile" there, or global logging by enabling "logfile" here.
	#
	# Per-section logging can be disabled by setting "logfile = ''"
#	logfile = ${logdir}/sqllog.sql

	#  Set the maximum query duration and connection timeout
	#  for rlm_sql_mysql.
#	query_timeout = 5

	#  As of version 3.0, the "pool" section has replaced the
	#  following configuration items:
	#
	#  num_sql_socks
	#  connect_failure_retry_delay
	#  lifetime
	#  max_queries

	#
	#  The connection pool is new for 3.0, and will be used in many
	#  modules, for all kinds of connection-related activity.
	#
	# When the server is not threaded, the connection pool
	# limits are ignored, and only one connection is used.
	#
	# If you want to have multiple SQL modules re-use the same
	# connection pool, use "pool = name" instead of a "pool"
	# section.  e.g.
	#
	#	sql1 {
	#	    ...
	#	    pool {
	#	    	 ...
	#	    }
	#	}
	#
	#	# sql2 will use the connection pool from sql1
	#	sql2 {
	#	     ...
	#	     pool = sql1
	#	}
	#
	pool {
		#  Connections to create during module instantiation.
		#  If the server cannot create specified number of
		#  connections during instantiation it will exit.
		#  Set to 0 to allow the server to start without the
		#  database being available.
		start = ${thread[pool].start_servers}

		#  Minimum number of connections to keep open
		min = ${thread[pool].min_spare_servers}

		#  Maximum number of connections
		#
		#  If these connections are all in use and a new one
		#  is requested, the request will NOT get a connection.
		#
		#  Setting 'max' to LESS than the number of threads means
		#  that some threads may starve, and you will see errors
		#  like 'No connections available and at max connection limit'
		#
		#  Setting 'max' to MORE than the number of threads means
		#  that there are more connections than necessary.
		max = ${thread[pool].max_servers}

		#  Spare connections to be left idle
		#
		#  NOTE: Idle connections WILL be closed if "idle_timeout"
		#  is set.  This should be less than or equal to "max" above.
		spare = ${thread[pool].max_spare_servers}

		#  Number of uses before the connection is closed
		#
		#  0 means "infinite"
		uses = 0

		#  The number of seconds to wait after the server tries
		#  to open a connection, and fails.  During this time,
		#  no new connections will be opened.
		retry_delay = 30

		# The lifetime (in seconds) of the connection
		lifetime = 0

		#  idle timeout (in seconds).  A connection which is
		#  unused for this length of time will be closed.
		idle_timeout = 60

		#  NOTE: All configuration settings are enforced.  If a
		#  connection is closed because of "idle_timeout",
		#  "uses", or "lifetime", then the total number of
		#  connections MAY fall below "min".  When that
		#  happens, it will open a new connection.  It will
		#  also log a WARNING message.
		#
		#  The solution is to either lower the "min" connections,
		#  or increase lifetime/idle_timeout.
	}

	# Set to 'yes' to read radius clients from the database ('nas' table)
	# Clients will ONLY be read on server startup.
	read_clients = yes

	# Table to keep radius client info
	client_table = "nas"

	#
	# The group attribute specific to this instance of rlm_sql
	#

	# This entry should be used for additional instances (sql foo {})
	# of the SQL module.
#	group_attribute = "${.:instance}-SQL-Group"

	# This entry should be used for the default instance (sql {})
	# of the SQL module.
	group_attribute = "SQL-Group"

	# Read database-specific queries
	$INCLUDE ${modconfdir}/${.:name}/main/${dialect}/queries.conf
}
```

အကျဉ်းအားဖြင့်တော့ ပြင်ရမယ့် line number တွေကိုပဲ highlight လုပ်ပေးထားပါတယ်။ ပထမဆုံး အနေနဲ့ line number ၃၆ ဖြစ်တဲ့ driver = “rlm\_sql\_null” ကို driver = “rlm\_sql\_mysql” ဆိုပြီးပြင်ဆင်ရမယ်။ ဒုတိယ အနေနဲ့ line number ၉၂ ဖြစ်တဲ့ dialect = “sqlite” ကို dialect = “mysql” ဆိုပြီးပြောင်းပေးရမယ်။ ပြီးတော့ line number ၉၆ ကနေပြီး ၉၉ မှာရှိတဲ့ \# တွေကိုဖယ်ပြီးတော့ အထက်မှာပြထားသလို ပြင်ဆင်ရမယ်။ ကိုယ်က MySQL database ကို တခြား server မှာ run ထားရင်တော့ လိုအပ်သလို ပြင်ဆင်ပြီးတော့ configure လုပ်နိုင်ပါတယ်။ ဒီ တစ်ခုမှာတော့ localhost မှာပဲ freeRADIUS နဲ့ Mariadb ကို အတူတူတွဲပြီးတော့ run တဲ့အတွက် localhost ဆိုပြီးထည့်ထားတာဖြစ်ပါတယ်။ နောက်တစ်ခု ပြင်ရမှာကတော့ line number ၁၀၂ မှာ radius\_db = “frad” ဆိုပြီးတော့ ပြောင်းထည့်ပေးရမှာ ဖြစ်ပါတယ်။ Line number ၂၅၀ နဲ့ ၂၅၃ မှာတော့ အထက်မှာပြထားသလို ဟုတ်မဟုတ် တချက်စစ်ကြည့်ပြီးတော့ လိုအပ်ပါက အထက်ကအတိုင်း ပြင်ဆင်ရပါ့မယ်။ နောက်တဆင့်မှာတော့ /etc/raddb/mods-enabled/sql ဆိုတဲ့ symbolic link ကို radiusd ရဲ့ group မှာ အောက်ကအတိုင်း လိုအပ်တဲ့ rights တွေပေးလိုက်ပါ့မယ်။

```text
[root@rpm-dev01  ~]# chgrp -h radiusd /etc/raddb/mods-enabled/sql

# verify and check if you can still run radiusd as below
[root@rpm-dev01  ~]# pkill radiusd
[root@rpm-dev01  ~]# radiusd -X
.....
Listening on auth address * port 1812 bound to server default
Listening on acct address * port 1813 bound to server default
Listening on auth address :: port 1812 bound to server default
Listening on acct address :: port 1813 bound to server default
Listening on auth address 127.0.0.1 port 18120 bound to server inner-tunnel
Listening on proxy address * port 47495
Listening on proxy address :: port 52337
Ready to process requests
```

အခုဆိုရင် freeRADIUS နဲ့ Mariadb MySQL တို့ကိုတွဲပြီး အသုံးပြုနိုင်ဖို့ အားလုံးပြင်ဆင်ပြီးပါပြီ။ နောက်တဆင့် အနေနဲ့ Dalo RADIUS WebUI နဲ့ Apache install လုပ်ပုံတို့ကို နောက်တပိုင်းမှာ ဆက်ပြီးတော့ ဖော်ပြပေးသွားပါ့မယ်။ ဒီအပိုင်းကိုတော့ ဒီမှာပဲရပ်လိုက်ပါတော့မယ်။

