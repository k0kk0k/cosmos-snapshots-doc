## Download latest snapshot  
Stop Osmosis service  
`systemctl stop osmosis.service`  

Remove old data in directory `~/.osmosisd/data`  
```
rm -rf ~/.osmosisd/data; \
mkdir -p ~/.osmosisd/data; \
cd ~/.osmosisd/data
```

Download snapshot  
```bash
SNAP_NAME=$(curl -s https://snapshots.stake2.me/osmosis/ | egrep -o ">osmosis.*tar" | tr -d ">" | tail -n1); \
wget -O - https://snapshots.stake2.me/osmosis/${SNAP_NAME} | tar xf -
```

Start service and check logs  
```
systemctl start osmosis.service; \
journalctl -u osmosis.service -f --no-hostname
```
