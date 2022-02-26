## Download latest snapshot  
Stop Certik service  
`systemctl stop certik.service`  

Remove old data in directory `~/.certik/data`  
```
rm -rf ~/.certik/data; \
mkdir -p ~/.certik/data; \
cd ~/.certik/data
```

Download snapshot  
```bash
SNAP_NAME=$(curl -s https://snapshots.stake2.me/certik/ | egrep -o ">certik.*tar" | tr -d ">" | tail -n1); \
wget -O - https://snapshots.stake2.me/certik/${SNAP_NAME} | tar xf -
```

Start service and check logs  
```
systemctl start certik.service; \
journalctl -u certik.service -f --no-hostname
```
