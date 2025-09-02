# Armbian Images

白嫖 GitHub Actions 构建比较新的 Armbian 镜像。有 [orangepizero3](./userpatches/config-orangepizero3.conf) 和 [orangepi3b](./userpatches/config-orangepi3b.conf)。

纯自用，不做 bug 修复，大概不接 pr。~~搞得好像有什么可 pr 的一样~~

有问题请移步 Discussions。

## 神秘记录 1

```console
# (On WSL2 fedora-remix)
# for level in {1..9}; do
$ time xz -k -$level Armbian-unofficial_25.11.0-trunk_Orangepi3b_trixie_current_6.12.44.img
$ du -h $file && du $file && rm $file
```

| Level    | Compress Time                                      | Diff             | File Size        | Diff               |
| -------- | -------------------------------------------------- | ---------------- | ---------------- | ------------------ |
| Original | /                                                  | /                | 2.4G (2,457,600) | /                  |
| 1        | real 1m12.677s<br>user 4m24.581s<br>sys 0m6.375s   | /                | 625M (639,184)   | -1.78G (1,818,416) |
| 2        | real 1m16.414s<br>user 6m21.102s<br>sys 0m6.966s   | +3.7s            | 609M (623,012)   | -16,172            |
| 3        | real 1m22.589s<br>user 9m9.354s<br>sys 0m8.491s    | +6.2s            | 594M (607,868)   | -15,144            |
| 4        | real 1m34.023s<br>user 13m47.625s<br>sys 0m10.564s | +11.4s           | 570M (583,552)   | -24,316            |
| 5        | real 2m3.528s<br>user 19m17.293s<br>sys 0m10.058s  | +29.5s           | 549M (561,632)   | -21,920            |
| 6        | real 2m16.514s<br>user 21m44.067s<br>sys 0m14.463s | +13s             | 546M (558,576)   | -3,056             |
| 7        | real 3m33.362s<br>user 16m30.236s<br>sys 0m7.694s  | +1m16.9s (76.9)  | 537M (549,396)   | -9,180             |
| 8        | real 7m0.957s<br>user 13m34.520s<br>sys 0m5.964s   | +3m27.6s (207.6) | 527M (539,484)   | -9,912             |
| 9        | real 12m55.056s<br>user 12m53.431s<br>sys 0m4.937s | +5m54.1s (354.1) | 506M (517,488)   | -21,996            |
