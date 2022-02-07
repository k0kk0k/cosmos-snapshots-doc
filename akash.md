## Download latest snapshot  
Stop Akash service  
`systemctl stop akash.service`  

Remove old data in directory `~/.akash/data`  
```
rm -rf ~/.akash/data; \
mkdir -p ~/.akash/data; \
cd ~/.akash/data
```

Download snapshot  
```bash
SNAP_NAME=$(curl -s https://snapshots.stake2.me/akash/ | egrep -o ">akash .*tar" | tr -d ">"); \
wget -O - https://snapshots.stake2.me/akash/${SNAP_NAME} | tar xf -
```

Start service and check logs  
```
systemctl start akash.service; \
journalctl -u akash.service -f --no-hostname
```
