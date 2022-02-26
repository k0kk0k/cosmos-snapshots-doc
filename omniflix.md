## Download latest snapshot  
Stop Omniflix service  
`systemctl stop omniflix.service`  

Remove old data in directory `~/.omniflixhub/data`  
```
rm -rf ~/.omniflixhub/data; \
mkdir -p ~/.omniflixhub/data; \
cd ~/.omniflixhub/data
```

Download snapshot  
```bash
SNAP_NAME=$(curl -s https://snapshots.stake2.me/omniflix/ | egrep -o ">omniflix.*tar" | tr -d ">" | tail -n1); \
wget -O - https://snapshots.stake2.me/omniflix/${SNAP_NAME} | tar xf -
```

Start service and check logs  
```
systemctl start omniflix.service; \
journalctl -u omniflix.service -f --no-hostname
```
