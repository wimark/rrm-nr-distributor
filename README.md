802.11k Neighbor Report distributor daemon
==========================================

## Features

- Multi-network support (different SSID for different networks)
- STA dependent band steering by advertising the other BSSes of the same AP
- Works out of the box after umdns is working
- Not too much but enough logs

## Installation

- Configure all your OpenWRT devices for the same SSID for each layer 2 network 
- Install umdns with `opkg update; opkg install umdns` and configure it (Pay attention to config the interface in the config file, setup your firewall, seccomp workaround etc)
- Copy files: `cp files/etc/init.d/rrm_nr /etc/init.d/ ; cp files/usr/bin/rrm_nr /usr/bin/rrm_nr`
- Run `/etc/init.d/rrm_nr enable` and `/etc/init.d/rrm_nr start` 
- Check the syslog for the results: `logread | grep rrm_nr` or `logread -e rrm_nr`

## Package build

 - Download Openwrt SDK, add feed, compile, indexing for opkg

 `wget -q -N -c https://downloads.openwrt.org/releases/22.03.0/targets/ath79/generic/openwrt-sdk-22.03.0-ath79-generic_gcc-11.2.0_musl.Linux-x86_64.tar.xz`
 `tar -x -f openwrt-sdk-22.03.0-ath79-generic_gcc-11.2.0_musl.Linux-x86_64.tar.xz`
 `echo "src-git rrm_nr https://github.com/wimark/rrm-nr-distributor.git" > feeds.conf`
 `./scripts/feeds update`
 `./scripts/feeds install -a`
 `echo "CONFIG_PACKAGE_rrm-nr-distributor=m" >> .config`
 `make defconfig`
 `make package/feeds/rrm_nr/package/compile`
 `make package/index`

## Known issues

- SSIDs with '|' character are not supported at the moment
- With large number of APs (>20) the full umdns update takes a few interations/minutes

## Copyright

Original code from [Kiss Ádám](https://github.com/kissadamfkut). 
[Danya Sliusar](https://github.com/danyanya) from *Wimark* updated with little style considering.  