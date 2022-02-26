## Download latest snapshot  
Stop Gravity bridge service  
`systemctl stop gravity.service`  

Remove old data in directory `~/.gravity/data`  
```
rm -rf ~/.gravity/data; \
mkdir -p ~/.gravity/data; \
cd ~/.gravity/data
```

Download snapshot  
```bash
SNAP_NAME=$(curl -s https://snapshots.stake2.me/gravity/ | egrep -o ">gravity.*tar" | tr -d ">" | tail -n1); \
wget -O - https://snapshots.stake2.me/gravity/${SNAP_NAME} | tar xf -
```

Start service and check logs  
```
systemctl start gravity.service; \
journalctl -u gravity.service -f --no-hostname
```
