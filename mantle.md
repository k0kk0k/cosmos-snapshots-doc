## Download latest snapshot  
Stop AssetMantle service  
`systemctl stop mantle.service`  

Remove old data in directory `~/.mantleNode/data`  
```
rm -rf ~/.mantleNode/data; \
mkdir -p ~/.mantleNode/data; \
cd ~/.mantleNode/data
```

Download snapshot  
```bash
SNAP_NAME=$(curl -s https://snapshots.stake2.me/mantle/ | egrep -o ">mantle.*tar" | tr -d ">" | tail -n1); \
wget -O - https://snapshots.stake2.me/mantle/${SNAP_NAME} | tar xf -
```

Start service and check logs  
```
systemctl start mantle.service; \
journalctl -u mantle.service -f --no-hostname
```
