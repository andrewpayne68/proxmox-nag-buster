## proxmox-nag-buster 
Forked from https://github.com/foundObjects/pve-nag-buster

`pve-nag-buster` is a dpkg hook script that persistently removes license nags
from Proxmox VE 6.x and up. Install it once and you won't see another license
nag until the Proxmox team  changes their web-ui code in a way that breaks the patch.

Please support the Proxmox team by [buying a subscription](https://www.proxmox.com/en/proxmox-ve/pricing) if it's within your
means. High quality open source software like Proxmox needs our support!

### How does it work?

The included hook script removes the "unlicensed node" popup nag from the web
gui and disables the pve-enterprise repository list. This script is called
every time a package updates the web gui or the pve-enterprise source list and
will only run if packages containing those files are changed.

The installer installs the dpkg hook script, adds the pve-no-subscription repo list
and calls the hook script once. There are no external dependencies beyond the base
packages installed with PVE by default.



### Installation

SSH in as root, no need for sudo.

```sh
wget https://raw.githubusercontent.com/foundObjects/pve-nag-buster/master/install.sh
```
#### Always read scripts downloaded from the internet before running them as root or with sudo
```sh
chmod +x install.sh && ./install.sh
```

#### Uninstall:
```sh
./install.sh --uninstall
```
#### remove /etc/apt/sources.list.d/pve-no-subscription.list if desired

#### Reboot the Proxmox Server



### Notes:

#### Why is there base64?

For convenience the install script also contains a base64 encoded copy of the
hook script, this makes installation possible without access to github or a
full clone of the project directory.

To inspect the base64 encoded script run `./install.sh --emit`; this dumps the
encoded copy to stdout and quits. To install using the stored copy just run
`sudo ./install.sh --offline`, no internet required.


### Contact:

[Open an issue](https://github.com/foundObjects/pve-nag-buster/issues) on GitHub

Please get in touch if you find a way to improve anything, otherwise enjoy!

