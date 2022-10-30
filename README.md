# Lean固件还原 xiaomi wifi驱动(授人以鱼不如授人以渔)

## 拉取代码
```
git clone https://github.com/coolsnowwolf/lede -b master openwrt
cd openwrt
git reset --hand 28696943
```

## 提取 xiaomi 驱动依赖的源代码
```
mkdir -p /tmp/xiaomi/package/kernel/
mkdir -p /tmp/xiaomi/package/network/utils
mkdir -p /tmp/xiaomi/package/firmware/
mkdir -p /tmp/xiaomi/target/linux/

cp -r package/kernel/mac80211 /tmp/xiaomi/package/kernel/
cp -r package/network/utils/iw /tmp/xiaomi/package/network/utils
cp -r package/firmware/ipq-wifi /tmp/xiaomi/package/firmware/
cp -r target/linux/ipq807x /tmp/xiaomi/target/linux/
```

## 编译 lede 主线代码之前，先还原上述提取的代码即可 
```
# 必须先删掉这两个目录，再还原代码，不然存在限速问题
rm -rf openwrt/package/network/utils/iw
rm -rf openwrt/package/kernel/mac80211
cp -rf /tmp/xiaomi/* openwrt/
```
