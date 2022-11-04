# Install

Get the code and install, check the `distributed-compliance-ledger` (dlc) github repository for more detailed instructions such as prerequisites like `go`, `jq`, etc.

```
git clone git@github.com:zigbee-alliance/distributed-compliance-ledger
cd distributed-compliance-ledger
make build
make install
make test
```

There's now a `dcld` binary available (check the spelling, it is easy to mistype).

# Persistent chains

Not interested in running something locally, let us connect to something live. Info can be found at <https://github.com/zigbee-alliance/distributed-compliance-ledger/tree/master/deployment/persistent_chains>.

```
dcld config chain-id main-net
dcld config node https://on.dcl.csa-iot.org:26657
dcld config output json
dcld config
dcld status
```

Or parsed prettier:

```
dlcd status | jq '.'
```

At this moment this results in:

```
{
  "NodeInfo": {
    "protocol_version": {
      "p2p": "8",
      "block": "11",
      "app": "0"
    },
    "id": "22671a69531175fdeb41664ec9e5b615aaba2686",
    "listen_addr": "tcp://0.0.0.0:26656",
    "network": "main-net",
    "version": "0.34.14",
    "channels": "40202122233038606100",
    "moniker": "CSA-ON-03",
    "other": {
      "tx_index": "on",
      "rpc_address": "tcp://0.0.0.0:26657"
    }
  },
  "SyncInfo": {
    "latest_block_hash": "DDD82FB11D2DDA06E223DF22134E086CC6EE4DECFA218C3F4E81D2535BA9DF16",
    "latest_app_hash": "FFF95033E408BA86C33267740A3CAF7BE72EE6E3E38126E937B591322C36D8DE",
    "latest_block_height": "12307",
    "latest_block_time": "2022-11-04T10:37:08.686589181Z",
    "earliest_block_hash": "B9F3E76529081EECDCA011F89826C7D1FBD4CAB6E8F9485323B9EE57DE522846",
    "earliest_app_hash": "E3B0C44298FC1C149AFBF4C8996FB92427AE41E4649B934CA495991B7852B855",
    "earliest_block_height": "1",
    "earliest_block_time": "2022-08-11T15:49:35.603086763Z",
    "catching_up": false
  },
  "ValidatorInfo": {
    "Address": "B8B7C814309220DEEAB81525E4D28D5A91102EE5",
    "PubKey": {
      "type": "tendermint/PubKeyEd25519",
      "value": "GcUFOBREvsiwPSQxeFJP/S1Fc6JTPuxqImvcfVb1c3Q="
    },
    "VotingPower": "0"
  }
}
```

Just type `dcld` to get help on the type of commands you can execute.

Let us query the main net:

```
dcld query vendorinfo all-vendors
```

The results of this can be found in `vendors.txt` in this repository, summarized here:

```
dcld query vendorinfo all-vendors | jq -r '.vendorInfo[] | "* [" + .companyLegalName + "](" + .vendorLandingPageURL + ")"'
```

* [Assa Abloy](http://www.yalehome.com)
* [Legrand](https://www.legrand.com)
* [NXP Semiconductors N.V.](https://www.nxp.com)
* [Qorvo, Inc.](https://www.qorvo.com/)
* [Universal Electronics Inc](https://www.uei.com/)
* [Comcast]()
* [Lumi United Technology Co., Ltd.](https://www.aqara.com/)
* [Tuya Global Inc.]()
* [Nordic Semiconductor ASA](https://www.nordicsemi.com)
* [EGLO Leuchten GmbH](https://www.eglo.com/en/)
* [Eve Systems GmbH](https://www.evehome.com)
* [Espressif Systems (Shanghai) Co. Ltd.](https://www.espressif.com)
* [Guangzhou Elite Education & Technology Co., Ltd.](https://longan.link/)
* [GE Lighting, a Savant company](https://www.gelighting.com/)
* [deveritec GmbH](https://deveritec.de)
* [Tridonic GmbH & Co KG](https://www.tridonic.com)
* [innovation matters iot GmbH](https://www.innovation-matters.at/)
