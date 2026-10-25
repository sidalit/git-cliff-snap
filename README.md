<div align="center">

<img src="snap/gui/git-cliff.png" alt="git-cliff logo" width="128" />

# git-cliff

**Generate changelogs from your Git history.**

[![git-cliff](https://snapcraft.io/git-cliff/badge.svg)](https://snapcraft.io/git-cliff)
[![Base: core26](https://img.shields.io/badge/Base-core26-2C8C3C?logo=canonical&logoColor=white)](https://snapcraft.io/core26)
![Confinement: strict](https://img.shields.io/badge/Confinement-strict-2C8C3C)
[![Maintainer: sidaliteir](https://img.shields.io/badge/Maintainer-sidaliteir-2C8C3C?logo=snapcraft&logoColor=white)](https://snapcraft.io/publisher/sidaliteir)
![Architectures: amd64 and arm64](https://img.shields.io/badge/Architectures-amd64%20%7C%20arm64-2C8C3C?logo=linux&logoColor=white)

[Getting Started](#getting-started) · [Configure](#configure) · [Limitations](#limitations) · [Build](#build) · [Support](#support) · [License](#license)

Unofficial snap packaging for [git-cliff](https://github.com/orhun/git-cliff), a customizable changelog generator with support for conventional commits.

</div>

---

## Getting Started

<a href="https://snapcraft.io/git-cliff"><img alt="Get it from the Snap Store" src="https://snapcraft.io/en/dark/install.svg" width="180"></a>

```bash
sudo snap install git-cliff
cd ~/my-project
git cliff --init
git cliff -o CHANGELOG.md
```

`git cliff` and `git-cliff` run the same command.

## Configure

There are no `snap set` options. Configure git-cliff through its TOML file:

| Configuration | Location |
|---|---|
| Project configuration | `cliff.toml` in your repository |
| Global configuration | `~/snap/git-cliff/current/.config/git-cliff/cliff.toml` |

`git cliff --init` creates a project configuration. To reuse a global configuration, copy it into the snap's location above.

For repositories on removable drives under `/media` or `/mnt`:

```bash
sudo snap connect git-cliff:removable-media
```

## Limitations

- Repositories must be in a visible home folder or connected removable storage. Host directories such as `/tmp`, `/opt` and `/srv` are unavailable.
- The snap cannot read `~/.gitconfig`. Repository settings in `.git/config` and `.mailmap` still work.
- `replace_command` runs inside the snap. Basic tools such as `sed`, `grep` and `awk` are available; programs installed only on the host are not.

## Build

```bash
git clone https://github.com/sidalit/git-cliff-snap.git
cd git-cliff-snap
sudo snap install snapcraft --classic
snapcraft pack
```

## Support

- **Installation or snap issues:** [open a packaging issue](https://github.com/sidalit/git-cliff-snap/issues).
- **Application bugs:** [report them upstream](https://github.com/orhun/git-cliff/issues).

## License

Snap packaging: [MIT](https://github.com/sidalit/git-cliff-snap/blob/main/LICENSE).
