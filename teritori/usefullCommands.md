## Usefull commands
### Service management
Check logs
```
journalctl -fu teritorid -o cat
```

Start service
```
sudo systemctl start teritorid
```

Stop service
```
sudo systemctl stop teritorid
```

Restart service
```
sudo systemctl restart teritorid
```

### Node info
Synchronization info
```
teritorid status 2>&1 | jq .SyncInfo
```

Validator info
```
teritorid status 2>&1 | jq .ValidatorInfo
```

Node info
```
teritorid status 2>&1 | jq .NodeInfo
```

Show node id
```
teritorid tendermint show-node-id
```

### Wallet operations
List of wallets
```
teritorid keys list
```

Recover wallet
```
teritorid keys add $WALLET --recover
```

Delete wallet
```
teritorid keys delete $WALLET
```

Get wallet balance
```
teritorid query bank balances $TERITORI_WALLET_ADDRESS
```

Transfer funds
```
teritorid tx bank send $TERITORI_WALLET_ADDRESS <TO_TERITORI_WALLET_ADDRESS> 10000000utori
```

### Voting
```
teritorid tx gov vote 1 yes --from $WALLET --chain-id=$TERITORI_CHAIN_ID
```

### Staking, Delegation and Rewards
Delegate stake
```
teritorid tx staking delegate $TERITORI_VALOPER_ADDRESS 10000000utori --from=$WALLET --chain-id=$TERITORI_CHAIN_ID --gas=auto
```

Redelegate stake from validator to another validator
```
teritorid tx staking redelegate <srcValidatorAddress> <destValidatorAddress> 10000000utori --from=$WALLET --chain-id=$TERITORI_CHAIN_ID --gas=auto
```

Withdraw all rewards
```
teritorid tx distribution withdraw-all-rewards --from=$WALLET --chain-id=$TERITORI_CHAIN_ID --gas=auto
```

Withdraw rewards with commision
```
teritorid tx distribution withdraw-rewards $TERITORI_VALOPER_ADDRESS --from=$WALLET --commission --chain-id=$TERITORI_CHAIN_ID
```

### Validator management
Edit validator
```
teritorid tx staking edit-validator \
  --moniker=$NODENAME \
  --identity=<your_keybase_id> \
  --website="<your_website>" \
  --details="<your_validator_description>" \
  --chain-id=$TERITORI_CHAIN_ID \
  --from=$WALLET
```

Unjail validator
```
teritorid tx slashing unjail \
  --broadcast-mode=block \
  --from=$WALLET \
  --chain-id=$TERITORI_CHAIN_ID \
  --gas=auto
```

### Delete node
This commands will completely remove node from server. Use at your own risk!
```
sudo systemctl stop teritorid
sudo systemctl disable teritorid
sudo rm /etc/systemd/system/teritori* -rf
sudo rm $(which teritorid) -rf
sudo rm $HOME/.teritorid* -rf
sudo rm $HOME/teritori -rf
sed -i '/TERITORI_/d' ~/.bash_profile
```
