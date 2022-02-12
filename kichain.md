## Download latest snapshot  
Stop Kichain service  
`systemctl stop kichain.service`  

Remove old data in directory `~/.kid/data`  
```
rm -rf ~/.kid/data; \
mkdir -p ~/.kid/data; \
cd ~/.kid/data
```

Download snapshot  
```bash
SNAP_NAME=$(curl -s https://snapshots.stake2.me/kichain/ | egrep -o ">kichain.*tar" | tr -d ">"); \
wget -O - https://snapshots.stake2.me/kichain/${SNAP_NAME} | tar xf -
```

Start service and check logs  
```
systemctl start kichain.service; \
journalctl -u kichain.service -f --no-hostname
```
