## Download latest snapshot  
Stop Agoric service  
`systemctl stop agoric.service`  

Remove old data in directory `~/.agoric/data`  
```
rm -rf ~/.agoric/data; \
mkdir -p ~/.agoric/data; \
cd ~/.agoric/data
```

Download snapshot  
```bash
SNAP_NAME=$(curl -s https://snapshots.stake2.me/agoric/ | egrep -o ">agoric.*tar" | tr -d ">" | tail -n1); \
wget -O - https://snapshots.stake2.me/agoric/${SNAP_NAME} | tar xf -
```

Start service and check logs  
```
systemctl start agoric.service; \
journalctl -u agoric.service -f --no-hostname
```
