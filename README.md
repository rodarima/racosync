## racosync

*Syncronize files from raco.fib.upc.edu*

The racosync(1) program search the Racó for new or modified files (attachments)
and syncronizes the local copy accordinly. It is designed to be launched
regularly, with cron or systemd timers.

See the manual racosync(1) for more details.

### Configuration

The configuration file `~/.racosync/config.json` should contain the output
directory where the files will be downloaded. The provided file can be used as
example:

	{
		"out_dir" : "~/raco/"
	}

To obtain a valid token, run the program in the command line, to follow the
Oauth link:

	$ racosync
	Please go here and authorize, https://api.fib....rompt=auto
	Paste the full redirect URL here:

The link will redirect you to a localhost page. Paste the URL in the terminal.
After a successful login you should be able to see in the log file
`~/.racosync/log` the first sync files being added:

	1520878971 A /home/joe/raco/cc/notes.pdf
	1520878974 A /home/joe/raco/ml/ML-MIRI-04.pdf
	1520878975 A /home/joe/raco/ml/L02.zip
	1520878976 A /home/joe/raco/ml/ML-MIRI-03.pdf
	1520878977 A /home/joe/raco/ml/L01.zip
	1520878978 A /home/joe/raco/ads/ads-miri.pdf
	...

### Running

To manually syncronize the files just run:

	$ racosync

#### Systemd timer

In order to enable the automatic update each 30 minutes, a timer is provided as
well a a service file. To start the timer execute:

	$ systemctl start --user racosync.timer

And to enable the timer at boot use: 

	$ systemctl enable --user racosync.timer
