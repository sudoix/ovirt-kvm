### Bad volume specification

The error is:

```
VM devcsredisbebsbkedit03 is down with error.
Exit message: Bad volume specification {'device': 'disk', 'type': 'disk', 'diskType': 'file', 'specParams': {}, 'alias': 'ua-65353d40-f81a-402d-8d8c-8ede61428aca',
'address': {'bus': '0', 'controller': '0', 'unit': '0', 'type': 'drive', 'target': '0'},
'domainID': '90d5c496-8690-4d24-a371-fbee41f8b6f9',
'imageID': '65353d40-f81a-402d-8d8c-8ede61428aca',
'poolID': '00000002-0002-0002-0002-000000000253',
'volumeID': 'de1c86e2-3c0c-414e-acaf-6fde6fdcc889',
'path': '/rhev/data-center/00000002-0002-0002-0002-000000000253/90d5c496-8690-4d24-a371-fbee41f8b6f9/images/65353d40-f81a-402d-8d8c-8ede61428aca/de1c86e2-3c0c-414e-acaf-6fde6fdcc889', 'discard': False, 'format': 'cow', 'propagateErrors': 'off', 'cache': 'none', 'iface': 'scsi', 'name': 'sda', 'bootOrder': '2', 'serial': '65353d40-f81a-402d-8d8c-8ede61428aca', 'index': 0, 'reqsize': '0', 'truesize': '1191936', 'apparentsize': '1245184'}.
```
For fix it we should go to the `path` and then edit the `*.meta` file.
In here path is the `/rhev/data-center/00000002-0002-0002-0002-000000000253/90d5c496-8690-4d24-a371-fbee41f8b6f9/images/65353d40-f81a-402d-8d8c-8ede61428aca/`

The meta file contains:

```
CAP=161061273600
CTIME=1725624634
DESCRIPTION={"DiskAlias":"","DiskDescription":""}
DISKTYPE=DATA
DOMAIN=90d5c496-8690-4d24-a371-fbee41f8b6f9
FORMAT=COW
GEN=1
IMAGE=7b805d3f-17c1-4a54-b183-830742a031e7
LEGALITY=LEGAL
PUUID=00000000-0000-0000-0000-000000000000
SEQ=0
TYPE=SPARSE
VOLTYPE=LEAF
EOF
```
And we should edit the `LEGALITY` field from `ILLEGAL` to `LEGAL` and save it.
After that you can start the VM.

