<h1>smokeping-pgsqllatency</h1>
Smokeping::probes::pgsqllatency

Integrates PgSQL latency as a probe into smokeping. It's based off https://github.com/alecs/smokeping-plugins
The variables ("host"), ("user") and ("password") must be specified in order for the probe to work.

This assumes a PgSQL version >=8 and checks for the existence of the default db named 'postgres'

Earlier PgSQL versions may have to edit line 65 in PgSQLLatency.pm accordingly:

<code>prepare("SELECT datname,pid,query FROM pg_stat_activity ORDER BY pid;")</code>

Requires perl-DBI.
DBD::Pg may need Postgres and pgsql-libs pre-installed
You may need to edit postgresql.conf & pg_hba.conf to enable access/network connectivity


<pre>
Original author: Alex Negulescu https://github.com/alecs
Hacked for PgSQL: Strykar https://github.com/Strykar
With help from: fwaggle https://github.com/fwaggle
</pre>
