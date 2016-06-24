# cellar
My OpenWRT Package Repository

### Installation
```bash
cd /path/to/openwrt
echo 'src-git cellar https://github.com/isofew/cellar.git' >> feeds.conf.default
scripts/feeds update -a
```

### Usage
```bash
scripts/feeds update cellar
scripts/feeds install -p cellar some-package-name
```

### Dev-Script
```bash
#!/bin/bash
# a simple package update script you may find helpful

rm -f `find bin -name $1*`

pfx=package/$1

make $pfx/clean $2 &&
make $pfx/compile $2 &&
make $pfx/install $2 &&

scp `find bin -name $1*` root@openwrt:~ &&
ssh root@openwrt "opkg remove $1 && opkg install $1* && $1"
```
