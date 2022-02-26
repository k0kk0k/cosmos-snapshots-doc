## Download latest snapshot  
Stop Axelar service  
`systemctl stop axelar.service`  

Remove old data in directory `~/.axelar/data`  
```
rm -rf ~/.axelar/data; \
mkdir -p ~/.axelar/data; \
cd ~/.axelar/data
```

Download snapshot  
```bash
SNAP_NAME=$(curl -s https://snapshots.stake2.me/axelar/ | egrep -o ">axelar.*tar" | tr -d ">" | tail -n1); \
wget -O - https://snapshots.stake2.me/axelar/${SNAP_NAME} | tar xf -
```

Start service and check logs  
```
systemctl start axelar.service; \
journalctl -u axelar.service -f --no-hostname
```
