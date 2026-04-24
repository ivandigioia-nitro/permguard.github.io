---
id: refresh
title: Refresh
sidebar_label: Refresh
sidebar_position: 9
description: Command reference for the `refresh` command of the Permguard CLI.
---

Using the `refresh` command, it is possible to scan source files in the current workspace and synchronize the local state.

```text
Usage:
  permguard refresh [flags]

Flags:
  -h, --help   help for refresh

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

<!-- updated: refresh output format changed; success case added; error now uses causes array, no validation_errors object -->

## Refresh the workspace state

The `permguard refresh` command allows you to scan source files in the current workspace and synchronize the local state.

```bash
permguard refresh
```

output:

```bash
Your workspace has been refreshed.
```

<details>
  <summary>
    JSON Output
  </summary>

```bash
permguard refresh --output json
```

output:

```json
{
  "code_files": [
    {
      "oid": "bafyreiekc2jsaebluqu3j56auwu43zxjx4vm4yzvv45vpmizobyyybnkqa",
      "oname": "view-branch-inventory-auditor",
      "partition": "/",
      "path": "view-branch-inventory-auditor.cedar",
      "section": 1
    }
  ]
}
```

</details>

## Refresh Errors

When one or more source files contain syntax errors, the command outputs the failing files and exits with an error.

```bash
permguard refresh
```

output:

```bash
  - platform-policies.cedar: parser error: parse error at <input>:15:5 "n": invalid primary ;
Your workspace has errors.
Please validate and fix the errors to proceed.
error: failed to execute the refresh
  - cli: blobification process failed due to code file errors
```

<details>
  <summary>
    JSON Output
  </summary>

```bash
permguard refresh --output json
```

output:

```json
{
  "causes": [
    "cli: blobification process failed due to code file errors"
  ],
  "error": "cli: failed to execute the refresh"
}
```

</details>
