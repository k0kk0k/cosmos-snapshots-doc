## Download latest snapshot  
Stop NYM service  
`systemctl stop nym.service`  

Remove old data in directory `~/.nyxd/data`  
```
rm -rf ~/.nyxd/data; \
mkdir -p ~/.nyxd/data; \
cd ~/.nyxd/data
```

Download snapshot  
```bash
SNAP_NAME=$(curl -s https://snapshots.stake2.me/nym/ | egrep -o ">nym.*tar" | tr -d ">" | tail -n1); \
wget -O - https://snapshots.stake2.me/nym/${SNAP_NAME} | tar xf -
```

Start service and check logs  
```
systemctl start nym.service; \
journalctl -u nym.service -f --no-hostname
```
