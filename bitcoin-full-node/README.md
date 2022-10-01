## Installing full node:

```
curl https://bitnodes.io/install-full-node.sh | sh
```

## Checking logs:
```
tail -f /root/bitcoin-core/.bitcoin/debug.log
```

## to stop:
```
cd /root/bitcoin-core/bin && ./stop.sh
```
## to uninstall:
```
./install-full-node.sh -u
```
