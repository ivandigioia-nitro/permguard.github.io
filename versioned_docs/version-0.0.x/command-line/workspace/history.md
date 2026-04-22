---
id: history
title: History
sidebar_label: History
sidebar_position: 7
description: Command reference for the `history` command of the Permguard CLI.
---

Using the `history` command, it is possible to show the history of the current checked out ledger.

```text
Usage:
  permguard history [flags]

Flags:
  -h, --help   help for history

Global Flags:
  -o, --output string            output format (default "terminal")
      --spiffe-enabled           enable native SPIFFE mTLS via Workload API
      --spiffe-endpoint string   SPIFFE Workload API socket path (defaults to SPIFFE_ENDPOINT_SOCKET env)
      --tls-ca-file string       path to CA certificate for server verification (PEM)
      --tls-cert-file string     path to client certificate for mTLS (PEM)
      --tls-key-file string      path to client private key for mTLS (PEM)
      --tls-skip-verify          skip server certificate verification (insecure, dev only)
  -v, --verbose                  true for verbose output
  -w, --workdir string           workdir (default ".")
```

:::caution
The output from your current version of Permguard may differ from the example provided on this page.
:::

<!-- updated: commit format changed from single tree CID to profiles array + manifest CID -->

## Show the History

The `permguard history` command allows you to show the history of the current checked out ledger.

```bash
permguard history
```

output:

```bash
Your workspace history head/273165098782/fd1ac44e4afa4fc4beec622494d3175a:

commit bafyreigicp6inahqx7bny4q3hayvfyldwgx34vlg55z6dt3mpgdc6xqtm4:
  - profiles:
    - ztas_app/: bafyreigecbyyfwelaip4ynreku26h7pwu5qqg5fm3s23lcbzlejdrhpfwu
  - manifest: bafyreig7lbj54eovjli534dwju3i3zce3vyldzyvdd7uvk2vtjro3xtqzy
  - Committer date: 2024-12-24 16:51:57 +0100 CET
  - Author date: 2024-12-24 16:51:57 +0100 CET
commit bafyreidxucxtwamjuk6g4ziku2yon2qhtm7jnjbcsbrcwyecm7fj2vzety:
  - profiles:
    - ztas_app/: bafyreigyugkg5ywg2fxgwmfbnz3b25tmi332255jbwzneurdssifdbazri
  - manifest: bafyreig7lbj54eovjli534dwju3i3zce3vyldzyvdd7uvk2vtjro3xtqzy
  - Committer date: 2024-12-24 16:50:04 +0100 CET
  - Author date: 2024-12-24 16:50:04 +0100 CET
commit bafyreiag4keidsdw5gyiyox3mqylddufxmsjdp2wpjaga66yuv5672bote:
  - profiles:
    - ztas_app/: bafyreigecbyyfwelaip4ynreku26h7pwu5qqg5fm3s23lcbzlejdrhpfwu
  - manifest: bafyreig7lbj54eovjli534dwju3i3zce3vyldzyvdd7uvk2vtjro3xtqzy
  - Committer date: 2024-12-24 16:48:58 +0100 CET
  - Author date: 2024-12-24 16:48:58 +0100 CET

total 3
```

<details>
  <summary>
    JSON Output
  </summary>

```bash
permguard history --output json
```

output:

```json
{
  "commits": [
    {
      "oid": "bafyreigicp6inahqx7bny4q3hayvfyldwgx34vlg55z6dt3mpgdc6xqtm4",
      "predecessor": "bafyreidxucxtwamjuk6g4ziku2yon2qhtm7jnjbcsbrcwyecm7fj2vzety",
      "profiles": [
        {
          "key": "ztas_app/",
          "tree": "bafyreigecbyyfwelaip4ynreku26h7pwu5qqg5fm3s23lcbzlejdrhpfwu"
        }
      ],
      "manifest": "bafyreig7lbj54eovjli534dwju3i3zce3vyldzyvdd7uvk2vtjro3xtqzy",
      "message": "",
      "author": "",
      "author_timestamp": "2024-12-24T16:51:57+01:00",
      "committer": "",
      "committer_timestamp": "2024-12-24T16:51:57+01:00"
    },
    {
      "oid": "bafyreidxucxtwamjuk6g4ziku2yon2qhtm7jnjbcsbrcwyecm7fj2vzety",
      "predecessor": "bafyreiag4keidsdw5gyiyox3mqylddufxmsjdp2wpjaga66yuv5672bote",
      "profiles": [
        {
          "key": "ztas_app/",
          "tree": "bafyreigyugkg5ywg2fxgwmfbnz3b25tmi332255jbwzneurdssifdbazri"
        }
      ],
      "manifest": "bafyreig7lbj54eovjli534dwju3i3zce3vyldzyvdd7uvk2vtjro3xtqzy",
      "message": "",
      "author": "",
      "author_timestamp": "2024-12-24T16:50:04+01:00",
      "committer": "",
      "committer_timestamp": "2024-12-24T16:50:04+01:00"
    },
    {
      "oid": "bafyreiag4keidsdw5gyiyox3mqylddufxmsjdp2wpjaga66yuv5672bote",
      "predecessor": "bafyreiaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "profiles": [
        {
          "key": "ztas_app/",
          "tree": "bafyreigecbyyfwelaip4ynreku26h7pwu5qqg5fm3s23lcbzlejdrhpfwu"
        }
      ],
      "manifest": "bafyreig7lbj54eovjli534dwju3i3zce3vyldzyvdd7uvk2vtjro3xtqzy",
      "message": "",
      "author": "",
      "author_timestamp": "2024-12-24T16:48:58+01:00",
      "committer": "",
      "committer_timestamp": "2024-12-24T16:48:58+01:00"
    }
  ]
}
```

</details>
