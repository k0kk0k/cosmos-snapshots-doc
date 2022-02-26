## Download latest snapshot  
Stop UMEE service  
`systemctl stop umee.service`  

Remove old data in directory `~/.umee/data`  
```
rm -rf ~/.umee/data; \
mkdir -p ~/.umee/data; \
cd ~/.umee/data
```

Download snapshot  
```bash
SNAP_NAME=$(curl -s https://snapshots.stake2.me/umee/ | egrep -o ">umee.*tar" | tr -d ">" | tail -n1); \
wget -O - https://snapshots.stake2.me/umee/${SNAP_NAME} | tar xf -
```

Start service and check logs  
```
systemctl start umee.service; \
journalctl -u umee.service -f --no-hostname
```
