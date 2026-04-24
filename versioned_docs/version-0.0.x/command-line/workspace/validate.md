---
id: validate
title: Validate
sidebar_label: Validate
sidebar_position: 10
description: Command reference for the `validate` command of the Permguard CLI.
---

Using the `validate` command, it is possible to validate the local state for consistency and correctness.

```text
Usage:
  permguard validate [flags]

Flags:
  -h, --help   help for validate

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

## Validate the local state

The `permguard validate` command allows you to validate the local state for consistency and correctness.

```bash
permguard validate
```

output:

```bash
Your workspace has been validated successfully.
```

<details>
  <summary>
    JSON Output
  </summary>

```bash
permguard validate --output json
```

output:

```json
{
  "code_files": [
    {
      "oid": "bafyreign6iochuo4trx7o6myvza63wzghoxajkfgxatj5o7arg4beul72u",
      "oname": "test-policy",
      "partition": "/",
      "path": "test-policy.cedar",
      "section": 1
    }
  ]
}
```

</details>

## Validation Errors

When one or more source files contain syntax errors, the command outputs the failing files and exits with an error.

```bash
permguard validate
```

output:

```bash
  - platform-policies.cedar: parser error: parse error at <input>:15:5 "n": invalid primary ;
error: failed to validate the workspace
  - cli: blobification process failed due to code file errors
```

<details>
  <summary>
    JSON Output
  </summary>

```bash
permguard validate --output json
```

output:

```json
{
  "causes": [
    "cli: blobification process failed due to code file errors"
  ],
  "error": "cli: failed to validate the workspace"
}
```

</details>
