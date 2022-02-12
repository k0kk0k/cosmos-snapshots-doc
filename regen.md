## Download latest snapshot  
Stop Regen service  
`systemctl stop regen.service`  

Remove old data in directory `~/.regen/data`  
```
rm -rf ~/.regen/data; \
mkdir -p ~/.regen/data; \
cd ~/.regen/data
```

Download snapshot  
```bash
SNAP_NAME=$(curl -s https://snapshots.stake2.me/regen/ | egrep -o ">regen.*tar" | tr -d ">"); \
wget -O - https://snapshots.stake2.me/regen/${SNAP_NAME} | tar xf -
```

Start service and check logs  
```
systemctl start regen.service; \
journalctl -u regen.service -f --no-hostname
```
