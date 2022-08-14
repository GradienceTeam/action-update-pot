# action-update-pot

[![Chat on Matrix](https://matrix.to/img/matrix-badge.svg)](https://matrix.to/#/#AdwCustomizer:matrix.org)

Github Action for updating .pot

## Usage

### Example usage

```shell
name: "Translation"

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]
  schedule:
    - cron: '21 6 * * 5'

jobs:
  update-pot:
    name: Update .pot
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v3

      - name: Update .pot
        uses: AdwCustomizerTeam/action-update-pot@main
        with:
          title: "Adwaita Manager POT file"
          copyright: "Adwaita Manager Team"
          license: "GNU GPLv3"
          author: "Adwaita Manager Team"
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

```

### Parameters

You must also provide an `GITHUB_TOKEN` in `env`

| Name               | Description                                                               | Default            | Required |
| ------------------ | ------------------------------------------------------------------------- | ------------------ | -------- |
| `destination_path` | Destination path to save generated .pot file                              | `/po`              | false    |
| `slug`             | Project slug. Defaults to the Github repository name.                     | $GITHUB_REPOSITORY | false    |
| `text_domain`      | Text domain to look for in the source code. Defaults to the project slug. | `slug`               | false    |
| `title`            | Replace "SOME DESCRIPTIVE TITLE."'                                        |                    | false    |
| `copyright`        | Replace "YEAR THE PACKAGE S COPYRIGHT HOLDER"'                            |                    | false    |
| `license`          | Replace "same license as the PACKAGE package"'                            |                    | False    |
| `author`           | Replace "FIRST AUTHOR <EMAIL@ADDRESS>"'                                   |                    | false    |
