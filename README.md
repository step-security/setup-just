[![StepSecurity Maintained Action](https://raw.githubusercontent.com/step-security/maintained-actions-assets/main/assets/maintained-action-banner.png)](https://docs.stepsecurity.io/actions/stepsecurity-maintained-actions)

# 🤖 `setup-just` action

[![Build Status](https://img.shields.io/github/actions/workflow/status/step-security/setup-just/build.yaml?branch=trunk)](https://github.com/step-security/setup-just/actions/workflows/build.yaml)

This GitHub Action will install a release of the
[just](https://github.com/casey/just) command runner for you.

## Usage

### Examples

In most cases all you will need is the following in your workflow.

```yaml
- uses: step-security/setup-just@v3
```

If you want a specific version of `just` you can specify this by passing the
`just-version` input.

```yaml
- uses: step-security/setup-just@v3
  with:
    just-version: '1.40.0'
```

To avoid rate-limiting, the default Github token available to all actions, is
automatically used to authenticate calls to Github. To override it, pass the
input `github-token`.

```yaml
- uses: step-security/setup-just@v3
  with:
    github-token: ${{ secrets.MY_GITHUB_TOKEN }}
```

### Inputs

| Name           | Required | Description                                  | Type   | Default               |
| -------------- | -------- | -------------------------------------------- | ------ | --------------------- |
| `just-version` | no       | A valid NPM-style semver specification.      | string | *                     |
| `github-token` | no       | A Github token to authenticate API requests. | string | `${{ github.token }}` |

The semver specification is passed directly to NPM's [semver
package](https://www.npmjs.com/package/semver). This GitHub Action will install
the latest matching release. Examples include

- `just-version: '*'` latest version (default).
- `just-version: '1'` equivalent to `>=1.0.0 <2.0.0`.
- `just-version: '1.2'` equivalent to `>=1.2.0 <2.0.0`.
- `just-version: '1.2.3'` equivalent to `=1.2.3`.
- `just-version: '^1.2.3'` equivalent to `>=1.2.3 <2.0.0`.

## Development

This action is a composite action and the installation logic is done in a shared
library located at
[@step-security/setup-crate](https://github.com/step-security/setup-crate).

## License

Licensed under

- MIT license ([LICENSE](LICENSE) or http://opensource.org/licenses/MIT)
