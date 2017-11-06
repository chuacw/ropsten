# Ropsten testnet PoW chain

[![Join the chat at https://gitter.im/ethereum/ropsten](https://badges.gitter.im/ethereum/ropsten.svg)](https://gitter.im/ethereum/ropsten?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

To resync to the revived Ropsten chain, at the command line run:
```
geth --testnet removedb
geth --testnet --fast --bootnodes "enode://20c9ad97c081d63397d7b685a412227a40e23c8bdc6688c6f37e97cfbc22d2b4d1db1510d8f61e6a8866ad7f0e17c02b14182d37ea7c3c8b9c2683aeb6b733a1@52.169.14.227:30303,enode://6ce05930c72abc632c58e2e4324f7c7ea478cec0ed4fa2528982cf34483094e9cbc9216e7aa349691242576d552a2a56aaeae426c5303ded677ce455ba1acd9d@13.84.180.240:30303"
```

or for Parity:
```
parity db kill --chain ropsten
parity --chain ropsten --bootnodes "enode://20c9ad97c081d63397d7b685a412227a40e23c8bdc6688c6f37e97cfbc22d2b4d1db1510d8f61e6a8866ad7f0e17c02b14182d37ea7c3c8b9c2683aeb6b733a1@52.169.14.227:30303,enode://6ce05930c72abc632c58e2e4324f7c7ea478cec0ed4fa2528982cf34483094e9cbc9216e7aa349691242576d552a2a56aaeae426c5303ded677ce455ba1acd9d@13.84.180.240:30303"
```

or for cpp-ethereum:
```
eth --ropsten --kill --pin --peerset "required:20c9ad97c081d63397d7b685a412227a40e23c8bdc6688c6f37e97cfbc22d2b4d1db1510d8f61e6a8866ad7f0e17c02b14182d37ea7c3c8b9c2683aeb6b733a1@52.169.14.227:30303 required:6ce05930c72abc632c58e2e4324f7c7ea478cec0ed4fa2528982cf34483094e9cbc9216e7aa349691242576d552a2a56aaeae426c5303ded677ce455ba1acd9d@13.84.180.240:30303"
```

## Troubleshooting

If you have problems syncing to the right chain, you can force your client to connect strictly to peers known to be on the revived chain. This only needs to be done for the initial sync.

For geth, start the client without connecting to any peers:
```
geth --testnet --fast --nodiscover
```
Then in the console (`geth attach`), add them manually:
```
admin.addPeer('enode://6ce05930c72abc632c58e2e4324f7c7ea478cec0ed4fa2528982cf34483094e9cbc9216e7aa349691242576d552a2a56aaeae426c5303ded677ce455ba1acd9d@13.84.180.240:30303')
admin.addPeer('enode://20c9ad97c081d63397d7b685a412227a40e23c8bdc6688c6f37e97cfbc22d2b4d1db1510d8f61e6a8866ad7f0e17c02b14182d37ea7c3c8b9c2683aeb6b733a1@52.169.14.227:30303')
admin.addPeer("enode://0f7c65277f916ff4379fe520b875082a56e587eb3ce1c1567d9ff94206bdb05ba167c52272f20f634cd1ebdec5d9dfeb393018bfde1595d8e64a717c8b46692f@51.15.54.150:41340");
admin.addPeer("enode://1168159d733aa87475828a9bb4e32d7765e7005099ba2b7ab6de526c9cebe2cf0b7628fecbd729f57ed6a0c4f255ddd2068142f2866cb9384134cc4a72273e0e@98.245.227.143:55816");
admin.addPeer("enode://28b48201295d17403cee0644013b0ff99efcbdf20899aea05a14630f5946dacfa5d20d43c6d7a81b0a35f5dc0108aa46b9895ac934e8a408b7103cfd3993b37d@58.246.66.214:18587");
admin.addPeer("enode://30db358700c246892c3629e904b7cb850bb9ea515de34eb81b5dd244c9c5cff2a1fc959ef4bc30ba60ad467f902b481faada07d050e6bc7ee180c5207979772d@31.211.80.204:61901");
admin.addPeer("enode://3a23d361eaeeeff3164785e748c2f58e8cd76a3280466e7e9b0a2cf5a66e14ec425225b99193858eb2101d1ed70a4b481c779e2d1101c11db6c8ec7fd2b96019@189.189.250.79:59838");
admin.addPeer("enode://418caa502b286ba09a5bcd3e8bc37a1704e83ba6a9c08cfbf6d115a7b985bac8e6c4bb424e1f3554c04968d9850ddbb97dda62e8105f901b17cc236091f86fa0@138.197.124.152:39734");
admin.addPeer("enode://4a8687d468f46d31fd9c166f5ed6631129d377bfb20e55c24fe6ae7f70e0bf34cc43cf62d79e311eea50dbc90eb05b84f5a456df4d60574019371484787ecc3e@34.204.199.229:30303");
admin.addPeer("enode://4c29de25a6c7433ab5d2d1d1163790f4b1759cc4a057d910ccb6070d2448a1b0d63d590a91c225ca3fc43c89ffe4a194441d8877c49adb54c876bafc6f313cd0@34.204.198.237:40058");
admin.addPeer("enode://5a8aff79126d0b42a20693cf131abe95df8f7d6e07ed06a9d876b7b208b7733e86e2279f6681a8711c82c26bbbec528503cf8fdea672c6c2044bd79871fd7916@72.36.89.14:38554");
admin.addPeer("enode://6ca327f93d878141698e14171c5931493edfe0efa777dbe5cb1eb8299df10847654cada44671244b5c5b6db712e4307275c78756c15b936f9b047a70e50fe4d3@41.212.225.76:51188");
admin.addPeer("enode://6db1a38490cf2437153b968d4c035e849f6b85d1fa48b0fba11ee6cdf426365893bd099853fcb99fef92b8ef3674c9cddb5a6cd8274e5386c4c4a5f5f42370fb@68.168.208.245:65110");
admin.addPeer("enode://71cae2ed71c8846a22686b8dd1406bb01eb7bf522091b838de0da63a0878fb01760a3bffb8f4edc231a544ab6f4ce5a4b7b7500a156f748e42d90d8f9521913d@198.50.160.104:60698");
admin.addPeer("enode://7755a33e5c0593439bc50517806f4f2afd0a40e313ccf949bdd8009f21a6e5c6712e6e1a634dff4fa45c7b5a8bd28eb6e7a422375fce5fff58c53a14aac37510@34.232.62.162:30303");
admin.addPeer("enode://8d65fc1c9f8c95be6c3e9594355c8122c9416cef8c01592c55b11643023f9dadcf1b5a587cff0afda1427e309a0d596b319f1eb4dc754f80f08730942712d681@129.110.241.5:53593");
admin.addPeer("enode://90ba4b2e260558afa6bd915e1cb633f59d58cc1a7fe27e1f5c5ee7055c0da9e2a1988a58d8b7d4dd1c788b821d5d36426899fa7c5a47170580d7ec0c8fbe1aa9@34.226.203.97:54780");
admin.addPeer("enode://95a12b92f2a23d2c85efb3af59ba7b9a1afcc7fcf064b2d21a89efbbd6db4f014a3fce503ea58f4a7c21833fbcd94ecbfa1ba69174126edd0239036957cc9bad@34.228.25.62:30303");
admin.addPeer("enode://a2981072125057a4cd201e8fca787cfc3b7d351a96412f47b09c6f81f30899276d7dc233f50ca85fc42611a39f37adc30959a5c57b3b14654472f94d40794b44@72.36.89.13:27298");
admin.addPeer("enode://b0f7096cee9c97522417d930076e02567aadea87464a4869d84520cec3a28192cc0b3d458fd5825e8ec3c4b12024a0b9628cbfc39bcda9c73d3bdc17a4532608@52.90.217.4:30303");
admin.addPeer("enode://b80c85af34065a7d80a4852bf0f92807ddb26148371dc8bf60e5407939ecb9acaff3a11a17baae71a153f97a90603d3f12c85dd3aa75222917844346926c3431@113.212.229.71:62022");
admin.addPeer("enode://be3901c7ca63f9ab0bb528bb7fb54a29eeed3441a1090086b9099b82248516b703c1d38a98363328013cf4d829803b7d35071847a95f65b0b059a142d386206d@94.201.100.231:62610");
admin.addPeer("enode://d014c9825b4850e1a19e8976f7d01100481aafdd996d35791f0364f7027d6c1927b81b071515a850eb5da7c34d426e9826b856e814021729d5b3c4073cd3564d@34.204.186.219:30303");
admin.addPeer("enode://d90526692837b302b9514e8d9af65bc7181d6b55073d761f98af0a762854c8d1daa8532f76fcf80a6ad5e3b625209d91d75909806f7178f4adb3a10e584f0bf9@130.149.22.247:30303");
admin.addPeer("enode://e8be9ef91b4d046d78411baad777e3a04619f89324b8c95a345efeccf225aeb3e3e76991ec7625974e0fb7c60846e13485256b415bdee0eec65add43a0f7a0ef@34.231.110.213:55622");
admin.addPeer("enode://f9d50c1e9d9a2eaa7ce387ec7ac64b12d6f0d16ae230d3cb975cd5210ed59c59ce021aa6230519cf2baa5c0fbb9f911ae2db32f0104d1e2b5d6448ff1d184d03@72.36.89.12:11882");
admin.addPeer("enode://fc6e2249bfdb51a83d98cacc2605b54f1aa6ec056c2c050f3bcdfad85ff2d12765bf5be0d2827edabcbcb3432026937bd76306d7a5c34506db8fe0be9b78cb3b@40.74.228.147:37880");
```

For parity:
```
echo -e "enode://20c9ad97c081d63397d7b685a412227a40e23c8bdc6688c6f37e97cfbc22d2b4d1db1510d8f61e6a8866ad7f0e17c02b14182d37ea7c3c8b9c2683aeb6b733a1@52.169.14.227:30303\nenode://6ce05930c72abc632c58e2e4324f7c7ea478cec0ed4fa2528982cf34483094e9cbc9216e7aa349691242576d552a2a56aaeae426c5303ded677ce455ba1acd9d@13.84.180.240:30303" >> ropstenpeers.txt
```
to add the peers (one per line) to a text file, and then run the client with flags:
```
parity --chain ropsten --reserved-peers ropstenpeers.txt --reserved-only
```

You can check that the client is on the revived chain by comparing to the block numbers on [http://pool.ropsten.ethereum.org](http://pool.ropsten.ethereum.org) and [http://ropsten.etherscan.io](http://ropsten.etherscan.io).
