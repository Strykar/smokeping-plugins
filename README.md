<pre>
This addon integrates PgSQL latency into smokeping and is based off https://github.com/alecs/smokeping-plugins
The variables ("host"), ("user") and ("password") must be specified in order for the probe to work.

This assumes a PgSQL version >=8 and checks for the existence of the default db named 'postgres'
Earlier PgSQL versions will have to edit line 65 in PgSQLLatency.pm accordingly:
prepare("SELECT datname,pid,query FROM pg_stat_activity ORDER BY pid;")

Requires perl-DBI.
You may need to edit postgresql.conf & pg_hba.conf to allow remote connections and listen on network interfaces

Original author: Alex Negulescu alecs@altlinux.org
Hacked to PgSQL: Strykar strykar@hotmail.com
With help from: fwaggle fwaggle@fwaggle.org
</pre>
