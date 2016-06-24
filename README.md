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
