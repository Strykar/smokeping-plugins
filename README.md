<h1>smokeping-pgsqllatency</h1>
Smokeping::probes::pgsqllatency
___
Integrates PgSQL latency as a probe into smokeping. It's based off <a href="https://github.com/alecs/smokeping-plugins">Alecs</a> MySQL smokeping probe.

The variables ("host"), ("user") and ("password") must be specified in order for the probe to work.

This assumes a PgSQL version >=8 and checks for the existence of the default db named 'postgres'

Earlier PgSQL versions may have to edit line 65 in <code>PgSQLLatency.pm</code> from:

<pre>("SELECT datname,pid,query FROM pg_stat_activity ORDER BY pid;")</pre>
to
<pre>"SELECT datname,procpid,current_query FROM pg_stat_activity ORDER BY procpid;"</pre>

Requires perl-DBI

DBD::Pg may need postgresql and pgsql-libs pre-installed on the master

You may need to edit postgresql.conf & pg_hba.conf to enable access/network connectivity


Logging: You can get logs of what goes on inside the plugin either by running smokeping with --debug, or by changing this line:
<pre>
  #set to LOG_ERR to disable debugging, LOG_DEBUG to enable it
  setlogmask(LOG_MASK(LOG_ERR));
</pre>
to
<pre>
  #set to LOG_ERR to disable debugging, LOG_DEBUG to enable it
  setlogmask(LOG_MASK(LOG_DEBUG));
</pre>
After doing this (and restarting smokeping), the plugin's logs will go to syslog, local0.debug. You will need something like

  `local0.*     /var/log/local.log`

in your syslog configuration.

___
<img src="https://dl.dropboxusercontent.com/u/314525/PT4_DB_mini.png">
<img src="https://dl.dropboxusercontent.com/u/314525/Slack14_DB_mini.png">

<pre>
Original author: Alex Negulescu https://github.com/alecs
Hacked for PgSQL: Strykar https://github.com/Strykar
With help from: fwaggle https://github.com/fwaggle
</pre>
