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

## License

GPLv3 (http://www.gnu.org/licenses/gpl-3.0.txt)
