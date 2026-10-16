# git-cliff snap

[![git-cliff](https://snapcraft.io/git-cliff/badge.svg)](https://snapcraft.io/git-cliff)

Snap packaging for [git-cliff](https://github.com/orhun/git-cliff), a highly customizable changelog generator that follows conventional commits.

Unofficial build, not affiliated with or endorsed by the git-cliff project.

## Build

```bash
snapcraft pack
```

## Install and try

<a href="https://snapcraft.io/git-cliff"><img alt="Get it from the Snap Store" src="https://snapcraft.io/en/dark/install.svg" width="180"></a>

```bash
sudo snap install git-cliff                   # or a local build: ./git-cliff_2.14.2_*.snap --dangerous
sudo snap connect git-cliff:removable-media   # optional: /media, /mnt
cd ~/my-project
git cliff --init
git cliff -o CHANGELOG.md
```

`git cliff` and `git-cliff` run the same command.

## Known limitations

### Config file

The global config file is `~/snap/git-cliff/current/.config/git-cliff/cliff.toml` instead of `~/.config/git-cliff/cliff.toml`. A `cliff.toml` in your project works as usual. To reuse an existing global config:

```bash
mkdir -p ~/snap/git-cliff/current/.config/git-cliff
cp ~/.config/git-cliff/cliff.toml ~/snap/git-cliff/current/.config/git-cliff/
```

### Commands in replace_command

Commands set in `replace_command` (commit preprocessors and postprocessors) run inside the snap, so only basic tools from the snap's base, such as `sed`, `grep` and `awk`, are available. Programs installed on your system, such as `typos`, are not found.

### Git settings

The snap cannot read `~/.gitconfig`, so settings from it, such as `mailmap.file`, do not apply. The repository's own `.mailmap` and `.git/config` still work.

### Repositories outside your home folder

The snap can only open repositories in your home folder and, with the `removable-media` connection, in `/media` and `/mnt`. Repositories in other places, such as `/tmp`, `/opt` or `/srv`, are not visible.

## Update to a new upstream release

Change `version` and `source-tag` in `snap/snapcraft.yaml`, then rebuild.

## License

The packaging is MIT-licensed (see `LICENSE`). git-cliff is licensed under MIT or Apache-2.0; its dependencies carry their own licenses.
