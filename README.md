# update-checksum-workflow

GitHub Actions Reusable Workflow to update aqua-checksums.json
If aqua-checksums.json isn't latest, update aqua-checksums.json and push a commit

About aqua's Checksum Verification, please see the document too.

https://aquaproj.github.io/docs/reference/checksum

## Workflow

[Workflow](.github/workflows/update-checksum.yaml)

## Requirements

```console
$ aqua g -i int128/ghcp
```

### Eample

```yaml
name: update-aqua-checksum
on:
  pull_request:
    paths:
      - aqua.yaml
      - aqua-checksums.json
jobs:
  update-aqua-checksums:
    uses: aquaproj/update-checksum-workflow/.github/workflows/update-checksum.yaml@0ff0064b95b335a8ed93a36664e491d514c75df0 # v0.1.2
    permissions:
      contents: read
    with:
      aqua_policy_config: aqua-policy.yaml
      aqua_version: v1.33.0
      prune: true
    secrets:
      gh_app_id: ${{secrets.APP_ID}}
      gh_app_private_key: ${{secrets.APP_PRIVATE_KEY}}
```

## LICENSE

[MIT](LICENSE)
