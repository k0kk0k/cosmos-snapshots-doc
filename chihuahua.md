## Download latest snapshot  
Stop Chihuahua service  
`systemctl stop chihuahua.service`  

Remove old data in directory `~/.chihuahua/data`  
```
rm -rf ~/.chihuahua/data; \
mkdir -p ~/.chihuahua/data; \
cd ~/.chihuahua/data
```

Download snapshot  
```bash
SNAP_NAME=$(curl -s https://snapshots.stake2.me/chihuahua/ | egrep -o ">chihuahua.*tar" | tr -d ">"); \
wget -O - https://snapshots.stake2.me/chihuahua/${SNAP_NAME} | tar xf -
```

Start service and check logs  
```
systemctl start chihuahua.service; \
journalctl -u chihuahua.service -f --no-hostname
```
