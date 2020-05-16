# Set Number of Watchers

## Reason

When working with some IDE or development tool which watch a folder in search from changes will make reach the limit of watchers really easy; So, you may want to put a higher limit of watchers in your SO

## Hot To

### Show how many watchers per user are:

```bash
cat /proc/sys/fs/inotify/max_user_watches
```

### Set how many watchers per user:

```bash
sudo nano /etc/sysctl.conf
```
- Go to the line `fs.inotify.max_user_watches` or go to the botton and type the number of watchers

```bash
fs.inotify.max_user_watches=524288
```

- Save the file
- Load the value to make it effective

```
sudo sysctl -p
```