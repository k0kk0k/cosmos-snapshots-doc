## Download latest snapshot  
Stop Shentu service  
`systemctl stop shentu.service`  

Remove old data in directory `~/.shentud/data`  
```
rm -rf ~/.shentud/data; \
mkdir -p ~/.shentud/data; \
cd ~/.shentud/data
```

Download snapshot  
```bash
SNAP_NAME=$(curl -s https://snapshots.stake2.me/shentu/ | egrep -o ">shentu.*tar" | tr -d ">" | tail -n1); \
wget -O - https://snapshots.stake2.me/shentu/${SNAP_NAME} | tar xf -
```

Start service and check logs  
```
systemctl start shentu.service; \
journalctl -u shentu.service -f --no-hostname
```
