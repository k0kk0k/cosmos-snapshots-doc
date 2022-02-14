## Download latest snapshot  
Stop Game service  
`systemctl stop gamehub.service`  

Remove old data in directory `~/.nibiru/data`  
```
rm -rf ~/.nibiru/data; \
mkdir -p ~/.nibiru/data; \
cd ~/.nibiru/data
```

Download snapshot  
```bash
SNAP_NAME=$(curl -s https://snapshots.stake2.me/gamehub/ | egrep -o ">gamehub.*tar" | tr -d ">"); \
wget -O - https://snapshots.stake2.me/gamehub/${SNAP_NAME} | tar xf -
```

Start service and check logs  
```
systemctl start gamehub.service; \
journalctl -u gamehub.service -f --no-hostname
```
