IPTB full name is IPFS testbed, which can quickly launch and manage lots of nodes on one machine.

**Make sure btfs was installed and added to path environment before start below steps, no need "btfs init"**
# Install IPTB
```
git clone git@github.com:TRON-US/iptb-btfs-plugins.git
cd iptb-btfs-plugins
make install 
```
# Initialize BTFS node cluster
```
iptb auto -type localbtfs -count 4
iptb run -- btfs init
iptb run -- btfs config profile apply storage-host-testnet
iptb start
```
(optional) persist the port number
```
# build file https://github.com/TRON-US/iptb-btfs-plugins/blob/master/standalone/rewrite_config.go
cd iptb-btfs-plugins/blob/master/standalone
go build rewrite_config.go

# standalone is the default tool name, it will parser log file and write to btfs configration files
iptb logs > iptb_logs.txt
./standalone
```
# Fund BTFS node cluster
```
# print all btfs nodes logs include bttc address, deposit 100 btt to all bttc address
iptb logs

# if the nodes already stopped when wait depositing, start again
iptb start
```
# Other useful command
Start single node
```
iptb start 0
iptb stop 0
```

Connect to single btfs node
```
iptb shell 0

# run normal btfs command on node 0
btfs config show

# disconnect to btfs node 0
exit
```
Run btfs command on sigle node directly
```
iptb run 0 -- btfs config --json Addresses.Swarm '["/ip4/0.0.0.0/tcp/4000"]'
iptb run 0 -- btfs config --json Addresses.API '["/ip4/127.0.0.1/tcp/5000"]'
iptb run 0 -- btfs config --json Addresses.RemoteAPI '["/ip4/127.0.0.1/tcp/6000"]'
iptb run 1 -- btfs config --json Addresses.Swarm '["/ip4/0.0.0.0/tcp/4001"]'
iptb run 1 -- btfs config --json Addresses.API '["/ip4/127.0.0.1/tcp/5001"]'
iptb run 1 -- btfs config --json Addresses.RemoteAPI '["/ip4/127.0.0.1/tcp/6001"]'
iptb run 2 -- btfs config --json Addresses.Swarm '["/ip4/0.0.0.0/tcp/4002"]'
iptb run 2 -- btfs config --json Addresses.API '["/ip4/127.0.0.1/tcp/5002"]'
iptb run 2 -- btfs config --json Addresses.RemoteAPI '["/ip4/127.0.0.1/tcp/6002"]'
iptb run 3 -- btfs config --json Addresses.Swarm '["/ip4/0.0.0.0/tcp/4003"]'
iptb run 3 -- btfs config --json Addresses.API '["/ip4/127.0.0.1/tcp/5003"]'
iptb run 3 -- btfs config --json Addresses.RemoteAPI '["/ip4/127.0.0.1/tcp/6003"]'
```
