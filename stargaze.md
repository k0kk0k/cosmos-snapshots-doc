## Download latest snapshot  
Stop Stargaze service  
`systemctl stop stargaze.service`  

Remove old data in directory `~/.starsd/data` and `~/.starsd/wasm`  
```
rm -rf ~/.starsd/data ~/.starsd/wasm; \
mkdir -p ~/.starsd/data ~/.starsd/wasm
```

Download DB snapshot  
```bash
SNAP_NAME=$(curl -s https://snapshots.stake2.me/stargaze/ | egrep -o ">stargaze_[0-9].*tar" | tr -d ">" | tail -n1); \
cd ~/.starsd/data; wget -O - https://snapshots.stake2.me/stargaze/${SNAP_NAME} | tar xf -
```

Download WASM snapshot  
```bash
WASM_SNAP_NAME=$(curl -s https://snapshots.stake2.me/stargaze/ | egrep -o ">stargaze_wasm.*tar" | tr -d ">" | tail -n1); \
cd ~/.starsd/wasm; wget -O - https://snapshots.stake2.me/stargaze/${WASM_SNAP_NAME} | tar xf -
```

Start service and check logs  
```
systemctl start stargaze.service; \
journalctl -u stargaze.service -f --no-hostname
```
