# nagios-munin-problems

Pull apart Munin's problems.html for Nagios to process.

## Installation

This is a Nagios plugin, upload to `/etc/nagios/plugins/` or wherever your plugins are stored.

## Configuration

By default we read `/var/cache/munin/www/problems.html` locally, this can be replaced by sourcing the file over HTTP, for example, if Munin and Nagios are on separate servers.

The Nagios command to use should look like this:

```
define command {
	command_name	check_munin_problems
	command_line	$USER1$/check_munin_problems $HOSTADDRESS$
}
```

A second argument to `check_munin_problems` will enable filtering for certain problems. For example, for Nagios to not be alerted by [WordPress plugins that haven't been updated](https://github.com/pressjitsu/munin-wp-plugins) `check_munin_problems $HOSTADDRESS$ wp_plugins` can be called. This will returns the usual output but an exit code of 0 if there are no other problems with the host. Several ignores can be provided by using a comma as a delimiter: `check_munin_problems $HOSTADDRESS$ wp_plugins,mysql_threads`.

## License

GPLv3 (http://www.gnu.org/licenses/gpl-3.0.txt)
