## Download latest snapshot  
Stop Stargaze service  
`systemctl stop stargaze.service`  

Remove old data in directory `~/.starsd/data`  
```
rm -rf ~/.starsd/data; \
mkdir -p ~/.starsd/data; \
cd ~/.starsd/data
```

Download snapshot  
```bash
SNAP_NAME=$(curl -s https://snapshots.stake2.me/stargaze/ | egrep -o ">stargaze.*tar" | tr -d ">"); \
wget -O - https://snapshots.stake2.me/stargaze/${SNAP_NAME} | tar xf -
```

Start service and check logs  
```
systemctl start stargaze.service; \
journalctl -u stargaze.service -f --no-hostname
```
