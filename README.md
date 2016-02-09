# NetspeedLogger

I've grown tired of my internet connection being very slow, especially when Comcast presumably is giving me a 150 Mbit/s connection.

The NetspeedLogger is a python script that will perform speedtest checks against www.speedtest.net and log the results to a designated logfile. It can easily be setup to run every 30 minutes in a user's crontab.

Currently, NetspeedLogger has the ability to work on machines hard wired to a network or machines that connect over WiFi. For WiFi enabled devices, an SSID whitelist can be configured in `config.yaml` to allow for NetspeedLogger to know which connections are your home network.

# Example Cron setup
Using crontab on a *Nix machine or in Cygwin on a windows machine, NetspeedLogger can be configured to run every 30 minutes. You can have multiple devices all append to a shared network file (like a file in dropbox).

`*/30 * * * * python NetspeedLogger --file $HOME/dropbox/speedtest.log > $LOGDIR/speedtest.out 2> $LOGDIR/speedtest.err`

# Log output
Each individual run of NetspeedLogger will generate a single log line consisting of a timestamp and a JSON encoded datastructure:

`[2016-02-08 22:17:01] {'SSID': '', 'Ping': '24.004 ms', 'System': 'Cygwin', 'Upload': '10.60 Mbit/s', 'Download': '6.42 Mbit/s', 'HardWired': True}`
