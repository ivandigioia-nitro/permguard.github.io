---
id: apply
title: Apply
sidebar_label: Apply
sidebar_position: 2
description: Command reference for the `apply` command of the Permguard CLI.
---

Using the `apply` command, it is possible to apply the plan to the remote ledger.

```text
Usage:
  permguard apply [flags]

Flags:
  -h, --help   help for apply

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

<!-- updated: apply JSON fields changed to integer IDs, added partition/datatype/code_files, manifest blob now in plan -->

## Apply the local state

The `permguard apply` command allows you to apply the plan to the remote ledger.

```bash
permguard apply
```

output:

```bash
Initiating the planning process for ledger head/273165098782/fd1ac44e4afa4fc4beec622494d3175a.
Planning process completed successfully.
  + bafyreicvh2o5kwyfsgjq5qcdxse4dkkbbvzxknxjim6ibbc35kmw27fbne /view-branch-inventory-auditors
  ~ bafyreide5rsd2b3vocfji4sw5di6xkeyugcotteee74yibev4x27aopgia /assign-role-branch
  = bafyreiaapbtxeti2vaasc3ms3dii5urgtjk6jfkxllhld5dm33mfsqkz5y /schema
  - bafyreiekc2jsaebluqu3j56auwu43zxjx4vm4yzvv45vpmizobyyybnkqa /view-branch-inventory-auditor
  = bafyreig7lbj54eovjli534dwju3i3zce3vyldzyvdd7uvk2vtjro3xtqzy /manifest
unchanged 2, created 1, modified 1, deleted 1
Initiating the apply process for ledger head/273165098782/fd1ac44e4afa4fc4beec622494d3175a.
Apply process completed successfully.
Your workspace is synchronized with the remote ledger: head/273165098782/fd1ac44e4afa4fc4beec622494d3175a.
```

<details>
  <summary>
    JSON Output
  </summary>

```bash
permguard apply --output json
```

output:

```json
{
  "code_files": [
    {
      "oid": "bafyreicvh2o5kwyfsgjq5qcdxse4dkkbbvzxknxjim6ibbc35kmw27fbne",
      "oname": "view-branch-inventory-auditors",
      "partition": "/",
      "path": "view-branch-inventory-auditors.cedar",
      "section": 1
    },
    {
      "oid": "bafyreide5rsd2b3vocfji4sw5di6xkeyugcotteee74yibev4x27aopgia",
      "oname": "assign-role-branch",
      "partition": "/",
      "path": "assign-role-branch.cedar",
      "section": 2
    },
    {
      "oid": "bafyreiaapbtxeti2vaasc3ms3dii5urgtjk6jfkxllhld5dm33mfsqkz5y",
      "oname": "schema",
      "partition": "/",
      "path": "schema.json",
      "section": 3
    }
  ],
  "plan": {
    "create": [
      {
        "partition": "/",
        "oname": "view-branch-inventory-auditors",
        "otype": "blob",
        "oid": "bafyreicvh2o5kwyfsgjq5qcdxse4dkkbbvzxknxjim6ibbc35kmw27fbne",
        "datatype": 0,
        "codeid": "view-branch-inventory-auditors",
        "codetypeid": 2,
        "languageid": 2,
        "languagetypeid": 2,
        "languageversionid": 0,
        "state": "create"
      }
    ],
    "delete": [
      {
        "partition": "/",
        "oname": "view-branch-inventory-auditor",
        "otype": "blob",
        "oid": "bafyreiekc2jsaebluqu3j56auwu43zxjx4vm4yzvv45vpmizobyyybnkqa",
        "datatype": 0,
        "codeid": "view-branch-inventory-auditor",
        "codetypeid": 2,
        "languageid": 2,
        "languagetypeid": 2,
        "languageversionid": 0,
        "state": "delete"
      }
    ],
    "modify": [
      {
        "partition": "/",
        "oname": "assign-role-branch",
        "otype": "blob",
        "oid": "bafyreide5rsd2b3vocfji4sw5di6xkeyugcotteee74yibev4x27aopgia",
        "datatype": 0,
        "codeid": "assign-role-branch",
        "codetypeid": 2,
        "languageid": 2,
        "languagetypeid": 2,
        "languageversionid": 0,
        "state": "modify"
      }
    ],
    "unchanged": [
      {
        "partition": "/",
        "oname": "schema",
        "otype": "blob",
        "oid": "bafyreiaapbtxeti2vaasc3ms3dii5urgtjk6jfkxllhld5dm33mfsqkz5y",
        "datatype": 0,
        "codeid": "schema",
        "codetypeid": 1,
        "languageid": 2,
        "languagetypeid": 1,
        "languageversionid": 0,
        "state": "unchanged"
      },
      {
        "partition": "/",
        "oname": "manifest",
        "otype": "blob",
        "oid": "bafyreig7lbj54eovjli534dwju3i3zce3vyldzyvdd7uvk2vtjro3xtqzy",
        "datatype": 1,
        "codeid": "",
        "codetypeid": 0,
        "languageid": 0,
        "languagetypeid": 0,
        "languageversionid": 0,
        "state": "unchanged"
      }
    ]
  }
}
```

</details>
