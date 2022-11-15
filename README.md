# `mcaddon` Package Workflow

A reusable workflow which packages resource and/or behavior packs into `.mcpack` and `.mcaddon` files.

## Usage

Here is an example workflow that creates a `.mcaddon` file in /builds/\<versionString\>

```YAML
name: Generate Assets
on:
  workflow_dispatch:
    inputs:
      versionString:
       type: string
       required: true
jobs:
  generate:
    uses: AdamRaichu/mcaddon-package-workflow/.github/workflows/main.yml@v1
    with:
      pack_name: example_pack
      pack_type: 0
      target_path: ./builds/${{ inputs.versionString }}
      bp_path: ./behavior_pack
      rp_path: ./resource_pack
```

## Inputs

Here are the possible inputs along with usage explanation.

```YAML
inputs:
  pack_name:
    description: The name of the file # shown as <pack_name>.mcpack or <pack_name>.mcaddon
    required: true
    type: string
  pack_type:
    description: What kind of package you are building # use `0` for mcaddon, `1` for behavior, or `2` for resource
    required: true
    type: number
  target_path:
    description: Where you would like the assets to be stored # a path which starts with `./`
    required: false
    type: string
    default: ./assets
  bp_path:
    description: Path to the behavior pack
    required: false
    type: string
    default: ./bp
  rp_path:
    description: Path to the resource pack
    required: false
    type: string
    default: ./rp
  user_name:
    description: User name to be used in commit push
    required: false
    type: string
    default: github-actions
  user_email:
    description: User email to be used in commit push
    required: false
    type: string
    default: github-actions@github.com
```
