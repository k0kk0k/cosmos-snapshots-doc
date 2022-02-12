## Download latest snapshot  
Stop Firmachain service  
`systemctl stop firmachain.service`  

Remove old data in directory `~/.firmachain/data`  
```
rm -rf ~/.firmachain/data; \
mkdir -p ~/.firmachain/data; \
cd ~/.firmachain/data
```

Download snapshot  
```bash
SNAP_NAME=$(curl -s https://snapshots.stake2.me/firmachain/ | egrep -o ">firmachain.*tar" | tr -d ">"); \
wget -O - https://snapshots.stake2.me/firmachain/${SNAP_NAME} | tar xf -
```

Start service and check logs  
```
systemctl start firmachain.service; \
journalctl -u firmachain.service -f --no-hostname
```
