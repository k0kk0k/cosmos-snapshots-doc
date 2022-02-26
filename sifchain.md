## Download latest snapshot  
Stop Sifchain service  
`systemctl stop sifchain.service`  

Remove old data in directory `~/.sifnoded/data`  
```
rm -rf ~/.sifnoded/data; \
mkdir -p ~/.sifnoded/data; \
cd ~/.sifnoded/data
```

Download snapshot  
```bash
SNAP_NAME=$(curl -s https://snapshots.stake2.me/sifchain/ | egrep -o ">sifchain.*tar" | tr -d ">" | tail -n1); \
wget -O - https://snapshots.stake2.me/sifchain/${SNAP_NAME} | tar xf -
```

Start service and check logs  
```
systemctl start sifchain.service; \
journalctl -u sifchain.service -f --no-hostname
```
