# Daily Maintenance Script
Simple script for daily maintenance

## Set the script to execute on Launchd
For details take a look of the [Launchd Manual](https://www.unix.com/man-page/osx/5/launchd.plist/)

### Set environment
1. Create personal folder
```shell
mkdir $HOME/.bin
```
2. 
```shell
cp daily_maintenance $HOME/.bin
```

### Register script to launchd
1. Set permissions to be executed
```shell
chmod u+x,g+x,o+x $HOME/.bin/daily_maintenance
```
2.  Copy plist configuration to local user folder
```shell
cp daily_maintenance.plist $HOME/Library/LaunchAgents
```
3.  load the script to launchd
```shell
cd $HOME/Library/LaunchAgents
launchctl load -w daily_maintenance.plist
```

### Unload and delete plist script from launchd
```shell
launchctl unload -w daily_maintenance.plist
rm $HOME/Library/LaunchAgents/daily_maintenance.plist
```

### Useful command for launchd
Start the script:
```shell
launchctl start com.bicio.daily_maintenance.agent
```

Stop the script:
```shell
launchctl stop com.bicio.daily_maintenance.agent
```

List registered agents and search for the daily maintenance script:
```shell
launchctl list | grep daily_maintenance
```

Remove the daily maintenance agent from launchd
```shell
launchctl remove com.bicio.daily_maintenance.agent
```