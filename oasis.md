## Download latest snapshot  
Stop Oasis service  
`systemctl stop oasis.service`  

Remove `abci-state` and `data` in directory `.../serverdir/node/tendermint/` and remove `.../serverdir/node/persistent-store.badger.db`  

Go to `.../serverdir/node/tendermint/`

Download snapshot  
```bash
SNAP_NAME=$(curl -s https://snapshots.stake2.me/oasis/ | egrep -o ">oasis.*tar" | tr -d ">" | tail -n1); \
wget -O - https://snapshots.stake2.me/oasis/${SNAP_NAME} | tar xf -
```

Start service and check logs  
```
systemctl start oasis.service; \
journalctl -u oasis.service -f --no-hostname
```
